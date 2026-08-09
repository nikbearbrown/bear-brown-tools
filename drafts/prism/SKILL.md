---
name: prism
description: "A structured prompt library and methodology for getting production-ready output from Figma AI and the MCP Server. Use when — NEEDS TRIGGER."
---
# PRISM — Figma AI Prompt Reference
*A structured prompt library and methodology for getting production-ready output from Figma AI and the MCP Server.*

---

## WHAT THIS IS

Figma's AI tools generate native, editable layers from text input. That input box is not a search bar. Treated like one, it produces generic wireframes that require significant cleanup. Treated like a design brief, it produces structured, system-aligned layouts that are close to shippable.

This guide gives you the prompt blocks, frameworks, and workflows to get the second kind of output — consistently.

---

## THE CORE RULE

**The AI infers everything you don't specify.** Its defaults are: desktop, light mode, placeholder copy, no edge states, happy path only, disconnected from your design system. Every piece of information you withhold becomes a guess the model makes on your behalf.

A high-context prompt is not more work. It is insurance against rework.

---

## THE TOKEN FRAMEWORK — Pre-Flight Checklist

Before writing any prompt, run through these five vectors. If you cannot answer a vector, your prompt is incomplete.

| Vector | What It Defines | You Must Specify |
|---|---|---|
| **T** — Task | The explicit objective | What are you generating or modifying? |
| **O** — Output | The expected visual state | Fidelity level? Copy quality? How many screens? |
| **K** — Key Elements | Required UI components | What must appear on the canvas? |
| **E** — Expected Behaviors | Interactions and states | What happens on tap, error, or load? |
| **N** — Notable Constraints | Technical and brand limits | Platform? Accessibility standard? Design system? |

A prompt that clears all five vectors will produce a structurally predictable result. A prompt that skips two or more will produce a structurally unpredictable one.

---

## PROMPT BLOCKS — COPY AND PASTE DIRECTLY

The blocks below are complete, production-ready prompts. Paste them as-is, or edit the bracketed fields for your context.

---

### BLOCK 1 — Mobile Onboarding Flow

```
Task: Design a 3-screen mobile onboarding flow for a [fintech / wellness / productivity] app.
Output: High-fidelity wireframes with realistic copy. No lorem ipsum.
Key Elements:
  - Screen 1: Welcome — hero illustration, headline, subhead, primary CTA
  - Screen 2: Value proposition — 3 feature cards with icons, secondary CTA
  - Screen 3: Account setup — email input, password input, terms checkbox, submit button
  - Persistent: Horizontal progress bar at the top of all screens
Expected Behaviors:
  - Tapping the primary CTA advances to the next screen
  - Progress bar fills incrementally across screens
  - Submit button is disabled until all fields are valid
Constraints: iOS styling. Generous padding. WCAG AA contrast. No absolute positioning.
```

---

### BLOCK 2 — Dashboard with Data States

```
Task: Design a personal finance dashboard in mobile view.
Output: High-fidelity layout with 3 frame states: loaded, loading, and empty.
Key Elements:
  - Summary cards: "Income" (green accent) and "Expenses" (red accent)
  - Toggleable line chart for 30/90/365-day trends
  - Recent transactions list (5 rows minimum)
  - Floating action button: "+ Add Transaction"
Expected Behaviors:
  - Loading state: skeleton placeholders for cards and chart
  - Empty state: illustration with "No transactions yet" and a prompt to add the first one
  - Error state: alert banner with retry button
Constraints: Minimalist layout. 16px border radius. White space dominant. Match [Brand] design tokens.
```

---

### BLOCK 3 — Sign-In Screen with Edge States

```
Task: Design a sign-in screen for a [SaaS / mobile / enterprise] product.
Output: High-fidelity. Include 4 states in separate frames: default, loading, error, success.
Key Elements:
  - Email input field with label and placeholder
  - Password input with show/hide toggle
  - "Forgot password?" link
  - Primary "Sign In" button
  - Social sign-in option (Google, Apple)
Expected Behaviors:
  - Loading state: spinner inside the button, fields disabled
  - Error state: inline field error below the email input reading "No account found for this email"
  - Success state: checkmark animation, brief confirmation message
Constraints: Use components from /UI-Library/Core. Pull active primary buttons and text inputs from system symbols only.
```

---

### BLOCK 4 — Settings Screen

```
Task: Design a settings screen for a [mobile app name].
Output: Scrollable single-screen layout. Realistic copy throughout.
Key Elements:
  - Section: Account — avatar, name, email, "Edit Profile" link
  - Section: Notifications — toggle rows for email, push, and SMS
  - Section: Security — "Change Password" and "Two-Factor Authentication" rows with chevrons
  - Section: Danger Zone — "Delete Account" in red, with a destructive action confirmation modal
Expected Behaviors:
  - Toggle rows change state on tap
  - "Delete Account" opens a modal requiring confirmation text input before enabling the delete button
Constraints: iOS list-style layout. No custom illustrations. System icons only.
```

---

### BLOCK 5 — Component Generation (Single Element)

```
Task: Generate a notification toast component in 4 variants: info, success, warning, error.
Output: Component set. Each variant uses the same base structure with semantic color and icon differences.
Key Elements:
  - Icon (left-aligned, variant-specific)
  - Title (bold, 1 line)
  - Body text (regular weight, 2 lines max)
  - Dismiss button (X, top-right)
Expected Behaviors:
  - Component is designed to slide in from the top of the viewport
  - Dismiss button removes the toast on tap
Constraints: 12px border radius. Drop shadow. Use brand color tokens if available. No inline hex values.
```

---

## STAGED PROMPTING — FOR COMPLEX SCREENS

Running one large prompt for a multi-section, multi-state screen increases the chance of truncated output and disconnected components. Use this sequence instead.

**Run in three separate prompt inputs:**

**Step 1 — Structure first**
```
Generate the structural wireframe only for [screen name]. Establish the grid, container placement, and section breaks. No components, no copy. Placeholder boxes only.
```

**Step 2 — Component population**
```
Populate the wireframe with components from /UI-Library/Core. Replace placeholder boxes with the correct system components: [list specific components]. Apply realistic copy. No lorem ipsum.
```

**Step 3 — Interactions and states**
```
Add interaction behaviors to the populated layout. Link [button name] to [target screen]. Add a loading state, an empty state, and an error state for [dynamic element name]. Use separate frames for each state.
```

---

## EDGE STATES — ALWAYS DEFINE EXPLICITLY

Figma AI defaults to the happy path. It will not generate loading, empty, or error states unless you ask. Leaving these out guarantees manual rework.

**Template — add to any prompt:**

```
Explicitly include three frame states for [dynamic element]:
1. Loading — skeleton placeholder or spinner
2. Empty — illustration or icon with a short prompt message
3. Error — alert banner with an error message and a retry or refresh action
```

---

## DESIGN SYSTEM ALIGNMENT — PREVENT UNLINKED LAYERS

When Figma AI generates components from scratch, they are not connected to your library. Use this language to force system alignment:

```
Use components from /UI-Library/Core. Pull primary buttons, input fields, and card containers directly from system symbols. Do not generate new component styles.
```

If you have specific token names, name them explicitly:

```
Apply color tokens: Primary-500 for CTA backgrounds, Neutral-900 for body text, Semantic-Error for destructive actions. Do not use inline hex values.
```

---

## ITERATION — HOW TO PROMPT AFTER THE FIRST DRAFT

Figma AI accepts follow-up prompts as long as you have not made a manual edit. The moment you drag, resize, or type directly on the canvas, that element is locked from AI modification.

**Safe iteration prompts:**

```
Increase the spacing between sections to 48px. Keep all components intact.
```

```
Swap the color scheme to dark mode. Maintain all layout proportions.
```

```
Replace all placeholder copy with copy appropriate for a [healthcare / legal / consumer] product. Maintain tone: [professional / conversational / urgent].
```

```
Add a secondary CTA below the primary button. Label it "Learn more." Style it as a ghost button.
```

**What breaks the link:**
Manually resizing a frame, editing text directly on canvas, dragging a component to a new position. After any manual edit, use traditional editing to continue — iterative prompting no longer applies to that element.

---

## MCP SERVER — PROMPTS FOR IDE INTEGRATION

When working via Claude Code, Cursor, or VS Code with the Figma MCP server connected, use these agent prompts.

**Read a design and generate code:**

```
Use get_design_context on [Figma node URL] to read the component structure. Use get_screenshot to capture its visual state. Generate production-ready React + Tailwind code that matches the design. Do not use inline styles. Map all colors to the token file at /tokens/colors.ts.
```

**Build a screen from the design system:**

```
Search the /UI-Library/Core library for the following components: [list]. Instantiate them on a new frame at [position]. Apply the text overrides from the attached copy document. Do not create new component styles.
```

**Create a Code Connect mapping file:**

```
Use get_code_connect_suggestions on [component node URL]. Generate a .figma.ts mapping file that binds the Figma component variants to the codebase component at /components/[ComponentName]. Map all variant props, boolean properties, and slot triggers.
```

**Create a new blank file:**

```
Use whoami to resolve my plan key. Create a new Figma Design file in drafts titled "[Project Name] — [Date]". Return the file_key.
```

---

## VALIDATION CHECKLIST — BEFORE MARKING AS COMPLETE

AI output is visually plausible, not engineering-precise. Run this check before handoff.

| Category | What to Verify | Fix |
|---|---|---|
| **Layout** | Auto-Layout applied everywhere. No absolute positioning. | Stretch parent frames to confirm responsive scaling. |
| **Components** | All elements are library instances, not unlinked layers. | Run "Select Same" to find disconnected elements. Swap with library components. |
| **Edge States** | Loading, empty, and error states exist for every dynamic element. | Design missing states manually. |
| **Accessibility** | Contrast passes WCAG AA. Images have alt text. Interactive elements have labels. | Run contrast check. Write ARIA attributes for custom elements. |
| **Copy** | No lorem ipsum. Copy matches brand tone. | Use Figma's copywriting tool to refine tone and line breaks. |
| **Design System** | No inline hex values. All colors reference tokens. | Find/replace hex values with token references. |

---

## COMMAND REFERENCE

| What You Need | Prompt Strategy |
|---|---|
| New screen from scratch | TOKEN framework block — all five vectors |
| Multi-screen flow | Staged prompting — structure → components → interactions |
| Edge states | Explicit edge state template appended to any block |
| Design system alignment | Library reference language + token names |
| Iterate on AI output | Follow-up prompt — before any manual edit |
| Code from a design | MCP: get_design_context + get_screenshot |
| Build on canvas from IDE | MCP: library search + use_figma instantiation |
| New blank file | MCP: whoami + create_new_file |

---

*The AI resolves ambiguity by defaulting to generic. Every parameter you name is a decision you keep.*
