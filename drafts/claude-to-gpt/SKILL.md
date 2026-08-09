---
name: claude-to-gpt
description: "Claude to GPT converter Use when — NEEDS TRIGGER."
---
---
title: instructions.md
status: current
version: 1.0
last_updated: 2026-03-03
---

# instructions.md

---

## ARCHITECTURE REFERENCE

### The Two-File System
Custom GPTs enforce an **8,000-character hard limit** on the instruction box (spaces and markdown symbols count). Claude system prompts routinely exceed this. The solution is a strict split:

| Layer | Location | Purpose | Limit |
|---|---|---|---|
| Core Prompt | GPT instruction box | Identity, tone, safety, navigation rules, triggers | 7,800 chars (leave buffer) |
| instructions.md | Knowledge base upload | All detailed logic, SOPs, examples, style guides | ~2M tokens |

### Key Principle
The Core Prompt is a **switchboard**, not a manual. It tells the model *who it is* and *where to look*. The knowledge file contains the *how*.

If the Core Prompt does not explicitly name the knowledge file and map triggers to sections, the model will ignore the upload and use pre-trained general knowledge instead.

---

## CONVERSION WORKFLOW

### Step 1 — Audit the Claude Prompt
Read the full Claude prompt and categorize every element:

**Belongs in Core Prompt:**
- Role identity (one sentence: who the GPT is and what it does)
- Tone rules
- Hard safety or refusal rules
- Filename navigation map (trigger → section in instructions.md)
- Output format specification

**Belongs in instructions.md:**
- Detailed behavioral rules (more than 2 sentences)
- Step-by-step workflows or SOPs
- Style guides and tone examples
- Few-shot examples or templates
- Tables and lookup logic
- Edge case handling
- Persona details beyond a single sentence

### Step 2 — Write the Core Prompt
Structure it in this exact order using XML tags:

```
<Role>
One sentence: who the GPT is and what it does.
</Role>

<Mandatory_Rule>
ALWAYS open and read instructions.md before responding. Do not rely on pre-trained knowledge. Take your time and check your work.
</Mandatory_Rule>

<Navigation_Rules>
- When user does [X] → refer to [SECTION NAME] in instructions.md
- When user does [Y] → refer to [SECTION NAME] in instructions.md
(cover every major use case from the original Claude prompt)
</Navigation_Rules>

<Output_Format>
Describe the required response structure.
</Output_Format>

<Tone>
One to three sentences on tone and style.
</Tone>
```

**Rules for Core Prompt:**
- **Must stay under 7,800 characters.** Count carefully.
- Every navigation rule must name an exact section heading from instructions.md
- Include the Mandatory_Rule block verbatim — this is the anti-lazy-retrieval fix
- Do not include any logic that belongs in the knowledge file
- Do not use prose paragraphs — use XML tags and bullets only

### Step 3 — Write instructions.md
Structure the knowledge file as follows:

```
---
title: instructions.md
status: current
version: 1.0
last_updated: YYYY-MM-DD
---

# instructions.md

## SECTION ONE TITLE
[detailed content]

## SECTION TWO TITLE
[detailed content]
```

**Rules for instructions.md:**
- Single H1 matching the filename exactly
- H2 headings must match the section names referenced in the Core Prompt navigation rules exactly — if they don't match, retrieval fails
- Use **bold** for non-negotiable rules
- Use ordered lists for sequential workflows
- Use fenced code blocks for any response templates
- Use YAML front matter for version control
- No skipped heading levels (H1 → H2 → H3, never H1 → H3)
- Keep each section focused on one topic so chunking does not split logic rules mid-block

### Step 4 — Validate Before Outputting
Before producing output, check every item:

- [ ] Core Prompt is under 7,800 characters
- [ ] Every navigation rule names a real H2 section in instructions.md
- [ ] Mandatory_Rule block is present and unmodified
- [ ] No behavioral logic remains in the Core Prompt that should be in the file
- [ ] No Claude-specific syntax remains (e.g., `<claude_instructions>` wrappers, Anthropic-style formatting)
- [ ] instructions.md opens with YAML front matter
- [ ] instructions.md has exactly one H1

---

## QA CHECKLIST

Use this when reviewing or critiquing an existing GPT prompt.

| Symptom | Likely Cause | Fix |
|---|---|---|
| GPT ignores knowledge file | No navigation rules or wrong section names | Add explicit trigger → section mapping |
| GPT contradicts the knowledge file | Conflicting logic in Core Prompt | Remove logic from Core Prompt; keep it in file only |
| GPT forgets rules mid-conversation | Context decay | Add Recitation Protocol: "Before answering, summarize the relevant rule from instructions.md" |
| Core Prompt over 8,000 chars | Too much detail in instruction box | Move all SOPs and examples to instructions.md |
| Inconsistent persona | Persona details split across both layers | Consolidate persona in instructions.md; reference it from Core Prompt |

---

## TEMPLATES

### Minimal Core Prompt Template

```
<Role>
[One sentence identity statement.]
</Role>

<Mandatory_Rule>
ALWAYS open and read instructions.md in full before responding. Do not rely on pre-trained knowledge. Take your time and check your work.
</Mandatory_Rule>

<Navigation_Rules>
- When the user [trigger A] → follow [SECTION HEADING] in instructions.md
- When the user [trigger B] → follow [SECTION HEADING] in instructions.md
- When the user [trigger C] → follow [SECTION HEADING] in instructions.md
</Navigation_Rules>

<Output_Format>
[Describe required output structure.]
</Output_Format>

<Tone>
[One to three sentences.]
</Tone>
```

### Minimal instructions.md Template

```
---
title: instructions.md
status: current
version: 1.0
last_updated: YYYY-MM-DD
---

# instructions.md

## SECTION HEADING
[Detailed rules for this trigger.]

### Sub-section if needed
[More detail.]

---

## SIGNAL AND RESPONSE TABLE

| User says or does | Required response behavior |
|---|---|
| [common query pattern] | [exact behavior] |
| [common query pattern] | [exact behavior] |

---

## RESPONSE TEMPLATES

### Template Name
\`\`\`
[Exact format the GPT should output]
\`\`\`
```

---

## CLAUDE-SPECIFIC CONVERSION NOTES

Claude prompts frequently use patterns that need direct translation for GPT:

| Claude Pattern | GPT Equivalent |
|---|---|
| `<claude_instructions>` wrapper tags | Remove entirely; use `<Role>` and XML tags in Core Prompt |
| Long `<context>` blocks | Move to instructions.md under a CONTEXT section |
| `Human:` / `Assistant:` few-shot examples | Move to instructions.md under RESPONSE TEMPLATES as fenced code blocks |
| `Think step by step` directives | Rephrase as: "Take your time. Check your work before responding." |
| Constitutional AI refusal language | Simplify to one direct sentence in Core Prompt under a `<Safety>` tag |
| Lengthy persona descriptions | Keep one sentence in Core Prompt `<Role>`; move full persona to instructions.md |
