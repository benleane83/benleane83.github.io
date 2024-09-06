---
layout: post
title: 5 reasons you're going to love Copilot Workspace
description: >
  An early look at the new Copilot Workspace IDE, in private preview mode from GitHub and already packed with exciting features
image: /assets/img/blog/workspace-banner.webp
sitemap: true
published: true
---

## 5 reasons you're going to love Copilot Workspace

I've been lucky enough to have access to the technical preview of [GitHub Copilot Workspace](https://githubnext.com/projects/copilot-workspace) for the last few months, and I'm having a blast so far!

While this is not the magic 'write a prompt, press the button and a finished piece of software pops out' app you might be dreaming of, it represents a potentially huge leap forward in abstracting developer tasks within a natural language UI. And for an early preview, I was surprised at how many fun features and general UI polishes are there already.

Why do I think this may be another game changer for developer productivity and satisfaction? Here are 5 reasons based on my own experiences (with a caveat that this is pre-release functionality and may change):

![Workspace IDE](/assets/img/blog/workspace-ide.png)

### 1. Everything is made to be edited and re-run

Wait, so the generated code isn't perfect on the first try?
Likely not. 

Like any AI editor, Workspace will get you most of the way through common programming tasks on the first attempt, and then need refining into a finished product.
Where the Workspace IDE shines though is in the '**co-editing experience**'. Every element, from the initial task prompt through to specs to code, is made to be edited and re-generated on the fly.
That means less emphasis on a perfect one-shot prompt to complete the task, and more ability to refine and even rethink as you go.

That's something other AI code generation tools have struggled with, leaving you tempted to throw away their code entirely if it's off-mark.
Hell, there are even Undo / Redo buttons built into the UI to let you experiment and back out changes with confidence!

![Workspace Regeneration](/assets/img/blog/workspace-regen.png)

### 2. Any edits made directly in your Workspace session or Codespace are synced

The new Workspace IDE lets you directly edit code on the same screen as your specs, and for minor tweaks that was perfectly fine.
But for anything substantial, you'll want to go out to Codespaces or a local IDE session.

What impressed me about Workspace was the two-way sync between the Workspace IDE and Codespace, meaning you're not forced to abandon your Workspace session as soon as you get coding yourself.
Want to go back and add some Plan steps later? Go for it!

### 3. It has an integrated terminal

Proposed code changes look good but want to check if they build or pass tests quickly?
The Workspace IDE has its own terminal built-in, which is actually backed by a Codespace and can therefore perform any command you'd normally run there.

Not entirely sure how often I'll find myself firing this up vs a full Codespace, but feels like a nice option to have on hand.

![Workspace Terminal](/assets/img/blog/workspace-terminal.png)

### 4. You can share your sessions with others

My experience so far has been mostly solo coding, but I noticed there are sharing features built into the Workspace IDE already.
That will allow you to share a snapshot of your session showing your task, plan, and proposed code changes directly with others.

That's bound to open up some interesting 'here's a draft plan I sketched out for you to review' scenarios, and could even move team collaboration earlier from Pull Request reviews into Plan reviews.

![Workspace Sharing](/assets/img/blog/workspace-sharing.png)

### 5. It works great on mobile

I wouldn't dream of opening Codespaces or other IDEs on my mobile phone, regardless of how well-built the UI feels. The tiny screen and absence of a keyboard/mouse just make any coding work beyond a one-line config change seem clunky! 

Co-editing task and plan info on my phone and letting Copilot generate the code is a different story though. In my brief trial, the mobile UI is already behaving smoothly, with what appeared to be feature parity with the web. So while I wouldn't be directly pushing code to Production from there, I'd consider at least drafting up an urgent change and sending it for review or completion later on PC. 

The Workspace IDE has a Session History page which will let you jump into previous sessions quickly on a new device.

![Workspace On Mobile](/assets/img/blog/workspace-mobile.png)

### Sounds great - when can I have it?

For now, Copilot Workspace remains in GitHub's 'Experiments' library, with no firm release plan announced. 

According to GitHub, demand for the private preview has been incredibly high however, and I'd expect that we may see some announcements coming at Universe in October. There's already lots to be excited about here, so watch this space...