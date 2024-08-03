---
layout: post
title: AI Agents and Multi-Agent Workflows: How Will They Impact Software Development?
description: >
  A look at Multi-Agent workflows in AI - the patterns being introduced, and current tooling available to developers. Includes examples for AutoGen Studio.
image: /assets/img/blog/multi-agent-workflows-intro.jpg
sitemap: false
---

## AI Agents and Multi-Agent Workflows: How Will They Impact Software Development?

![Multi Agent Workflows](/assets/img/blog/multi-agent-workflows-intro.png)

This week I've been getting to know [AutoGen Studio](https://autogen-studio.com/), one of the in-development projects from Microsoft Research related to AI agents. AutoGen is one of a few open-source toolsets emerging for development of these (CrewAI and LangGraph being others), and Studio is their brand new low-code UI for managing them.

New to this area? Let's start with a quick definition or two:

### Characteristics of an AI Agent

An AI agent is a software entity that performs tasks autonomously, often mimicking human decision-making processes. These agents can perceive their environment through data or sensors, process this information, and take actions based on predefined rules or learned behaviours. Characteristics of AI agents include:

- **Autonomy**: They can operate without human intervention.
- **Reactivity**: They respond to changes in their environment in real-time.
- **Proactiveness**: They can take the initiative to achieve goals.
- **Social ability**: They can interact with other agents or human users.

### Exploring Multi-Agent Workflows

Tools like AutoGen promise to help master a new pattern of software development - one where multiple specialized agents work together to achieve a single goal. Each agent specialises in a specific sub-task and collaborates with other agents to complete the overall objective. Unlike single-agent systems, which operate in isolation, multi-agent workflows rely on the synergy between agents to achieve optimal results.

Interesting concept, and it's not hard to see how companies creating 'one AI assistant to rule them all' may lead to similar issues of the monolithic mainframes and desktop apps of recent years. As AutoGen's creator himself (Chi Wang) says, a multi-agent system offers 3 big benefits:

- **Modularity**: simplifying development, testing, and maintenance
- **Specialization**: allowing an agent and its creators to focus on excelling at a specific task area
- **Learning**: allowing agents to work together to deliver results they couldn't achieve alone

Sounds amazing doesn't it?

A similar concept has been around since the rise of chatbot assistants. With the launch of Amazon Alexa's skills library in 2015 I wrote about the benefits and challenges of having smaller natural-language AI applications integrating with each other. Admittedly Amazon's attempt at a skills ecosystem didn't quite succeed, but many experts have argued that the concept was sound but perhaps ahead of its time.

### Multi-Agent Workflows In Action

The example workflow available in AutoGen Studio is a trivial but interesting one:

A travel planner agent awaits a request from you to help plan a trip itinerary. After receiving your input, it works with two other agents (a local knowledge specialist and a language and culture specialist) to produce and refine the itinerary, before handing it back. In the demo, all 3 agents take the form of a GPT-4 model with tailored prompting to focus their behaviour. In a more evolved form, those specialist agents may be capable of placing bookings, contacting 3rd parties, or translating languages.

![AutoGen Studio Beta](/assets/img/blog/autogen-studio.png)

AutoGen Studio Beta

A more evolved example may be Tesla's Autopilot system - while the exact details of this are unknown, it is likely a form of multi-agent ecosystem where specialist agents collaborate with human input to produce a single outcome.

### Challenges and Limitations
As a developer, I can see the issues integrating software in this manner will have. A quick scan of AutoGen documentation will introduce you to concepts like cycling, conditional flows, human interruption, token streaming, and more... Wow.

The challenges you may face in building a multi-agent solution today include:

- **Complexity in Design and Implementation**: Developing and managing a multi-agent system is more complex than a single-agent one.
- **Communication Overhead**: The need for constant communication and coordination among agents can create overhead, potentially slowing down the workflow.
- **Conflict Resolution**: Agents may have conflicting objectives or behaviours, necessitating formal conflict resolution mechanisms.
- **Resource Management**: Efficiently managing shared resources and preventing bottlenecks can be challenging in a multi-agent environment.
- **Security and Privacy**: Ensuring secure and private communication between agents can be difficult, especially in distributed systems.

I suppose those of us building early Service-Oriented-Architecture and API-based solutions faced similar friction, and over time these have been abstracted away to make some of the trickier integration challenges go away.

### Are We There Yet?

After a few hours with AutoGen Studio, I can see it's a step in the right direction for developing this new software pattern, but still far from mainstream-ready. It is in beta form after all, and installing it requires a level of Python knowledge (thank you GitHub Copilot for guiding me through this!). We're evolving fast though, and there are a few ways you can get ready for this pivot if you're a software engineer:

- Continue learning about prompt engineering and different techniques to produce specialised outputs
- Learn about libraries and methods for integrating LLMs into custom applications - [Prompt Flow](https://github.com/microsoft/promptflow) from Microsoft is a good example
- Learn about reference architectures for deploying GenAI solutions at scale in the cloud (Microsoft's [Azure OpenAI reference model](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/architecture/baseline-openai-e2e-chat) based on WAF is a great intro to this)

Want to go deeper into the Multi-Agent AI world? This Forbes article interviewing the AutoGen creator is a great start:

[The Promise Of Multi-Agent AI](https://www.forbes.com/sites/joannechen/2024/05/24/the-promise-of-multi-agent-ai/)

