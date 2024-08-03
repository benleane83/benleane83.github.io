---
layout: post
title: Example Content II
description: >
  A page showing how regular markdown content is styled in Hydejack.
image: /assets/img/blog/example-content-ii.jpg
sitemap: false
---

## AI-Powered Testing: How is quality engineering changing in 2024?

![AI-Powered Testing](/assets/img/blog/ai-powered-testing-intro.png)

AI-assisted development tools like GitHub Copilot are in the spotlight this year in the Software Engineering community. There's no doubt they've had an immediate impact for developers who adopt them, but there's also growing interest in AI-enabling other personas in the Software Development lifecycle.

I was curious to see what the major Quality Engineering vendors are doing in this space, and sure enough, they're racing to apply AI benefits to existing products, in a bid to grow market share. 

### The Rise of Selenium and Appium

![Appium and Selenium](/assets/img/blog/appium-selenium.png)

Test automation frameworks such as Selenium and Appium have seen huge adoption in recent years, with businesses investing in libraries worth of test scripts for ongoing app testing. At the same time, new players are arriving in the market promising a more efficient approach through various AI techniques. Interestingly very few are building on top of Selenium/Appium scripts, meaning teams may need to re-implement regression test suites to adopt them completely?

It's too early to say what the right investment is yet, but I expect the next 6 months will see a surge of pilot projects aiming to evaluate these new capabilities. So what are the most promising uses of AI for testing?

### Common AI Use Cases

- **Test Case Generation**: The first use case most people think of and the easiest to satisfy with generalist tools like Copilot. Test cases are either generated based on descriptions of business requirements / user stories, or reverse-engineered off existing code.

- **Test Data Generation**: Another use case that can be done already by Copilot Chat with the right prompting. Generating mock test data with enough variety and volume can be high effort, but by describing data in natural language ("Give me a set of 100 valid customer records with US phone numbers and addresses"), LLMs are surprisingly good at generating fresh examples to fit your needs. Or if you need larger volume, ask Copilot to write test data generation scripts and run them to receive your outputs.

- **Automated UI Testing**: UI test frameworks like Selenium and Appium are powerful, but their methods to identify UI elements during test execution are still prone to issues as apps evolve. Multiple vendors are promising to use AI models to assist in this process, either by moving to more dynamic detection of UI elements, or by eliminating noise from minor changes in UI to focus on significant defects.

- **Bug Detection**: Similar to automated UI testing, vendors are starting to offer an AI-driven approach to bug detection that will collect data and observe trends in different application components, reporting potential bugs without the need for hand-crafted test scripts. I haven't tried these personally yet, but it makes sense given the evolution of anomaly detection AI across the broader industry.

- **Test Prioritization**: Some testing vendors now offer test suites that dynamically prioritize test script execution based on AI models. For example, by looking at which components of an application's codebase have been modified within a release, it can select the minimum set of appropriate tests to run. Tools like Azure DevOps have achieved 'non-AI' versions of this for years using linkage of code, work items and test cases, but look for this field to expand rapidly.

- **Test Environment Simulation**: Finally, some vendors are experimenting with AI decision-making on configuration of test environments themselves. Learning models can review usage trends and pre-configure a range of environments to match expected or real-world usage, to allow more accurate test coverage.

### Vendor Options
In my research this week, these are the top companies that appeared to offer dedicated AI functionality in their testing tools. Big disclaimer that I've only spent minimal time with these yet myself, so would love to hear from anyone who has put them through the paces.

- [Aplitools](https://applitools.com/): Aplitools is known for visual testing and AI-powered visual validation. It focuses on detecting visual regressions and ensuring consistent UI across different platforms. 

- [Testim](https://www.testim.io/): Testim offers AI-driven test automation. Its platform uses machine learning to create and maintain test scripts, making it easier for testers to manage test cases. 

- [Appvance](https://appvance.ai/): Appvance promises to handle repetitive and time-consuming tasks with AI, making it suitable for managing a high volume of test cases. 

- [Mabl](https://www.mabl.com/): Mabl’s AI-driven testing platform focuses on end-to-end testing, including test case generation, execution, and reporting. They're promising to simplify testing for non-technical users.

### Challenges and Considerations: 

Just like with AI-assisted programming, it'll be critical (for now) to validate AI testing outputs manually on a regular basis. Any products using LLMs under the hood will likely hallucinate at times, and data issues may lead to unexpected results being reported.

However I can see how an 'AI testing assistant' could allow test teams to cover much more ground, and perhaps fill in gaps where businesses haven't been able to afford full test coverage. It will be interesting to see how this area evolves!
