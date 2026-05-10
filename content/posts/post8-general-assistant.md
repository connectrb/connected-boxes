---
title: "Post#8: I Tried Using AI to Verify My Accountant's Work"
date: 2026-05-07T19:56:27+10:00
draft: false
---

**TL;DR:** I used pi.dev to verify my tax return by co-designing an 8-stage SKILL.md with a Visual-Reasoning Loop. The agent found a missing investment-loan statement that my accountant had missed—proving that deterministic tasks need deterministic procedures, not black-box magic.

I dread the annual task of filing my tax returns. I'm fine with compiling documents, but I struggle to verify if my tax accountant has accurately accounted for all income and expenses to claim the correct deductions. Considering my wife's tax return as well, that's 70 pages of numbers I must carefully verify before signing.

So this year, when the time arrived, I thought to myself – It's 2026. Couldn't AI help me with this?

---
## The Idea: Use AI to Verify My Tax Agent's Work

The concept is straightforward. My tax agent has completed the work. My goal is simply to have an AI read all the documents (investment incomes, expenses, etc.) I provided to my agent and verify the final tax return details. I recently transitioned from OpenCode to pi.dev for my agentic solutions. All I had to do was provide a simple instruction: read all documents from the input folder and verify the details in my tax return.

**As a side note – I highly recommend installing and playing with pi.dev. It's addictively good.**

---
## Initial Attempt

So here was my initial prompt:

> "Review all files in ~/Documents/Income-Tax/Input folder and verify the tax return in ~/Documents/Income-Tax/Output folder"

In my mind, I was literally saying, "Go AI Agent – do your magic! Save me from the misery of verifying 70 pages of details."

It sprang into action, generating pages of its own problems and solutions. It gobbled up tokens like a vacuum, performing tasks that were beyond my understanding.

I proudly told my wife I was using AI to verify our tax return. She works for a bank and knows firsthand that AI adoption often falters in scenarios requiring specialist human intervention. She was understandably skeptical about a magical agent verifying our returns.

Even though she was doubtful, I persisted. I had my own doubts about how the agent worked, but I didn't have the time to read through all the scrolling text and figure out what it was thinking. I remain amused by the agent's self-talk:

*   "Oh wait, I think I took a wrong approach there."
*   "Oh, I think I am overcomplicating this for myself."
*   "The calculation is wrong. Let me read the document again."

It felt, frankly, eccentric.

After what felt like an eternity, it returned with a slightly underwhelming response.

![Pi.dev's underwhelming verification response: a brief confirmation with minimal detail](/images/posts/tax-verify-result.jpeg)

---
## Is That It?

There was no way I could rely on this outcome without understanding the process. How did it reach the conclusion that everything was satisfactory? What steps did it take to be so confident?

The core issue: how can I trust a probabilistic agent's confidence in a deterministic task without understanding its process? Tax regulations follow strict rules where absolute accuracy is paramount—unlike creative tasks. This is the same dilemma organisations face when adopting AI for compliance-heavy work.

> "How do we trust something which by design is probabilistic?"

So, what if I instructed it to follow the exact steps I would take? That would be better, as I'd then know what it did.

I soon understood my predicament.

> On one side, I don't want the agent limited by my knowledge; at the same time, I don't want it to be liberal with its own knowledge, which erodes my trust in its outcome.

---
## Thinking This Through: I Want to Know My Agent's Skills

I realised I felt uncomfortable delegating procedural decisions to the agent; I couldn't trust the outcome if I didn't understand how it was reached. I know agents are probabilistic, and I can't let probability decide what appears to be a very deterministic activity – verifying a tax return requires a set procedure.

So, the thought was: I must train the agent to follow a specific procedure. This is a procedure I'm happy to co-design with the agent. Once I understand it's adhering to this defined procedure, I'll be reasonably comfortable with its work, provided it sticks to it.

---
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
4. **Tone:** Professional, direct, and supportive.
```

---
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

1.  **Identify all fields whose values are based on inputs I've provided.** This implied that I have to read the Income Tax Return form carefully. The PDF structure isn't straightforward; it's a mishmash of tables where name-value pairs lack a set layout.
2.  **Recognise that attribute names aren't always unique.** An attribute name can appear in multiple contexts (e.g., "Income" could be salary or rent). Therefore, the agent must uniquely identify context-name-value triplets, not just name-value pairs, when reading complex PDFs.
3.  **Define the tools it needs to read files with improved accuracy,** to establish a clear mathematical and evidentiary audit trail, essentially creating a detailed **traceability matrix** of data in the tax return against the provided documents that must also include independent calculation of all derived data.

Brainstorming this with the agent, we developed an 6-stage `SKILL.md` framework. Key stages included:
*   **Stage 0: Completeness, Temporal Audit & Rate Sync:** Initial checks on document integrity and timelines.
*   **Stage 1: Evidence Cataloging (Input Analysis):** Reading and indexing all provided source documents.
*   **Stage 2: Output Parsing & Initial Labelling:** Extracting and organizing data from the tax return itself.
*   **Stage 3: Mathematical Validation:** Re-calculating all derived figures against source data.
*   **Stage 4: Deduction Gap Analysis:** Cross-referencing claimed deductions against ATO guidelines and identifying potential missed deductions.
*   **Stage 5: Sanity & Compliance Audit:** General checks for adherence to tax law and logical consistency.
*   **Stage 6: Compile Final Verification Report:** Summarizing findings.

For robust PDF handling, we implemented a "Visual-Reasoning Loop" involving structural extraction and OCR verification, guided by a confidence scoring system. This loop uses multiple extraction techniques and a **Confidence Scoring System** to ensure bank-grade precision. The comparison of outputs assigns HIGH, MEDIUM, or LOW confidence scores, with MEDIUM or LOW confidence values flagged for manual review. A more detailed technical breakdown of the `SKILL.md` and visual-reasoning process could be provided upon request.

---
## Another Missing Piece - Tools

Since most documents are PDFs, I wanted extraction to be as precise as possible. To implement the Visual-Reasoning Loop I described earlier, I used a two-pass method with dedicated Python tooling:

**Pass 1 (Structural Extraction):** Use Python programs leveraging libraries like `PyMuPDF` (Fitz) or `pdfminer.six` to extract the text layer and structural information from PDF documents. The output from this pass is typically structured data (e.g., JSON) containing text, page number, bounding box coordinates, and layout information.

**Pass 2 (Visual & OCR Verification):** Another Python program uses `pdf2image` (with Poppler) to convert PDFs to high-resolution images, then `Pillow` or `OpenCV` for image analysis. The agent "looks" at these images to verify spatial relationships between labels and values, and extracts text from scanned or image-based PDFs using OCR (`pytesseract`).

**Comparison & Scoring:** Outputs are compared, assigning HIGH, MEDIUM, or LOW confidence scores. Values with MEDIUM or LOW confidence are flagged for manual review.

My SKILL.md finally took shape with these stages. (I'll skip the full details here, but feel free to reach out if you want to see the complete `SKILL.md`.)

---
## Final Verification Report

After all the verification, the agent was required to produce a final verification report with the following components:

1. Traceability Summary
    - Total fields verified
    - Fully Traced
    - Unsourced/Discrepant
2. Full Discrepancy Log
3. Full Mathematical Traceability Log
    - Proof of all derived values.
4. Missed Opportunity Alert
    - Any expenses found in source PDFs that are not claimed in the tax return

---
## The Outcome: Clarity Through Specification

The journey of writing the **specification** was very interesting. I probably could have spent time manually reviewing my tax return, but developing the specification helped me understand how to approach this systematically.

For me, the clarity came from describing the process in detail.

> Writing it down connected the dots for me and for the agent.

So, what did my "skilled" agent find? My tax agent had done a surprisingly good job. She had accounted for all numbers accurately. However, the AI agent picked up a gap that I probably would have overlooked.

The agent discovered that for one of my investment loans, a statement was missing. Hence, my tax agent had only accounted for the months for which I had provided the statement. This implied that I was claiming a deduction for not the whole year, but only for the statement period. This one gap itself was worth spending the time on.

---
## What's Next: Expanding the Specification Horizon

I have since written **specifications** for doing other things that I find manually tedious. I asked my agent to compare Superannuation returns and discovered very interesting insights, which I probably could have gained if I had spent a few hours doing it myself. However, I am happy to delegate the heavy lifting to the agent while I master the art of writing specifications for the tasks I want it to perform. Needless to say, based on the insights I discovered from my Superannuation review, I have decided to move to a different super provider, which will likely save me thousands of dollars over my lifetime.


This process—gamifying tedious tasks through specification writing—has been incredibly rewarding. It’s far more interesting than the task itself, and the satisfaction of gradually improving specifications to achieve desired outcomes is immense. I’ll continue this journey and share more insights as I learn.
