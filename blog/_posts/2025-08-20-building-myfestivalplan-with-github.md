---
layout: post
title: How I Built a Launch Ready App in a Week Using GitHub Agents
description: >
  How I used GitHub Spark and Copilot Agents to turn a weekend idea into a launch-ready app in just days
image: /assets/img/blog/myfestivalplan-intro.png
sitemap: true
---

## How I Built a Launch-Ready App in a Week Using GitHub's Agents

A few weekends ago, my wife Shabnam Sarjami and I put our AI Agents knowledge to use on a personal project: how to improve attendee experience at Latin dance festivals (which we attend regularly). Event programs for these festivals aren't the best (low-res images packed with lots of info and posted direct to social media), and with GitHub Spark and Coding Agent just launched we wanted to see if we could rapidly prototype a better one!

The result? Not only a hit at our pilot festival last week (where we used it ourselves and shared with friends), but good enough to launch widely.

So how did we get this from idea to launchable business in just over a week?

It started with GitHub Spark, which was a huge help for ideating and iterating on UI design. Spark [launched in preview mode](https://github.blog/changelog/2025-07-23-github-spark-in-public-preview-for-copilot-pro-subscribers/) for Pro+ subscribers a few weeks ago, and if you haven't seen a 'prompt to app' UI in action yet it's magical!

Although Spark excels in great frontends with frameworks like React/Vite/Tailwind, many people forget you can add basic datastores to go beyond pure mockups. In my case I gave it sample CSV festival schedule files, which helped greatly to map out my data model and UI. 

>Hint: any time you're giving AI tools schemas and examples of data behind your app, you can expect to see much more accurate results!

Here's the result of my first Spark run:

![GitHub Spark in action building my first prototype](/assets/img/blog/myfestivalplan-spark.png){:width="70%"}

GitHub Spark in action building my first prototype
{:.figcaption}

After iterating in Spark for an hour or so, it was time to get hands-on with the code and use other agents to evolve it. All Sparks come with their own GitHub repo, but if you want to proceed to a production multi-user app, you'll want your own backend and authentication rather than Spark's own (I used Firebase/Firestore). For this and other enhancements, I used a mix of GitHub's new [Coding Agents](https://github.blog/news-insights/product-news/github-copilot-meet-the-new-coding-agent/), and [Agent Mode in VS Code](https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode):

- Coding Agent is amazing for those longer tasks where you have a clear spec in mind but don't want to supervise the work directly. Because it always works in its own branch, I have a safety net and can choose to discard changes if I don't like the result.

- For smaller changes (e.g., "Please refactor this large file into smaller components", "Please update this page with these style changes"), Coding Agent can be overkill. It takes time to download and compile code, form an implementation plan, and run full validations throughout. Agent Mode in the IDE is much more effective for these, as I can knock out minor changes in minutes and move on.

- I often find myself using both together - handing off the larger task to Coding Agent and then clearing out a bunch of smaller changes in parallel with VS Code (or just going to drink coffee and still feel like I’m working…).

### So how did my agents do?

Very well! Something I enjoyed was seeing my Copilot agents recommend new ways to validate my app and then make use of them once they existed in the repo. Early on my prototype app was lacking strong type checking, linting, and proper test coverage. But as these came online, agents would regularly use them to check their work. That creates this beautiful 'improvement cycle', where the better the codebase gets the more effective the agents are at doing work on it.

![Example from one of my Coding Agent sessions](/assets/img/blog/myfestivalplan-codingagent.png){:width="50%"}

Example from one of my Coding Agent sessions
{:.figcaption}

The same goes for [custom repo instructions](https://docs.github.com/en/enterprise-cloud@latest/copilot/tutorials/coding-agent/get-the-best-results#adding-custom-instructions-to-your-repository) too - I gradually evolved mine at *.github/copilot-instructions.md*, and it helped my agents stay on track when working on the app. Having good instructions files reduces risk of agents mis-interpreting prompts with wrong libraries, versions, or patterns. Everyone should use these now! I also have a growing set of custom prompt files (in *.github/prompts/{promptname}.prompt.md*), for tasks I perform repeatedly on my app. Don't overthink these, but whenever you find yourself typing out a long chat prompt that is like one you used before, think: "Could I save these for easy re-use?"

As well as general app coding duties, a big part of launching my app was streamlining data prep and validation for event schedules and artist data. Copilot Agent Mode helped greatly to create once-off or repeatable automation scripts for this. Without it the manual admin effort to launch new festivals would simply be too high and stop us scaling.

### A note on Copilot productivity:

I often hear people measuring Copilot effectiveness purely through "lines of code" generated, but that misses some of the biggest impact to having an AI agent helping through the development cycle. All the advice I received about topics like app branding and marketing, responsive website design, web performance optimization, deployment and release approaches - these were essential to us getting to 'launch ready' within days and not months!

### Pitfalls of agentic development:

The biggest negative I saw with agents guiding my coding is their tendency for 'complexity creep'. Often my agent would understand a goal and provide code that was perfectly capable and compiled… but complete overkill for the task I needed. Examples included: 

- Progressive loading and caching strategies

- Service workers or async threads running in background

- Backwards compatibility on changes that really didn't need them

This is where my own experience as a dev was crucial to spotting these and knowing when to apply the KISS (Keep it Simple Stupid) principle. It's why I don't fear AI Agents completely taking over developer jobs, as my app would've been a tech debt mess if I gave them complete control over architecture! That said, I do value the times when they pointed out flaws in my 'simple logic', including edge cases that could've led to nasty bugs later.

### Final thoughts:

You can see the final form of the app (and the website that goes with it) at [MyFestivalPlan](https://www.myfestivalplan.com/) now.

![Example festival guide on MyFestivalPlan](/assets/img/blog/myfestivalplan-example.png){:width="50%"}

Example festival guide on MyFestivalPlan
{:.figcaption}

 The experience of launching an app with an 'AI first' mindset was a positive and enjoyable one. Although I had the technical skills needed to build it by hand, the hours required would've been far more than I was able to invest in my personal time. The new approach still comes with a learning curve, but with enough experimenting anyone could follow this approach to turn their digital idea into reality!