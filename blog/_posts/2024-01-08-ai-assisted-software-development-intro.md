---
layout: post
title: AI-Assisted Software Development: What it is, how it works, and why you should care
description: >
  A intro to AI-Assisted Software Development as a growing trend in the IT industry, and some early learnings from rolling out across enterprises
image: /assets/img/blog/ai-development-intro.jpg
sitemap: true
---

## AI-Assisted Software Development: What it is, how it works, and why you should care

![AI Development](/assets/img/blog/ai-development-intro.jpg)

While the term 'AI-Assisted Software Development' isn't new this year (it became prominent in 2018 with launch of tools such as TabNine and Microsoft's IntelliCode), it's clear that 2023 is the year that it gained mainstream attention. Surging interest around Generative AI, ChatGPT, and Microsoft's own Copilot suite brought a renewed focus on AI productivity gains across all industries, and Software Development seemed a prime candidate.

Earlier tools such as TabNine and GitHub Copilot (released in preview form in 2021) delivered improvements to a range of common coding tasks, using their own AI models to recommend code snippets to developers. The experience was similar to previous tooling such as JetBrains ReSharper, but more intuitive about suggesting and generating code based on the context provided.

Fast forward to 2023, and a new wave of GenAI models provide a more powerful interactive approach; one which would not only produce lines of code but enable broader use cases including summarising, researching, and translating application code. GitHub Copilot Chat was released as a technical preview in July 2023, providing an experience like ChatGPT's but directly within a code editor and tailored to the software community. 

At the same time the broader Microsoft Copilot suite has been evolving with new features, and getting attention from IT stakeholders who are intrigued by claims of significant productivity improvements. Both GitHub Copilot and AWS Code Whisperer claim to support developers in coding up to 55% faster, harnessing revised GenAI models underneath. GitHub has since launched Copilot Chat in General Availability this month (Dec 2023), placing in hands of millions of developers worldwide.

### How Real Is The Hype Right Now?

As we end 2023, many organisations including Avanade are progressing global rollouts of GitHub Copilot, Azure OpenAI Service and other related tools. Avanade started our own GitHub Copilot rollout [almost two years ago](https://www.avanade.com/en/blogs/techs-and-specs/software-development/github-copilot), and has since acquired licenses for the majority of our developers worldwide. We're observing usage trends across internal and client facing teams, to see how their work has changed since adopting. Very quickly teams have been able to realise similar coding productivity and quality benefits as advertised by the tool vendors (40% or more), and in process freeing up developers to tackle more higher value or innovative tasks. We're now supporting our customers to run their own AI SDLC pilots, starting with GitHub Copilot usage and expanding from there.

Along the way we've realised several important lessons about this generation of AI tools:

#### Consistency is an issue
One of the biggest constraints of this generation of Large-Language-Model based AI (which powers GitHub Copilot and similar tools) is their non-deterministic nature, meaning that they return a variety of responses when provided with the same or similar input. In a software development context, that means that tasks that are performed repeatedly over a large codebase will result in suggested code looking different for every file processed. That lack of consistency can be alarming as you scale out to hundreds of code files (very common for modern enterprise apps).
While smart prompt engineering and manual refactoring of outputs can keep this under control, we've seen that bulk code-generation scenarios are often better left with dedicated tools that produce consistent output with lower defect rates. That leaves GenAI tools to guide refactoring and enhancements of converted outputs, a task it excels at. Conversion of application code from legacy languages such as COBOL into modern .NET/Java is a great example of this - GitHub Copilot can attempt this task at an individual file level but suffers when converting an entire application in batch.

#### Your tech lead roles are more important than ever
Across our first year of Copilot usage, we've seen an overall increase in coding quality from junior developers who use the tool to improve their work. Minor or cosmetic defects are dropping as the tool checks and recommends viable approaches to tasks, and helps them become proficient in new languages faster. At the same time, we typically see increased occurrences of architectural issues, leading from Copilot recommending code that while functional may not be the preferred way to achieve tasks. Because Copilot doesn't currently have access to your organization's coding standards or even private code repositories themselves, the responsibility to guide and check these aspects falls to your tech leads and senior developers. Good peer review practices are essential, as are providing clear patterns guidance and examples that other developers can follow.

#### Think beyond coding itself for the widest productivity gains
As examples of code generation and coding assistance becoming commonplace, we see more teams turning to other activities in the software development lifecycle to get a similar AI boost. Some of our favourite examples include:
- Summarising unfamiliar codebases and producing documentation
- Generating user stories and acceptance tests from a codebase
- Generating unit tests as well as test datasets for specific code
- Generating deployment scripts based on a described architecture

#### CoPilot isn't the only tool you'll need (but it's a great first step)
In most instances, teams have started with GitHub Copilot to realise immediate productivity gains on software projects; they only require license procurement and setup of a suitable GitHub Enterprise environment to start seeing results. Over time though, teams are exploring other tools including Microsoft's Azure OpenAI Service and Cognitive Search for more advanced capability which can gain additional context from your organisation's own datasets, and be scripted or embedded into other applications to provide AI features. Through early Copilot adoption, organisations can strengthen business cases for future AI work, including important data readiness activities that are essential for custom AI development.

### Where Do I Start?
While the Copilot family has made it easier than ever to start realising AI productivity gains quickly, there are still a few key steps we recommend to any organisation as they begin their GenAI rollout: 
- **Obtain any legal approvals**: it's important to ensure your business understands how new AI tooling will be used and what safeguards are in place to mitigate issues such as data privacy or IP infringement
- **Educate your developers**: all developers receiving new tools should be trained on effective usage, as well as ensuring processes such as code reviews are in place to review AI-produced outputs
- **Baseline key metrics**: in order to demonstrate productivity improvements, ensure dev teams are collecting the right metrics before and after tool adoption - we recommend starting with code commit volumes, cycle times for new work, and defect rates on new release