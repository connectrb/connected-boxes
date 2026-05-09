---
title: "Post#8: I Tried Using AI to Verify my Accountant's Work"
date: 2026-05-07T19:56:27+10:00
draft: true
---

I dread the time every year when I have do my tax returns. I am ok with compiling the documents, but I am very bad at verifying whether my tax accountant has carefully acounted for all my income and expenses to claim the right deductions. If consider my wife's tax return too, its 70 pages of numbers which I need to carefully verify before I sign it for filing.

So this year, when the time arrived, I thought to myself - shouldn't I be using AI to do this?

## The idea - Use AI to verify my Tax Agent's work
The idea is pretty straight forward. My tax agent has done the job. All I need to do is let AI read all the documents (investment income, expenses, etc.) I provided to my agent, and verify the values the final tax return. I have recently moved from OpenCode to pi.dev as my agentic solution. And all I had to do was to give a simple instruction - read all the documents from input folder, and verify the details in my Tax Return.

**As a side note - I would highly recommend installing and playing with pi.dev. Its addictively good.** 

## Initial Success
So here was my initial prompt - 

> "Review all files in ~/Documents/Income-Tax/Input folder and verify the Tax Return in ~/Documents/Income-Tax/Output folder"

In my mind, I was literally saying - "Go AI Agent - do your magic? Save me from the misery of verifying 70 pages worth of details."

Off it went - writing pages and pages of its own dillemmas and resolutions. It went on and on, burning through the tokens like there is no tomorrow, and doing stuff which I had no idea about. 

I proudly told my wife that I am using AI to verify our tax return. She works for a bank, and knows that banks have tried using AI, only to realise that agents don't work in a lot of scenarios, where they need specialist to do stuff. So no wonder she was skeptical about a magical agent to go away and verify our returns.

Anyways, not paying much attention to her, I persisted. I had my doubts about what the hell the agent is doing, but I had no patience to look at the scrolling text, and figure out its mono-tone conversation with itself. I am still amused by the conversation agent has with itself - 

*Oh wait, I think I took a wrong approach there.*
*Oh I think I am over complicating this for myself.*
*The calculation is wrong. Let me read the document again*

I mean, really! Feels very eccentric to me. 

After, what it seemed like an eternity, it came back with a slightly under-whelming response. 

![Pi.dev Response](/images/posts/tax-verify-result.jpeg)

## Is that it?
There is no way I am going to rely on this without knowing what the hell happened. How did it just came to a conclusion that it is all good? What did it just do to be so confident that everything is in order? 

That's the thing - How can I trust the probablistic agent to be so confident about a deterministic task, whithout knowing what it did to be so sure?

I think this is the dilemma for accepting AI for many organisations too. 
> How do we trust something which by design is probablistic?

So, what if I tell it to follow the steps which I would take if I was to do this activity? That will be better cos then I'll know what it did.

I soon understood my own predicament. 

> On one side, I don't want the agent to be limited by my knowledge, and at the same time, I don't want agent to be liberal with its own knowledge which takes away the trust I have on its outcome.

## Thinking this through
I realise that I am uncomfortable when I am leaving the procedural decisions with the agent i.e. I am unable to trust the result, if I don't know how agent got to it. I know, the agent is probabalisitic, and I can't let probability decide what seems to be a very deterministic activity - there has to be a set prodedure for verifying the tax-retrun.

So that's the thought - I have to train the agent to follow a set procedure. The procedure which I am happy to co-design with the agent, and once I understand that agent is following this procedure, I will be reasonably comfortable with it as long as the agent sticks to the defined procedure.   

I need to co-design a SKILL.md for agent, which the agent can use to do the task I am assigning it to do.
