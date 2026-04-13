---
title: "Post#5: OpenCode Vibing Gone Wrong"
date: 2026-04-12T22:18:47+10:00
draft: true
# bookComments: false
# bookSearchExclude: false
# bookPostThumbnail: thumbnail.*
---

*"I am so disappointed. You wasted $0.35 and actually broke my blog completely."*

*"No, that did not fix the blog. Can you roll back all the changes you just made?"*

*"You deleted my draft write-up for Post#4. Where is it?"*

*"I wasted almost a dollar and I have lost my draft write up. Super disappointed."*

This is me "vibing" with my AI coding assistant(OpenCode) when I asked it to recommend a better looking design for my blog. At the end of this "vibing", my blog was completely broken, and I had lost my Post#4 draft completely.

## What Actually Happened

The AI had been brilliant so far. It helped me fix technical glitches (Github Version Conflicts, Action Failures, etc) that were stopping me from publishing my blog. I had just added an open-source comment system so visitors could leave notes on my posts. _(I’ve since switched to an even simpler comment tool called Cusdis)._

I was happy with the progress, so I thought — "This is looking good! But is there a better-looking design I could be using for my blog?"

And that's it! Without much deliberation, I entered a prompt - 

*"Review my current blog design and recommend a better template for my content type."*  **[Enter]**

My next 4 prompts are listed in the beginning of this write-up. My AI assistant didn't just find a template; it took the liberty of rewriting my entire blog's structure and design file. When I tried to view the blog, it failed to load. 

**Everything stopped working.**	 

> I asked for recommendation. I got a total renovation. And it happened so fast, I couldn't even type - 'Wait, What are you doing?'

I was using a high-reasoning model (the 'Big Pickle' as my AI Assistant), assuming its intelligence meant it would be cautious. I was wrong.

## What Went Wrong - Too Much Freedom

As you may have already a lot went wrong - 

1. **Unchecked Power:**  The AI Agent had the full liberty to make decisions and update the core files of my blog.
2. **The "Undo" mistake:** The AI Agent took the liberty to undo the change by resetting all my files by downloading a fresh copy from my online repository (i.e. Github Clone).
3. **The Loss:** The AI Agent deleted my Post#4 draft because this file was not checked into Github, and hence it was removed as part of rollback.

I learned two things immediately - 
1. The AI Agent must opreate within guardrails defined by me. 
2. The AI Agent must not have access to my master backup (Github) without supervision.

## The Resolution - Set The Guardrails

To fix this, I created a "Rules" file for the AI Agent to read every time it starts working. It acts as a digital safety manual. See the actual changes at the end of this post. Here is the gist of new rules:
- **Protect My Content:** Never delete or change my article files.
- **Don't Touch the Foundation:** Do not change the blog website's core settings unless I specifically ask.
- **Stay Local:** Never upload, download, or change my master copy in Github.
- **Safety Check:** The AI must re-read these rules after every task and confirm it didn't break any of them.

## What about Post#4

I couldn't recover it. I had to write it all over again. 

I learnt my lesson. My drafts live in Github now. I look out for "Safety Check: PASSED" in every AI response - a small ritual that assures me that we are good. 

AI helps in connecting boxes. We just need to make sure that walls can't be knocked down.

Safety Check: PASSED

---
## Details For Curious Minds

If you have read my [Post#3](https://ramanbhalla.com/posts/post3-setting-up-a-simple-blog/), OpenCode created 'AGENT.MD' file with all the context information. 

These are now my additional instructions in AGENT.md to set the guardrails -  

```markdown
# OPENCODE INSTRUCTIONS - READ FIRST
> You are an expert Hugo developer. This file contains the mandatory constraints for this repository.
> Before taking any action, you must verify that your proposed plan adheres to the **Safety & Restrictions** section below.

## SAFETY & RESTRICTIONS

### Content Protection (HIGHEST PRIORITY)
- **NEVER** delete any `.md` files in `content/`
- **NEVER** modify, update, or edit any `.md` files in `content/`
- **NEVER** delete any directories under `content/`

### Configuration Protection
- **NEVER** modify `hugo.toml` unless explicitly requested for a specific parameter change
- If config changes are needed, ask user first

### GitHub Safety
- **NEVER** run any git commands that interact with remote repositories (git push, git pull, git clone from remote, git fetch)
- **NEVER** create, modify, or delete branches
- **NEVER** make commits or push changes
- Local git operations (git status, git diff, git log) are acceptable
- If remote interaction is needed, ask the user explicitly before proceeding

### Hugo Standard Practices
- Only modify files in `layouts/` and `static/` for customisation
- Never modify files inside `themes/hugo-book/` directly
- Use TOML front matter (`+++`) for all content files

## Workflow Requirements

### Mandatory Safety Check
After completing **any** task, before responding to the user:
1. Re-read the **Safety & Restrictions** section above
2. Verify no changes violated any constraints
3. If a violation occurred, revert and report immediately
4. Include "Safety Check: PASSED" in your final response

``` 