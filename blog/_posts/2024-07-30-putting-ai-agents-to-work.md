---
layout: post
title: Putting AI Agents to work - moving beyond chat with tools
description: >
  An intro to the concept of tools or plugins in AI agents, and how they are used in frameworks like Azure OpenAI Assistants and Autogen to do more than chat.
image: /assets/img/blog/ai-agents-tools-intro.jpg
sitemap: true
---

## Putting AI Agents to work: moving beyond chat with tools

In my recent article on [Multi-Agent AI Workflows](/blog/_posts/2024-07-01-ai-agents-multi-agent-workflows.md), I looked at some of the benefits and challenges of designing solutions that use multiple AI agents to deliver an outcome. 

The example workflows in that article used multiple LLM agents (each with specific prompting) to work together but without access to any resources other than their LLM model itself.
While there are [early signs](https://news.mit.edu/2023/multi-ai-collaboration-helps-reasoning-factual-accuracy-language-models-0918) that even combining agents in this way can achieve better results than a single agent, enabling them to take action directly rather than just return info is where things get really interesting!

### Agents vs Assistants

First, a quick definition as there are similar-sounding terms in this space:

- An **AI Agent** can be defined as "an autonomous entity capable of perceiving their environment and taking action to achieve specific goals". 
- An **AI Assistant** is a subset of an Agent designed to interact with people, providing help and support on tasks.

In late 2023, OpenAI [launched a beta](https://techcrunch.com/2023/11/06/openai-launches-api-that-lets-developers-build-assistants-into-their-apps/) of their new Assistants API, designed to help developers create custom assistants within their applications. This since launched as a [public preview within Azure OpenAI Service](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/assistant), and is now available across most regions.

### An Assistant Needs Their Tools

The Assistants API was created with two main goals:

1. Handling complexities of user interaction like managing context history
2. Introducing the concept of Tools, which allows developers to equip an assistant to perform new tasks based on inputs from a conversation. 

A Tool can be implemented in many ways, as long as it carries a standard schema to allow the assistant to invoke it. The Tool concept has since expanded into [Autogen](https://microsoft.github.io/autogen/) and other AI orchestration products, and we're seeing early patterns of tools emerge:

- Perform a RAG search across specified files ([See here](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview) if you're new to RAG and want an intro)
- Call a built-in user-defined function
- Execute custom code (this allows the agent itself to write and execute code)

Over in [Semantic Kernel](https://learn.microsoft.com/en-us/semantic-kernel/overview/) (Microsoft's other open source agent development SDK which powers Copilot), Plugins play a very similar role to OpenAI Tools.

#### How does an agent know what tool to use?

Each tool is described with metadata that allows an agent to understand its purpose, functionality and usage. This metadata is often written in natural language, and clear and descriptive metadata is the key to creating the right behaviour and outcomes for your agent. You have some control here as a developer by setting parameters that force tool use or allow tools to be used in parallel, but the model retains much of the control here.

#### Examples of agent tools in use

**Warning**: code snippets ahead - skip to the bottom for a low-code option if you'd prefer!
{:.message}

The first example that blew my mind was Autogen's [Custom Code Executor](https://microsoft.github.io/autogen/docs/topics/code-execution/custom-executor) sample. Grab the Jupyter Notebook off the link to try for yourself, and it'll have you first setting up Autogen along with some supporting Python libraries:


~~~py
! pip -qqq install pyautogen matplotlib yfinance

import os
from typing import List

from IPython import get_ipython

from autogen import ConversableAgent
from autogen.coding import CodeBlock, CodeExecutor, CodeExtractor, CodeResult, MarkdownCodeExtractor
~~~

Setting up Autogen environment and dependencies
{:.figcaption}

You'll then create a new agent using a GPT model (note that I modified their original sample to use Azure OpenAI) and a Code Executor tool, with instructions on how to use custom code to solve problems provided by the user.

You then run that agent with a sample prompt that requests a plot chart showing the market caps of the Top 7 listed companies on Yahoo Finance:

~~~py
code_writer_agent = ConversableAgent(
    name="CodeWriter",
    system_message="You are a helpful AI assistant.\n"
    "You use your coding skill to solve problems.\n"
    "You have access to a IPython kernel to execute Python code.\n"
    "You can suggest Python code in Markdown blocks, each block is a cell.\n"
    "The code blocks will be executed in the IPython kernel in the order you suggest them.\n"
    "All necessary libraries have already been installed.\n"
    "Once the task is done, returns 'TERMINATE'.",
    llm_config={"config_list": [{"model": "gpt-4o", "api_key": os.getenv("OPENAI_API_KEY"), "api_type": "azure", "base_url": "https://[youraiservice].cognitiveservices.azure.com/", "api_version": "2023-12-01-preview"}]},
)

code_executor_agent = ConversableAgent(
    name="CodeExecutor",
    llm_config=False,
    code_execution_config={"executor": NotebookExecutor()},
    is_termination_msg=lambda msg: "TERMINATE" in msg.get("content", "").strip().upper(),
)

chat_result = code_executor_agent.initiate_chat(
    code_writer_agent,
    message="Create a plot showing the market caps of the top 7 publicly listed companies using data from Yahoo Finance.",
)
~~~

Creating an agent with a code execution tool
{:.figcaption}

Hit run and you'll quickly see a nice chart returned to you via Matplotlib... makes sense, but where was all the code to get the stock data??

I did a double take at first, before realising that we left the agent to write and execute its own Python code, with only light guidance and some pre-installed libraries! Our little agent happily worked out what calls to make and how to pass Yahoo Finance data to Matplotlib to create the final visual:

![Output of the Autogen agent](/assets/img/blog/tools-article-graph.png)

Output of the Autogen agent
{:.figcaption}

You're probably not alone if the thought of leaving AI agents to write their own code leaves you finally a little uneasy. I'm not sure that style of demo will be appearing in production apps any time soon, but it does show how much autonomy this generation of AI can have.

Now let's take a slightly more paired back example, focusing on custom function integration within an agent. This comes from Autogen's Calculator Tool sample, which sets up a simple calculator function that accepts two numbers and an operator:

~~~py
from typing import Annotated, Literal

Operator = Literal["+", "-", "*", "/"]


def calculator(a: int, b: int, operator: Annotated[Operator, "operator"]) -> int:
    if operator == "+":
        return a + b
    elif operator == "-":
        return a - b
    elif operator == "*":
        return a * b
    elif operator == "/":
        return int(a / b)
    else:
        raise ValueError("Invalid operator")
~~~

Setting up a custom function tool
{:.figcaption}

Once that's defined, create a new agent with the tool and some basic instructions to 'solve simple calculations':

~~~py
import os

from autogen import ConversableAgent

# Let's first define the assistant agent that suggests tool calls.
assistant = ConversableAgent(
    name="Assistant",
    system_message="You are a helpful AI assistant. "
    "You can help with simple calculations. "
    "Return 'TERMINATE' when the task is done.",
    llm_config={"config_list": [{"model": "gpt-4o", "api_key": os.getenv("OPENAI_API_KEY"), "api_type": "azure", "base_url": "https://[youraiservice].cognitiveservices.azure.com/", "api_version": "2023-12-01-preview"}]},
)

# The user proxy agent is used for interacting with the assistant agent
# and executes tool calls.
user_proxy = ConversableAgent(
    name="User",
    llm_config=False,
    is_termination_msg=lambda msg: msg.get("content") is not None and "TERMINATE" in msg["content"],
    human_input_mode="NEVER",
)

# Register the tool signature with the assistant agent.
assistant.register_for_llm(name="calculator", description="A simple calculator")(calculator)

# Register the tool function with the user proxy agent.
user_proxy.register_for_execution(name="calculator")(calculator)
~~~

Configuring an agent with a custom function
{:.figcaption}

Finally, start a chat with your agent and pass it a complex math equation, with only the single function available to use. The agent will decompose it and use its calculator to piece together the answer.

~~~py
from autogen import register_function

# Register the calculator function to the two agents.
register_function(
    calculator,
    caller=assistant,  # The assistant agent can suggest calls to the calculator.
    executor=user_proxy,  # The user proxy agent can execute the calculator calls.
    name="calculator",  # By default, the function name is used as the tool name.
    description="A simple calculator",  # A description of the tool.
)

chat_result = user_proxy.initiate_chat(assistant, message="What is (44232 + 13312 / (232 - 32)) * 5?")
~~~

Running the agent with an example math equation
{:.figcaption}

Both examples were "dumbed down" to the point where a simple web search could have revealed the answer, but they give a glimpse into the power of allowing AI to manage its own actions without explicit instructions.

### Can I use low-code tools?

Yes, Microsoft has already launched multiple options that achieve the same Assistant-Tool concept in a low-code context.

Within the Azure OpenAI Assistants preview, you can use [Logic Apps as a user-defined function tool](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/assistants-logic-apps) (only Consumption hosted Apps currently).

Copilot Studio also presents its own version of this within [Generative Mode copilots](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions) called 'Actions'; these are used and triggered in a very similar way. Copilot Actions can include a range of inbuild connectors from Power Automate, or execute your own Power Automate Flows or Bot Framework Skills for more complex scenarios. Be aware that the debug tooling around these is still lacking (being able to trace detailed conversation paths and tool usage), but I'm betting this will evolve over the coming months.

### Where to next?

Like AI assistant development overall, this is a fast-moving area with new products and patterns appearing every month! There are now a dizzying number of options available to developers wanting to build their own assistants, but also signs of common patterns forming across each.

Experiment and see which fits your team and use case, but don't forget important non-functional considerations such as cost, security and scalability along the way. As each experiment shows merit, think through the likely volumes that production usage will bring, and ensure your architecture can evolve to match (more on this topic later perhaps!).