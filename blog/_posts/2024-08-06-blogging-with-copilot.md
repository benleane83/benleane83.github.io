---
layout: post
title: Blogging adventures with GitHub Pages and Copilot
description: >
  Using GitHub Pages and Copilot to learn some new languages and have fun at the same time
image: /assets/img/blog/blogging-with-copilot-intro.jpg
sitemap: true
published: true
---

## Blogging adventures with GitHub Pages and Copilot

One of the biggest changes I've noticed since I've been developing with [GitHub Copilot](https://github.com/features/copilot) is that it's **making coding fun again**. With my new AI coding assistant at my side, I'm tackling tasks that previously fell into the 'too hard to give up my evening hours for' category.

**My latest challenge?**
Porting my LinkedIn articles into a new GitHub Pages hosted blog.

Yes, I'm over a decade late onto [GitHub Pages](https://pages.github.com/) - it's GitHub's completely free hosting platform for static websites backed by GitHub repos! 

The starter template can be deployed in minutes, and there's full support for the Jekyll blogging platform (also maintained by GitHub under open source). 
Blogging without a CMS? Consider me intrigued...

### Getting started

Jekyll itself is developed and compiled in Ruby. As someone who had never touched Ruby in my life, I dived in with Copilot to coach me.

I set up a Codespace to work in - these are GitHub's cloud-based dev environments and are great for working across different PCs or tech stacks you don't commonly use. I browsed a few Jekyll themes and selected [Hydejack](https://hydejack.com/) as it looks amazing. I cloned their template repo into my Codespace, and I'm quickly able to set up Ruby's Bundler and other tooling without crowding my main dev laptop. Plus I'm running VS Code on Settings Sync so it brings Copilot and other extensions I need each time I'm in a Codespace.

Copilot is already helping me with my 'super ignorant' Ruby questions, and I'm rarely stuck for more than a few seconds on each task.

> "Copilot: How do I install a gemfile?"
{:.lead}

![Copilot Chat Example](/assets/img/blog/copilot-chat-example.png)

With my Codespace and repo setup, GitHub Actions is happily building and deploying my static site on each push to main (Configured automatically by GitHub Pages and abstracting the Ruby tooling for me!).

### Working in Markdown

Jekyll supports Markdown and Liquid based pages, to allow authoring with text editors. Markdown has gained huge popularity across GitHub and Azure DevOps documentation, so it wasn't hard to get writing.

> "Copilot: Why is my Markdown page failing to load?"
{:.lead}

> "Your page has a single character syntax issue with a semicolon in your Front Matter section" (somehow missed by VS Code itself...)

#### Markdown docs as Copilot context

Already using Markdown for your technical documentation?

Great, because as a simple markup language, these are easily searchable by Copilot!
For any docs sitting in the same repo as you're editing, they're likely already being searched by Copilot Chat when using the @workspace agent. In my case Hydejack's docs are bundled into the repo template, enabling questions like this:

> "Copilot: How do I use the Hydejack blog layout in a subdirectory?"

![Copilot Workspace Agent](/assets/img/blog/copilot-workspace-command.png)

#### Is your documentation located in other repos?

If you're on Copilot Enterprise, you're covered through [Copilot Knowledge Bases](https://docs.github.com/en/enterprise-cloud@latest/copilot/managing-copilot/managing-github-copilot-in-your-organization/enhancing-copilot-for-your-organization/managing-copilot-knowledge-bases) (previously known as Docsets). It lets you define multiple knowledge bases linked to GitHub repos, allowing targeted Q&A against any Markdown docs in those repos. This launched in GitHub.com Chat but is now in [preview in VS Code too](https://github.blog/changelog/2024-06-14-new-copilot-enterprise-features-in-vs-code-preview/), through the **@github #kb** command. This is the same way you interact with other [GitHub Copilot Extensions](https://github.blog/news-insights/product-news/introducing-github-copilot-extensions/), opening the door to lots of interesting possibilities. Docker and Octopus are two examples of companies with beta extensions out already, and I'm sure we'll have more to come.

### Results

Here's where I landed after a few hours of customising, tweaking and learning ([click here](https://benleane83.github.io/) to view if you're reading this on LinkedIn):

![Blog Homepage](/assets/img/blog/blog-homepage.png)

The finished product (for now!)
{:.figcaption}

### A glimpse into the future with Copilot Workspace

While pair programming with Copilot inside VS Code already feels great, GitHub is working hard to evolve this into something even more powerful for end-to-end software development. I've been using the [GitHub Copilot Workspace](https://githubnext.com/projects/copilot-workspace) tech preview for the last month, and I'm super impressed with how this is shaping up. It's still in experiment stages under GitHub Next for now, but look out for my thoughts in a follow-up post.
