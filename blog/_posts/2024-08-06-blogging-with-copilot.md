---
layout: post
title: Blogging with Copilot
description: >
  TBC
image: /assets/img/blog/ai-agents-tools-intro.jpg
sitemap: false
published: false
---

## Blogging adventures with Copilot Workspace

I've been lucky enough to have access to technical preview of [GitHub Copilot Workspace](https://githubnext.com/projects/copilot-workspace) for the last month or so, and I'm having a blast so far.
While this is not the magic 'write a prompt, press the button and a finished piece of software pops out' app you might be dreaming of, it does represent a potentially huge leap forward in abstracting developer tasks within a natural language UI. And since I've had it, I'm having fun tackling tasks that previously fell into the 'too hard to give up my evening hours for' category!

**My latest challenge?**
Porting my LinkedIn articles into a new GitHub Pages hosted blog.

Yes, I'm over a decade late onto [GitHub Pages](https://pages.github.com/) - it's GitHub's completely free hosting platform for static websites backed by GitHub repos! 

The starter template can be deployed in minutes, and there's full support for the Jekyll blogging platform (also maintained by GitHub under open source).

Blogging without a CMS? Consider me intrigued...

### Getting started

Jekyll itself is developed and compiled in Ruby. As someone who had never touched Ruby in my life, I figured I'd dive in with Copilot at my side to coach.
I setup a quick Codespace to work in - these are GitHub's cloud based dev environments, and great for working across different PCsto work across multiple PCs. I browsed a few Jekyll themes, and selected [Hydejack](https://hydejack.com/) as it looks amazing. Cloning their template repo into my Codespace, and I'm quickly able to setup Ruby's Bundler and other tooling without crowding my main dev laptop. Plus I'm running VS Code on Settings Sync so it brings Copilot and other extensions I need each time I'm in a Codespace.

Copilot is already helping me with my 'super ignorant' Ruby questions, and I'm rarely stuck for more than a few seconds on each task.

"Hey Copilot: How do I install a gemfile?"
- "You typically use bundler tools - start by running **gem install bundler**, followed by **bundle install**"

![Copilot Chat Example](/assets/img/blog/copilot-chat-example.png)

With my Codespace and repo all setup, GitHub Actions is happily building and deploying my static site on each push to main (Configured automatically by GitHub Pages and abstracting a bunch more Ruby tooling for me!).

### Working in Markdown

Jekyll supports Markdown and Liquid based pages, to allow authoring with text editors. Markdown has gained huge popularity across GitHub and Azure DevOps documentation, so it wasn't hard to get writing.

"Hey Copilot: Why is my Markdown page failing to load?"
- "Your page has a single character syntax issue with a semicolon in your Front Matter section" (somehow missed by VS Code itself)

### Markdown docs as Copilot context

Already using Markdown for your technical documentation?

Great, because as a simple markup language these are easily searchable by Copilot!
For any docs sitting in the same repo as you're editing, they're likely already being searched by Copilot Chat when using the @workspace agent.

"Hey Copilot: How do I use the Hydejack blog layout in a subdirectory?"
- "To use the blog layout in a subdirectory, follow these steps..." (followed by a bunch of content straight from Hydejack's embedded .md docs)

![Copilot Workspace Agent](/assets/img/blog/copilot-workspace-command.png)

Is your documentation located in other repos?
If you're on Copilot Enterprise, you're ...

## A glimpse into the future with Copilot Workspace
