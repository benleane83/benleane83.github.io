---
layout: post
title: "Six Agentic Dev fundamentals you should learn"
description: >
  A framework I've used with businesses to assess where they're at on agentic development fundamentals, along with links to learn more about each technique.
image: /assets/img/blog/agentic-dev-intro.png
sitemap: true
---

## Six Agentic Dev fundamentals you should learn

Agentic development (the newest form of AI-assisted software development) is evolving rapidly, and with it comes a flood of new concepts. For many developers, it’s easy to feel overwhelmed by advanced demos and articles. Here's a framework I've used with businesses lately to assess where they're at on agentic development fundamentals specifically, along with links to learn more about each one. *Where do you sit in your company?*

### 1. Chat With My Code 
This is now what I recommend for anyone just starting with agentic dev. Before you dive into building new features or debugging issues with your AI Agent, just have it help you get to know your codebase better: questions like "How does logging work in this app?", "What level of UI test coverage do I have currently?", and "How can I optimize the performance of my frontend?" ***Learn more at:*** [Getting started with prompts for GitHub Copilot Chat](https://docs.github.com/en/copilot/how-tos/chat-with-copilot/get-started-with-chat)

### 2. Custom Instructions
In agentic development, context plays a crucial role - it's easy to overlook important task details that your agent may not pick up on unless you specify them clearly. The easiest place to start storing context is in your Custom Instructions file (Copilot's sits at ***.github/copilot-instructions.md***). Think of it as a one-stop-shop for anything you want the agent to know before starting any task on your workspace. ***Learn more at:*** [Customize chat with custom instructions](https://code.visualstudio.com/docs/copilot/copilot-customization#_use-a-githubcopilot-instructionsmd-file)

### 3. MCP Tools
With a good prompt and context, your agent can tackle a range of tasks across your workspace using only built-in tools or commands. However you can instantly supercharge it by providing it with custom tools, to let it interact with other software (local or cloud hosted) on your behalf. The most common type of tools today are published using Model Context Protocol (MCP), and you'll find a list of some top ones at [GitHub's MCP Registry](https://github.com/mcp). Some great tools to start with are the tool for your work management platform (GitHub, Azure DevOps, Jira) to let your agent read and update work items on your behalf, and the Playwright tool to give your agent instant access to automate browser tasks like navigating your web app independently. ***Learn more at:*** [Extending GitHub Copilot Chat with the Model Context Protocol (MCP)](https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/extend-copilot-chat-with-mcp)

### 4. Custom Prompt Files & Chatmodes
Once you're comfortable prompting your agent using context and tools, it's time to get creative with more extensive prompts that bring together those concepts in re-usable ways. If you find yourself writing similar instructions for your agent multiple times in the chat window, consider turning that prompt into a Custom Prompt file. These are Markdown files (like Custom Instructions) but made to run only in specific situations. 

Chatmodes are an evolution of this and bundle a stored prompt with pre-enabled tools relevant to the prompt. They give your agent a tailored 'persona' for jobs like Infra-As-Code Engineer, App Security Reviewer, Performance Tuning Guru, etc. Want some inspiration on prompts and chatmodes? The [Awesome-Copilot repo](https://github.com/github/awesome-copilot) has a collection of these created by the community and offering one-click install into VS Code. ***Learn more at:*** [Customize chat with prompt files](https://code.visualstudio.com/docs/copilot/customization/overview#_prompt-files-experimental)

### 5. Specification Files (or full Spec-Driven Development) 
Sometimes for complex tasks even the best-written prompt won't lead to the ideal outcome in one attempt. Developing software is an iterative process, and the best AI-assisted developers are often those who iterate with their AI Agents on a problem and break it down into smaller tasks. You can do this iteration directly in your agent's chat window, but there are benefits to collaborating on an actual document that becomes a living specification for the work. These docs can persist as long as required, and your agent can mark completed tasks over time. Great for longer running work that may be performed over a few days! 

The industry is still refining this pattern, but storing files as ***.spec.md*** is a way differentiate these from other prompt or instruction files. One well-known implementation of this is GitHub's own [Spec-Kit](https://github.com/github/spec-kit), an open-source toolkit for spec-driven development. It provides a highly structured approach to coding, which won't be for everyone but is a great example of how to evolve your agentic development. ***Learn more at:*** [Spec-driven development with AI](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)

### 6. Agentic Workflows 
If you've mastered those five techniques, you may notice that they mostly relate to guided pair-programming with your agent, rather than agents that operate independently on your behalf. Today the easiest way to start with unattended agents is via GitHub's [Copilot Coding Agent](https://github.blog/ai-and-ml/github-copilot/github-copilot-coding-agent-101-getting-started-with-agentic-workflows-on-github/) - these are fully managed agents running within the GitHub Cloud platform and can have work assigned via a simple prompt or GitHub issue. 

Did you know that there are other ways to incorporate unattended agents into your workflows though? This year the top AI Coding Agents such as GitHub Copilot have released CLI versions that can run as part of automation scripts or pipelines. The CLI mode builds on the same concepts as IDE Agents - custom instructions, MCP tools, and prompt files - but unlocks new use cases for schedule or event driven agent tasks. There's a very simple [example GitHub Action here](https://github.com/benleane83/copilot-agent-demo/blob/main/.github/workflows/copilot-cli-code-analysis.yml) that runs code analysis on each commit/PR. ***Learn more at:*** [GitHub Copilot CLI brings the power of Copilot coding agent directly to your terminal](https://github.com/github/copilot-cli)

## Want to go even deeper?
For an in-depth look at topics like Agentic Workflows and Spec-Driven Development, a great article to read is this one from Daniel Meppiel: [How to build reliable AI workflows with agentic primitives and context engineering](https://github.blog/ai-and-ml/github-copilot/how-to-build-reliable-ai-workflows-with-agentic-primitives-and-context-engineering/?utm_source=blog-release-oct-2025&utm_campaign=agentic-copilot-cli-launch-2025), along with his associated [AI Native Development Guide](https://danielmeppiel.github.io/awesome-ai-native). He shares lots of advanced techniques, along with the new Agent Package Manager (APM) which helps tackle common problems teams face when building out agentic workflows.