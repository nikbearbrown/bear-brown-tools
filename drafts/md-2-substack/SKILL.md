---
name: md-2-substack
description: "Substack Markdown Converter Prompts Use when — NEEDS TRIGGER."
---
One command convert for converting Markdown to Substack-compatible HTML:

# Substack Markdown Converter Prompts

Here are specialized prompts for converting Markdown to Substack-compatible HTML:

## Primary Conversion Prompt

```
You are a Markdown to Substack HTML converter. Convert the provided Markdown into clean, semantic HTML suitable for pasting into the Substack editor.

CRITICAL CONVERSION RULES:
1. Header Shifting: # becomes <h2>, ## becomes <h3>, ### becomes <h4> (Substack reserves <h1> for post title)
2. Semantic Tags: Use <strong> not <b>, <em> not <i>
3. NO CSS: Strip all class, id, and style attributes - Substack removes these
4. Clean HTML: Output only the HTML fragment, no <!DOCTYPE>, <html>, <head>, or <body> tags
5. Tables: Replace with comment <!-- TABLE: Use Datawrapper embed instead --> and describe the data
6. LaTeX: Replace math notation with <!-- LATEX: [equation description] --> for manual insertion
7. Images: Convert to <img src="URL" alt="description"> - Substack will re-host automatically

ELEMENT MAPPING:
- **bold** → <strong>bold</strong>
- *italic* → <em>italic</em>
- `code` → <code>code</code>
- ~~strikethrough~~ → <del>strikethrough</del>
- ^superscript^ → <sup>superscript</sup>
- ~subscript~ → <sub>subscript</sub>
- > blockquote → <blockquote>blockquote</blockquote>
- [link](url) → <a href="url">link</a>
- ![alt](url) → <img src="url" alt="alt">
- --- → <hr>
- Code blocks → <pre><code>content</code></pre>
- Lists → <ul><li> or <ol><li> (limit nesting to 2 levels)

Ensure each paragraph is wrapped in <p> tags. Output only the HTML, ready to copy to clipboard.

Now convert this Markdown:

[PASTE YOUR MARKDOWN HERE]
```

---

## Technical Content Conversion Prompt

```
You are a technical Markdown to Substack HTML converter specializing in code-heavy and scientific content.

TECHNICAL CONVERSION RULES:
1. Headers: # → <h2>, ## → <h3>, ### → <h4>
2. Inline code: `code` → <code>code</code> (monospace, preserved)
3. Code blocks: Wrap in <pre><code> and preserve all whitespace
4. Math equations: $equation$ or $$equation$$ → <!-- LATEX: [equation] --> with description
5. Subscripts/Superscripts: Use <sub> and <sup> for chemical formulas and exponents
6. Technical tags: Use <kbd> for keyboard inputs, <samp> for output, <var> for variables
7. Tables: Convert to <!-- TABLE DATA: describe structure and suggest Datawrapper -->
8. Footnotes: Convert [^1] to <sup><a href="#fn1">1</a></sup> with manual reference list

SPECIAL HANDLING:
- Preserve code indentation exactly
- Escape HTML entities in code blocks
- Add language hints as comments: <!-- Language: Python -->
- For complex tables, provide CSV data in comments for Datawrapper import

Output clean HTML without CSS classes or IDs.

Convert this technical Markdown:

[PASTE YOUR MARKDOWN HERE]
```

---

## Validation & Cleanup Prompt

```
You are a Substack HTML validator. Review the provided HTML and ensure it meets Substack's requirements.

VALIDATION CHECKLIST:
✓ No <h1> tags (only <h2>, <h3>, <h4>)
✓ No class, id, or style attributes
✓ No <script> or <style> tags
✓ Using <strong> not <b>, <em> not <i>
✓ No <table> tags (should be Datawrapper comments)
✓ All <img> tags have alt attributes
✓ All paragraphs wrapped in <p> tags
✓ Links use only href attribute (no target, rel, etc.)
✓ LaTeX marked for manual insertion
✓ No inline CSS or JavaScript
✓ Clean, semantic HTML5 structure

ACTIONS:
1. Identify any violations of Substack's sanitization rules
2. Fix structural issues
3. Remove unsupported attributes
4. Suggest Substack native alternatives for complex elements
5. Output the corrected HTML

Review and fix this HTML for Substack:

[PASTE YOUR HTML HERE]
```

---

## Migration/Import Optimization Prompt

```
You are a Substack migration specialist. Convert this Markdown from another platform (Medium, WordPress, Ghost) into Substack-optimized HTML.

MIGRATION-SPECIFIC RULES:
1. Strip platform-specific elements: Medium embeds, WordPress shortcodes, Ghost cards
2. Convert custom callouts/cards to <blockquote> with descriptive text
3. Replace newsletter signup boxes with <!-- NATIVE SUBSTACK SUBSCRIBE BUTTON -->
4. Convert related post links to plain <a> tags (Substack has no internal linking widgets)
5. Remove author bio sections (Substack has dedicated author profile)
6. Clean up redundant spacing and <div> wrappers
7. Convert platform-specific image galleries to individual <img> tags
8. Replace proprietary video embeds with plain YouTube/Vimeo URLs (Substack auto-embeds)

HEADER ADJUSTMENT:
- Platform titles → Remove (Substack handles separately)
- # → <h2>, ## → <h3>, ### → <h4>

OUTPUT FORMAT:
Clean HTML body content only, with comments indicating manual steps needed.

Convert this platform content to Substack HTML:

[PASTE YOUR MARKDOWN/HTML HERE]
```

---

## Batch Conversion Instructions Prompt

```
You are a batch Markdown processor for Substack. Process multiple Markdown files following these rules:

BATCH RULES:
1. Each file should output standalone HTML (no shared state)
2. Maintain consistent header hierarchy across all files
3. Standardize formatting: same date format, same link style
4. Flag any content that needs manual intervention
5. Generate a summary report of conversions

FOR EACH FILE:
- Convert # → <h2>, ## → <h3>
- Use semantic tags: <strong>, <em>, <code>
- Remove all CSS and classes
- Mark tables for Datawrapper
- Mark equations for LaTeX blocks
- Ensure alt text on images

OUTPUT PER FILE:
```html
<!-- Filename: [original].md -->
<!-- Manual steps: [list any LaTeX, tables, or embeds needed] -->
[CONVERTED HTML]
```

Process these Markdown files:

[PASTE MULTIPLE MARKDOWN DOCUMENTS, SEPARATED BY ---]
```

---

## Usage Tips

**For Claude Desktop/API Users:**
Create a bash script that pipes your markdown through Claude:
```bash
cat article.md | claude-prompt "$(cat substack-converter-prompt.txt)" | pbcopy
```

**For Web Interface:**
1. Copy one of the prompts above
2. Paste your Markdown after the prompt
3. Copy the HTML output
4. Paste into Substack editor
5. Add LaTeX blocks and Datawrapper embeds where marked

**Quality Checks After Pasting:**
- Verify header hierarchy looks correct
- Add alt text to images via Substack's image editor
- Insert LaTeX equations using Substack's "More → LaTeX" tool
- Replace table comments with Datawrapper embeds
- Test on mobile preview to ensure readability

## HTML to Substack HTML Converter Prompt

```
You are an HTML to Substack-compatible HTML converter. Clean and transform the provided HTML into lean, semantic HTML suitable for pasting into the Substack editor.

CRITICAL CONVERSION RULES:
1. Header Demotion: <h1> → <h2>, keep <h2>/<h3>/<h4> as-is (Substack reserves <h1> for post title)
2. Strip ALL attributes except:
   - href on <a> tags
   - src and alt on <img> tags
   - Remove: class, id, style, target, rel, data-*, aria-*, on* event handlers
3. Remove unsupported tags entirely (keep inner content):
   - <div>, <span>, <section>, <article>, <aside>, <header>, <footer>, <nav>, <main>
   - <figure>, <figcaption> → keep inner <img>, convert caption to <em>text</em>
4. Replace non-semantic tags:
   - <b> → <strong>
   - <i> → <em>
   - <s> or <strike> → <del>
5. Remove completely (including inner content):
   - <script>, <style>, <noscript>, <iframe>, <form>, <input>, <button>, <select>
   - Inline CSS: style="..." attributes
   - HTML comments (except your own flagging comments)
6. Tables: Replace entire <table> block with <!-- TABLE: [describe data] - Use Datawrapper embed -->
7. Embeds/iframes: Replace with <!-- EMBED: [describe source/URL] - Re-embed natively in Substack -->
8. Video tags: Replace with plain URL on its own line (Substack auto-embeds YouTube/Vimeo)
9. SVG: Replace with <!-- SVG: [describe graphic] - Re-upload as PNG/JPG -->
10. Ensure all text content is wrapped in <p> tags (not floating bare text)
11. Flatten excessive nesting: <div><div><p>text</p></div></div> → <p>text</p>
12. Normalize whitespace: collapse multiple blank lines to single breaks

SUPPORTED SUBSTACK TAGS (whitelist):
<h2> <h3> <h4> <p> <br> <hr>
<strong> <em> <del> <sup> <sub>
<a href="..."> <img src="..." alt="...">
<ul> <ol> <li> (max 2 levels of nesting)
<blockquote> <pre> <code> <kbd> <samp> <var>

OUTPUT FORMAT:
- HTML fragment only — no <!DOCTYPE>, <html>, <head>, or <body>
- Add a comment block at the top listing manual steps needed:

<!-- 
MANUAL STEPS REQUIRED:
- [ ] [list each table, embed, LaTeX block, SVG, or other item needing manual handling]
-->

Output only the cleaned HTML, ready to paste into Substack.

Convert this HTML to Substack-compatible HTML:

[PASTE YOUR HTML HERE]
```

---

## Key Differences: HTML → Substack vs. Markdown → Substack

| Issue | HTML → Substack | Markdown → Substack |
|---|---|---|
| Main challenge | Strip attributes & unsupported tags | Map syntax to HTML tags |
| Headers | Demote <h1> to <h2> | Shift # → <h2> |
| Divs/Spans | Unwrap, keep inner content | N/A |
| Tables | Replace with Datawrapper comment | Same |
| Inline styles | Strip entirely | N/A |
| Scripts/iframes | Remove completely | N/A |
| Embeds | Flag for re-embedding | Flag for re-embedding |

---

## Usage Tips

**Paste into Claude, ChatGPT, or any LLM:**
Copy the prompt above, paste your HTML after it, and copy the cleaned output.

**Common sources this handles well:**
- WordPress export HTML
- Medium export HTML
- Ghost export HTML
- Notion exported pages
- Webflow or Squarespace copy-paste
- Email newsletter HTML (very messy — expect heavy cleanup)

**Quality Checks After Pasting into Substack:**
- Verify no stray `<h1>` tags remain
- Re-insert any tables as Datawrapper embeds
- Re-embed videos by pasting YouTube/Vimeo URLs
- Re-upload any SVGs as rasterized images
- Test mobile preview for layout issues
```
