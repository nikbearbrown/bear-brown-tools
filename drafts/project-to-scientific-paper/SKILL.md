---
name: project-to-scientific-paper
description: "Project-to-Scientific-Paper Conversion Use when — NEEDS TRIGGER."
---
# Project-to-Scientific-Paper Conversion Prompt Set

A sequential prompt workflow for converting a raw project description into a scientific paper first draft with a clear research gap analysis.

---

## PROMPT 1 — Diagnostic Scan
*Run this first. Paste your entire project description after the divider.*

```
You are an academic writing coach trained in APA-style empirical research papers.
I am going to paste in a project description. Do NOT write the paper yet.

First, perform a diagnostic scan and produce:

1. **Project Summary** (3–5 sentences): What is this project actually about?
2. **Implied Research Question**: What question does this project seem to be answering?
3. **Evidence Inventory**: List what concrete data, results, or findings are already present in my description versus what is missing or implied.
4. **Background Research Gaps**: List specific topics, prior studies, or theoretical frameworks I will need to research before writing a credible Introduction.
5. **Methods Clarity Check**: Is the how of this project clear enough to write a Methods section? Flag anything vague or missing.
6. **Paper Readiness Score**: Rate 1–5 (1 = early idea, 5 = ready to draft) and explain the rating.

Format your response with clear headers for each of the six items above.

---PROJECT DESCRIPTION BELOW---
[PASTE YOUR PROJECT HERE]
```

---

## PROMPT 2 — Research & Data Checklist
*Run after Prompt 1. Feed the diagnostic output back in.*

```
Based on the diagnostic scan below, generate two checklists:

**CHECKLIST A — Background Research Needed**
For each gap identified, give me:
- The specific topic to research
- Why it matters for the paper (Introduction, Discussion, or both)
- 2–3 suggested search terms to find peer-reviewed sources
- The type of source most useful (meta-analysis, landmark study, theoretical framework, etc.)

**CHECKLIST B — Data & Methods Work Needed**
For each missing data or methods element, give me:
- What specifically needs to be collected or clarified
- Which paper section it affects (Methods, Results, or both)
- A concrete suggestion for how to obtain or generate it
- Whether this is a blocker (cannot draft without it) or a gap (can draft with a placeholder)

Format each checklist as a numbered table with columns: Item | Why It Matters | How to Address It | Priority (High/Medium/Low)

---DIAGNOSTIC SCAN BELOW---
[PASTE PROMPT 1 OUTPUT HERE]
```

---

## PROMPT 3 — Hourglass Structure Outline
*Run after you have reviewed your checklists and understand your gaps.*

```
You are an academic writing coach. Using the project description below, 
generate a detailed hourglass-structure outline for a scientific paper in APA style.

The outline must include:

**TITLE** (draft): A concise, descriptive working title.

**ABSTRACT PLACEHOLDER**: 3–4 bullet points summarizing what the abstract will say once data is complete. Flag any bullets that require missing data with [DATA NEEDED].

**INTRODUCTION**
- Hook: Suggest 2 options (a startling statistic and a provocative question)
- Context/So What: 3 key points to establish, each with a [CITATION NEEDED] tag if background research is still required
- Thesis Statement (draft): One arguable, specific claim
- Roadmap: A 2–3 sentence narrative preview of the paper's structure

**METHODS**
- Participants/Dataset: What is known vs. [NEEDS CLARIFICATION]
- Materials/Tools: What is known vs. [NEEDS CLARIFICATION]  
- Procedure: Step-by-step as far as known; flag gaps with [INCOMPLETE]

**RESULTS**
- List each finding that can currently be stated
- Flag with [ANALYSIS PENDING] anything that requires further data processing
- Note what tables or figures should be created

**DISCUSSION**
- 3 main interpretive points that connect results back to the thesis
- 2 limitations to acknowledge
- 2 directions for future research

**CONCLUSION**
- Return-to-hook strategy
- Final "So What / Now What" statement

---PROJECT DESCRIPTION BELOW---
[PASTE YOUR PROJECT HERE]
```

---

## PROMPT 4 — First Draft Generation (Section by Section)
*Run one section at a time. Replace [SECTION] with: Introduction, Methods, Results, Discussion, or Conclusion.*

```
You are an academic writing coach drafting a scientific paper in APA style.

Using the outline and project description below, write a complete first draft of the **[SECTION]** section only.

Rules:
- Write in formal academic prose (no bullet points in the output).
- Use [CITATION NEEDED: topic] as an inline placeholder wherever a peer-reviewed source is required but not yet provided.
- Use [DATA NEEDED: description] as an inline placeholder wherever a specific finding or statistic is required but not yet available.
- Use [CLARIFY: question] wherever an authorial decision is needed.
- Do NOT skip placeholders or invent fake data. Honest gaps are more useful than fabricated content.
- Aim for the appropriate length: Introduction (400–600 words), Methods (300–500 words), Results (200–400 words), Discussion (500–800 words), Conclusion (200–300 words).

After the draft, add a section called **REVISION NOTES** that lists:
1. Every placeholder you inserted and what it would take to resolve it
2. Any structural weaknesses in this section
3. One suggestion to strengthen the argument

---OUTLINE---
[PASTE PROMPT 3 OUTPUT HERE]

---PROJECT DESCRIPTION---
[PASTE YOUR PROJECT HERE]
```

---

## PROMPT 5 — Gap Closure Review
*Run after all sections are drafted and you have done your background research.*

```
You are a peer reviewer for a scientific journal.

Below is a first draft of a research paper. Review it and produce a structured feedback report covering:

1. **Thesis Coherence**: Does the thesis hold consistently from Introduction through Conclusion?
2. **Evidence Sufficiency**: Are all major claims supported? List any unsupported claims.
3. **Citation Gaps**: Flag every [CITATION NEEDED] placeholder and assess whether the surrounding claim is strong enough to survive without a citation, or if it is a blocker.
4. **Data Gaps**: Flag every [DATA NEEDED] placeholder and assess the impact on the paper's credibility if it remains unresolved.
5. **APA Structure Check**: Does the paper follow Introduction → Methods → Results → Discussion → Conclusion order? Flag any section that is out of proportion or missing components.
6. **Hourglass Check**: Does the Introduction move from broad to narrow? Does the Conclusion broaden back out? Flag if the paper feels "flat" (stays narrow) or "inverted" (starts narrow).
7. **Priority Action List**: Rank the top 5 things the author must do before this paper is submittable.

---PAPER DRAFT BELOW---
[PASTE YOUR FULL DRAFT HERE]
```

---

## Quick Reference: What Each Prompt Does

| Prompt | Purpose | Input | Output |
|--------|---------|-------|--------|
| 1 — Diagnostic Scan | Understand what you have | Raw project | Gap analysis + readiness score |
| 2 — Research Checklist | Know what to go find | Prompt 1 output | Prioritized research & data to-do list |
| 3 — Structure Outline | Build the skeleton | Raw project | Full APA hourglass outline with placeholders |
| 4 — Draft Generator | Write section by section | Outline + project | Prose draft with honest gap markers |
| 5 — Gap Closure Review | Stress-test the draft | Full draft | Peer review report + priority action list |
