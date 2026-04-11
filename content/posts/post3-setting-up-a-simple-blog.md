+++
title = "Post#3: Why I swapped LinkedIn for Hugo"
date = 2026-04-05T11:26:14+10:00
# bookComments = false
# bookSearchExclude = false
# bookPostThumbnail = "thumbnail.*"
+++

This long weekend, I finally managed to do something I have been putting off for months: I started a digital diary (blog).

In the past, I've shared my thoughts on LinkedIn, but I've realised that content on LinkedIn is a nightmare to manage. I tried to edit an image in one of my past posts, and ended up completely disturbing the content. There was no way to roll back to an older version or fix the mess. That's when I had thought of creating a space that I could  actually control.

## The Setup: Debian, Hugo and GitHub
I've been a Debian user for a long time - it's been my go-to ever since I started using Open Media Vault (OMV) for my home storage and Docker needs. It's a fantastic and rock-solid OS, which I have used to store my precious documents archive and all photos/videos.

After a bit of research on Gemini (After spending a lot of time with Perplexity, I have settled currently on Gemini for my day to day queries), I settled on Hugo hosted on GitHub pages. Setting it up was  surprisingly straightforward - just a few commands and clicks, and the site was live.

If you are thinking of starting a blog, do check out Hugo and GitHub. It should work on any desktop OS of your choice.

## The Supporting Toolkit: OpenCode and OpenRouter
To make things easier, I installed OpenCode with OpenRouter as the model backend. I initialised it right in my Hugo base folder, and OpenCode was quick to create a context file to help me provide any assistance with my Hugo setup or template errors.

I've been experimenting with a few different models on OpenRouter to see what works best:
- **Gemini 3 Flash:** My main choice. Its fast and covers my basic needs perfectly.
- **Deepseek V3.2:** Cheaper, but can be slow.
- **Claude Sonnet 4.6:** Great, but relatively expensive for simple tasks.

![OpenRouter-Activity](/images/posts/OpenRouter-Activity-2026-04-05-11-38-15.png)
*My OpenRouter Activity Snapshot*

## The Workflow
I'm a bit of a fanboy for terminal-based tools. Since I don't get to use the terminal in my day-to-day work, it feels nostalgic to spend time in it. My editor of choice is **Micro**, and I use **LazyGit** for my Git commits and pushes. The integration is seamless - as soon as I push a new post, Github Actions make they page live in a few seconds.

I did run into some initial compatibility issues between Hugo and the templates I chose, but they were easy to rectify by running a folder structure and code scan through OpenCode.

![Writing-Setup](/images/posts/Writing-Setup-2026-04-05-13-36-27.png)
*My Humble Writing Setup*

If you are thinking of getting into writing, just get started.
