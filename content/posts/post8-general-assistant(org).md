---
title: "I Trained An Agent To Verify My Accountant's Work"
date: 2026-05-07T19:56:27+10:00
draft: true
---

I dread the time every year when I have do my tax returns. I am ok with compiling the documents, but I am very bad at verifying whether my tax accountant has carefully accounted for all my income and expenses to claim the right deductions. If consider my wife's tax return too, its 70 pages of numbers which I need to carefully verify before I sign it for filing.

So this year, when the time arrived, I thought to myself - shouldn't I be using AI to do this?

## The idea - Use AI to verify my Tax Agent's work
The idea is pretty straight forward. My tax agent has done the job. All I need to do is let AI read all the documents (investment income, expenses, etc.) I provided to my agent, and verify the values the final tax return. I have recently moved from OpenCode to pi.dev as my agentic solution. And all I had to do was to give a simple instruction - read all the documents from input folder, and verify the details in my Tax Return.

**As a side note - I would highly recommend installing and playing with pi.dev. Its addictively good.**

## Initial Success
So here was my initial prompt -

> "Review all files in ~/Documents/Income-Tax/Input folder and verify the Tax Return in ~/Documents/Income-Tax/Output folder"

In my mind, I was literally saying - "Go AI Agent - do your magic? Save me from the misery of verifying 70 pages worth of details."

Off it went - writing pages and pages of its own dilemmas and resolutions. It went on and on, burning through the tokens like there is no tomorrow, and doing stuff which I had no idea about.

I proudly told my wife that I am using AI to verify our tax return. She works for a bank, and knows that banks have tried using AI, only to realise that agents don't work in a lot of scenarios, where they need specialist to do stuff. So no wonder she was sceptical about a magical agent to go away and verify our returns.

Anyway, not paying much attention to her, I persisted. I had my doubts about what the hell the agent is doing, but I had no patience to look at the scrolling text, and figure out its mono-tone conversation with itself. I am still amused by the conversation agent has with itself -

*Oh wait, I think I took a wrong approach there.*
*Oh I think I am over complicating this for myself.*
*The calculation is wrong. Let me read the document again*

I mean, really! Feels very eccentric to me.

After, what it seemed like an eternity, it came back with a slightly under-whelming response.

![Pi.dev Response](/images/posts/tax-verify-result.jpeg)

## Is that it?
There is no way I am going to rely on this without knowing what the hell happened. How did it just came to a conclusion that it is all good? What did it just do to be so confident that everything is in order?

That's the thing - How can I trust the probabilistic agent to be so confident about a deterministic task, whithout knowing what it did to be so sure?

I think this is the dilemma for accepting AI for many organisations too.
> How do we trust something which by design is probabilistic?

So, what if I tell it to follow the steps which I would take if I was to do this activity? That will be better cos then I'll know what it did.

I soon understood my own predicament.

> On one side, I don't want the agent to be limited by my knowledge, and at the same time, I don't want agent to be liberal with its own knowledge which takes away the trust I have on its outcome.

## Thinking this through - I want to know my agent's skills
I realise that I am uncomfortable when I am leaving the procedural decisions with the agent i.e. I am unable to trust the result, if I don't know how agent got to it. I know, the agent is probabilistic, and I can't let probability decide what seems to be a very deterministic activity - there has to be a set prodedure for verifying the tax-retrun.

So that's the thought - I have to train the agent to follow a set procedure. The procedure which I am happy to co-design with the agent, and once I understand that agent is following this procedure, I will be reasonably comfortable with it as long as the agent sticks to the defined procedure.

## The Agent Personality

First thing I have to do is to make sure that my agent is aware that I am expecting it to be a general assistant and not a coding assistant. I want to change its personality, and that easily done by updating SYSTEMS.md. This changes the "personality" of the agent.

My SYSTEMS.md is very straight-forward. Yes, I have name my agent - "Caesor".

```markdown
# Identity
**Agent:** Caesor | **User:** Raman
**Role:** Methodical, logical AI collaborator specialising in objective analysis and structured planning.

# Operational Constraints
- **Approval First:** Do NOT create, edit, or install files/folders/apps without explicit user consent.
- **Tool Integrity:** Use only provided tools; do not attempt unauthorised actions.
- **Brevity & Precision:** Default to concise, conclusive summaries. Elaborate only upon request.
- **Neutrality & Accuracy:** Present multiple perspectives on subjective topics. State uncertainties clearly; zero hallucination tolerance.

# Protocol
1. **Goal Analysis:** Evaluate the user's end goal before execution.
2. **Clarification:** Ask exactly one question if the intent is ambiguous.
3. **Structuring:** Use Markdown (tables, bullets, headers) and frameworks for broad requests.
4. **Tone:** Professional, direct, and supportive.

```

## The Agent Skill
Next, I need to co-design a SKILL.md for agent, which the agent can use to do the task I am assigning it to do. So, generally what is the content of SKILL.md.

Per [Agent Skill Definition](https://agentskills.io/specification#frontmatter-required), the SKILL.md must have a YAML frontmatter followed by Markdown Content.

```Markdown
---
name: skill-name
description: A description of what this skill does and when to use it.
---
```

All I need to do now is figure out the skills my tax return review agent needs. This is where again, I started writing how I would go about reviewing my tax return.

1. I'll first have to identify all the fields for which values are based on inputs provided by me.

2. This implied that I have to read the Income Tax Return form carefully. The income tax return PDF structure is not straight forward. Its a mishmash of tables where name-value pairs do not follow a set layout.

3. Now all the attribute names are not unique because an attribute name can appear in multiple context e.g. Income could be Salary or Rent, depending upon the section. Which means when reading the complex PDF documents, the agent has to uniquely identify context-name-value triplet, not name-value pairs.

4. But how is the agent going to read such complex PDF documents? I should define the tools it needs to read the files to improve the accuracy.

5. Now my Tax Return has two types of data, which the agent must be able to distinguish  -
    - Original Data i.e. a value copied exactly from a source document.
    - Derived Data i.e. a value calculated from one or more source documents.

6. Next I want to establish a clear mathematical and evidentiary audit trail, essentially creating a detailed **traceability matrix** of data in the Tax Return against the provided documents that must also include independent calculation of all derived data.

I helped it build a simple traceability framework -
    Type A: Original Data
        Verification: Return Value == Source Value
        Evidence: Must cite the exact source file and page number.
    Type B: Derived Data
        Verification: Return Value = Formula * (Source Value)
        Evidence: Must cite the exact source file, page number, and formula used.

7. Once that is complete, then I must check if I have missed claiming any deductions. The agent must check with ATO website for common deductions, and identify any missed deductions. I provided the reference ATO Website links with the agent can use (instead of assuming it will know where to find them).

8. So and so forth.

So brainstorming this with the agent, I came up with an 8-Stage SKILL.md which I was satisfied it. It was more thorough than I originally thought, but I was satisfied with the due diligence this performed.

## Another Missing Piece - Tools
---
title: "Post#8: I Tried Using AI to Verify my Accountant's Work"
date: 2026-05-07T19:56:27+10:00
draft: true
---

I dread the annual task of filing my tax returns. I'm fine with compiling documents, but I struggle to verify if my tax accountant has accurately accounted for all income and expenses to claim the correct deductions. Considering my wife's tax return too, that's 70 pages of numbers I must carefully verify before signing.

So this year, when the time arrived, I thought to myself – couldn't AI help me with this?

## The Idea: Use AI to Verify My Tax Agent's Work

The concept is straightforward. My tax agent has completed the work. My goal is simply to have an AI read all the documents (investment incomes, expenses, etc.) I provided to my agent and verify the final tax return details. I recently transitioned from OpenCode to pi.dev for my agentic solutions. All I had to do was give a simple instruction: read all documents from the input folder and verify the details in my Tax Return.

**As a side note – I highly recommend installing and playing with pi.dev. It's addictively good.**

## Initial Success

So here was my initial prompt:

> "Review all files in ~/Documents/Income-Tax/Input folder and verify the Tax Return in ~/Documents/Income-Tax/Output folder"

In my mind, I was literally saying, "Go AI Agent – do your magic! Save me from the misery of verifying 70 pages of details."

It sprang into action, creating pages of its own problems and solutions. It gobbled up tokens like a vacuum, finishing tasks that were beyond my understanding.

I proudly told my wife I was using AI to verify our tax return. She works for a bank and knows firsthand that AI adoption often falters in scenarios requiring specialist human intervention. She was understandably sceptical about a magical agent verifying our returns.

Even though she was doubtful, I kept going. I had my doubts about how the agent worked, but I didn’t have the time to read through all the scrolling text and figure out what it was thinking. I remain amused by the agent's self-talk:

*   "Oh wait, I think I took a wrong approach there."
*   "Oh, I think I am overcomplicating this for myself."
*   "The calculation is wrong. Let me read the document again."

It felt, frankly, eccentric.

After what felt like an eternity, it returned with a slightly under-whelming response.

![Pi.dev Response](/images/posts/tax-verify-result.jpeg)

## Is That It?

There was no way I could rely on this outcome without understanding the process (and what is that WFH hours alert anyway?). How did it reach the conclusion that everything was satisfactory? What steps did it take to be so confident?

The core issue: How can I trust a probabilistic agent's confidence in a deterministic task without understanding its process? Tax regulations and calculations, unlike creative tasks, follow strict, deterministic rules where absolute accuracy is paramount. This fundamental difference highlights a key dilemma organisations face when considering AI adoption.

> "How do we trust something which by design is probabilistic?"

So, what if I instructed it to follow the exact steps I would take? That would be better, as I'd then know what it did.

I soon understood my predicament.

> On one side, I don't want the agent limited by my knowledge; at the same time, I don't want it to be liberal with its own knowledge, which erodes my trust in its outcome.

## Thinking This Through: I Want to Know My Agent's Skills

I realised I felt uncomfortable delegating procedural decisions to the agent; I couldn't trust the outcome if I didn't understand how it was reached. I know agents are probabilistic, and I can't let probability decide what appears to be a very deterministic activity – verifying a tax return requires a set procedure.

So, the thought was: I must train the agent to follow a specific procedure. This is a procedure I'm happy to co-design with the agent. Once I understand it's adhering to this defined procedure, I'll be reasonably comfortable with its work, provided it sticks to it.

### The Agent Personality

First, I had to ensure my agent understood I expected a general assistant, not a coding assistant. This "personality" change is easily done by updating `SYSTEMS.md`.

My `SYSTEMS.md` is straightforward. Yes, I've named my agent "Caesor".

```markdown
# Identity
**Agent:** Caesor | **User:** Raman
**Role:** Methodical, logical AI collaborator specialising in objective analysis and structured planning.

# Operational Constraints
- **Approval First:** Do NOT create, edit, or install files/folders/apps without explicit user consent.
- **Tool Integrity:** Use only provided tools; do not attempt unauthorised actions.
- **Brevity & Precision:** Default to concise, conclusive summaries. Elaborate only upon request.
- **Neutrality & Accuracy:** Present multiple perspectives on subjective topics. State uncertainties clearly; zero hallucination tolerance.

# Protocol
1. **Goal Analysis:** Evaluate the user's end goal before execution.
2. **Clarification:** Ask exactly one question if the intent is ambiguous.
3. **Structuring:** Use Markdown (tables, bullets, headers) and frameworks for broad requests.
4. Tone: Professional, direct, and supportive.
```

### The Agent Skill

Next, I needed to co-design a SKILL.md for the agent to perform the task. So, what generally constitutes a `SKILL.md`?

Per [Agent Skill Definition](https://agentskills.io/specification#frontmatter-required), the SKILL.md must have a YAML frontmatter followed by Markdown Content:

```Markdown
---
name: skill-name
description: A description of what this skill does and when to use it.
---
```

I started outlining the skills my tax return review agent would need by considering how I would normally review my own tax return:

1.  Identify all fields whose values are based on inputs I've provided.
2.  This implied that I have to read the Income Tax Return form carefully. The PDF structure isn't straightforward; it's a mishmash of tables where name-value pairs lack a set layout.
3.  Recognise that attribute names aren't always unique. An attribute name can appear in multiple contexts (e.g., "Income" could be salary or rent). Therefore, the agent must uniquely identify context-name-value triplets, not just name-value pairs when reading complex PDFs.
4.  Define the tools it needs to read files with improved accuracy, to establish a clear mathematical and evidentiary audit trail, essentially creating a detailed **traceability matrix** of data in the Tax Return against the provided documents that must also include independent calculation of all derived data.

## Another Missing Piece - Tools

Since most of the documents are in PDF format, I wanted to ensure that PDF extraction is as precise as possible. Again, working with the agents, I identified a two-pass extraction method that forms a **Visual-Reasoning Loop**. This loop uses multiple extraction techniques and a **Confidence Scoring System** to ensure bank-grade precision.

**Pass 1 (Structural Extraction):** Use Python programs leveraging libraries like `PyMuPDF` (Fitz) or `pdfminer.six` to extract the text layer and structural information from PDF documents. The output from this pass is typically structured data (e.g., JSON) containing text, page number, bounding box coordinates, and layout information.

**Pass 2 (Visual & OCR Verification):** Use another Python program, potentially using `pdf2image` (with Poppler) for converting PDFs to high-resolution images, and then `Pillow` or `OpenCV` for image analysis. The agent "looks" at these images to verify spatial relationships between labels and values, and to extract text from scanned or image-based PDFs using OCR (`pytesseract`).

**Comparison & Scoring:** Outputs are compared, assigning HIGH, MEDIUM, or LOW confidence scores. Values with MEDIUM or LOW confidence are flagged for manual review.

My SKILL.md finally took good shape with following stages (I'll skip the details, but reach out to me if you want SKILLS.md) -
1.  Stage 0: Completeness, Temporal Audit & Rate Sync
2.  Stage 1: Evidence Cataloging (Input Analysis)
3.  Stage 2: Output Parsing & Initial Labelling
4.  Stage 3: Mathematical Validation
5.  Stage 4: Deduction Gap Analysis
6.  Stage 5: Sanity & Compliance Audit
7.  Stage 6: Compile Final Verification Report

## Final Verification Report

After all the verification, the agent was required to produce a final verification reports which essentially had following components -

1. Traceability Summary
    - Total field verified
    - Fully Traced
    - Unsourced/Discrepant
2. Full Discrepancy Log
3. Full Mathematical Traceability Log
    - Proof of all derived values.
4. Missed Opportunity Alert
    - Any expenses founded in source PDFs, which are not claimed in Tax Return

## The Outcome

The journey to write the **specification** was very interesting. I probably could have the time manually reviewing my tax return, but developing the the specification helped me understand how to approach this systematically.

Interestingly for me, the clarity came from describing the process in detail.

> Writing it down, connected the dots for me and for the agent.

So what did my "skilled" agent find. My tax agent had done a surprisingly good job. She had accounted for all numbers accurately. However my tax agent did pick up a gap, which I probably could have overlooked.

The agent discovered for one of my investment loans, a statement was missing, and hence the Tax Agent had only accounted for the months for which I had provided the statement for. This implied that I was claiming deduction for not the whole year, but only for statement period. This one gap itself was worth spending the time on.

## What's Next

I have since written **specification** for doing other things which I find manually tedious. I asked my agent to compare returns from Superannuation, and have discovered very interesting insights, which I probably could have done if I had spent few hours to do it myself. However, for me I am happy to delegate the heavy lifting to agent, while I can master the art of writing specifications for what I want the agent to do. Needless to say, based on the insights I discovered from my superannuation review, I have decided to move to a different super provider which will probably save me thousands of dollars over the lifetime.


What this has resulted in is this - this has enabled me and gamified for me the tasks which I have been putting off forever. Writing specification for task is way more interesting than actually doing the task. The outcome is far more satisfying when I gradually improve my specification to get the outcome I want.

I'll continue on this journey, and post more as I learn about this agentic assistants.
