---
layout: post
title: 5 steps to using Copilot with niche languages
description: >
  How you can use Copilot to get improved results over almost any coding language or framework
image: /assets/img/blog/ai-with-niche-languages.jpg
sitemap: true
---

## 5 steps to using Copilot with niche languages

One piece of common feedback I receive about GitHub Copilot and other AI coding assistants is this: 
>"They're fine for common languages like .NET/JavaScript/Python, but they never work for my [insert custom language] application!"

Copilot has good knowledge of public codebases on [GitHub.com](https://github.com) (there are over 25 million of them today), but there are many languages without a large volume of code there.

ADA, COBOL, FORTRAN, PL/I, ABAP, SAS, MUMPS, VHDL, RPG, REXX - just to name a few!
They still play a vital role in some of the world's biggest enterprise systems, but the code is proprietary and rarely open-sourced.

Luckily for developers of those languages, GitHub Copilot now comes with features that allow support for these languages too, without training a whole custom model.

Here's an example of how I setup Visual Studio Code and GitHub Copilot to work on a T24 BASIC application (used in Temenos core banking applications):

### 1 - Download your codebase and open in VSCode
I cloned this example codebase for T24 development, with a set of example files for my language: https://github.com/mathisi-io/t24dev. 

Any codebase will work though, even if not stored in a modern Git repository.

### 2 - Install Copilot and other IDE extensions
Next make sure you have the right IDE extensions within your editor, including GitHub Copilot and any other language-specific extensions. VSCode offers syntax highlighting out of the box for some languages, but there's also 12,000+ [community developed language packs](https://marketplace.visualstudio.com/search?target=VSCode&category=Programming%20Languages&sortBy=Installs). 

I installed this MV Basic one: https://marketplace.visualstudio.com/items?itemName=RocketSoftware.rocket-mvbasic

Don't find what you want? You can even [write your own language pack](https://code.visualstudio.com/api/language-extensions/syntax-highlight-guide#developing-a-new-grammar-extension) if you're keen! 

### 3 - Copy any development or coding standards into your workspace as Markdown
Remember that GitHub Copilot can read any Markdown (.MD) format documentation and use as context for your prompts, so you'll want to grab whatever is available and load directly into your workspace.

Don't have Markdown format docs yet? There are free converters available online for other formats like PDF, or you can ask Copilot to create a script to convert yours locally if you'd prefer.

### 4 - Reference your docs in your Copilot Instructions
While Copilot can often locate and use Markdown docs in your workspace without prompting, I recommend adding a short reference in your Copilot Instructions file. 

What's a Copilot Instructions file? It's a special file you can create within any repository at **.github\copilot-instructions.md**, where any text stored there will be bundled into all prompts you send in Copilot Chat. That makes it a good home for relevant context or reminders that help Copilot answer more accurately.

In my case, I added the following to my instructions file: "This project is a T24 Basic Temenos banking application. The development standards for this language are in the t24devstandards.md file. Please read these before answering questions."  

![Example of a Copilot Instructions file](/assets/img/blog/github-copilot-instructions-example.png)

Example of a Copilot Instructions file
{:.figcaption}

**Bonus tip**: In the latest VSCode Stable release, you can even reference public URL links (i.e. links with no auth needed to access) in your Instructions file! This is a great way to centralize info across multiple projects.

Read more about [Copilot Instructions for repositories here](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot).

### 5 - Try it out with some example prompts! 
Now you're all set and ready to try your context-enhanced AI assistant in action. Open Copilot Chat and ask questions of your codebase, and you should see Copilot referencing your Instructions file if placed correctly.

![Example response from Copilot using Copilot Instructions](/assets/img/blog/github-copilot-instructions-prompt.png)

Example response from Copilot using Copilot Instructions
{:.figcaption}

**Not sure what prompts to use?**

This [Copilot guide for Modernizing COBOL](https://docs.github.com/en/copilot/using-github-copilot/guides-on-using-github-copilot/modernizing-legacy-code-with-github-copilot) is a good place to start. It's loaded with examples on explaining existing code, creating diagrams from code, generating new tests, and even converting into other languages! 


You can apply the same recipe to any language/framework, or even just use it to inject your own coding standards into a workspace.

VSCode may not be able to replace all functionality from a specialized IDE for your language, but this approach should give you an 'AI assistant boost' when you need one.

Have fun and I'd love to hear stories of what languages you've tried this on.