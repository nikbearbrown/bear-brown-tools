---
name: suno-portuguese
description: "Suno Use when — NEEDS TRIGGER."
---
# SUNO PORTUGUESE PHONETIC CONVERSION
## Master Prompt Set for Native-Sounding Portuguese Vocals

---

## MASTER SYSTEM PROMPT (paste into Suno style box or prepend to any LLM conversion request)

```
You are a Portuguese phonetic engineer specializing in Suno AI vocal optimization.
Your job is to transform standard Portuguese lyrics into a Suno-optimized phonetic script
that forces the model to render authentic Portuguese phonology — eliminating American,
English, and Brazilian drift when targeting European Portuguese.

You do NOT change the meaning of lyrics. You change ONLY the spelling and structure
so Suno's generative engine maps the text to correct Portuguese audio tokens.

Output format: phonetic version (display version in parentheses after each line).
```

---

## PROMPT 1 — FULL LYRIC CONVERSION (General Portuguese)

**Use when**: You have a complete lyric sheet and want a clean phonetic transformation.

```
Convert the following Portuguese lyrics to Suno-optimized phonetic script.

Apply ALL of these rules without exception:

NASAL VOWELS:
- "ão" → "SAWN-g" (e.g., coração → co-rah-SAWN-g)
- "ões" → "OYN-sh"
- "ão" at line endings → "ah-oon" (softer close, e.g., pão → Pah-oon)
- "em" / "ém" → "ay-ing" (e.g., também → tam-BAY-ing)
- "om" / "oom" → "o-ong" (e.g., bom → bo-ong)
- "im" / "im" → "see-n" (e.g., sim → see-n)
- "um" → "oon"

PALATAL CONSONANTS:
- "lh" → "ly" before a, o, u / "li" before e, i (e.g., trabalho → tra-BAH-lyo)
- "nh" → "ny" universally (e.g., amanhã → ah-mah-NYAH)

SIBILANTS (European Portuguese targets):
- Terminal "s" → "sh" (e.g., nós → no-sh)
- "s" before voiced consonant → "zh"
- "z" at word end → "sh" (e.g., faz → fah-sh)
- "x" → "sh" (e.g., peixe → PAY-shee)

STRESS:
- Capitalize the TONIC syllable of every word over 2 syllables
- Do NOT capitalize the first letter of a line unless it is the tonic syllable
- Use accented vowels (ó, ê, á) even where not orthographically required, to lock vowel quality

PACING:
- Insert hyphens between syllables of any word with a consonant cluster (e.g., saudade → SAU-da-de)
- Split any line exceeding 10 syllables into two with a line break

OUTPUT FORMAT:
Line 1 phonetic
(Line 1 original)

Line 2 phonetic
(Line 2 original)
[continue for all lines]

LYRICS TO CONVERT:
[PASTE LYRICS HERE]
```

---

## PROMPT 2 — EUROPEAN PORTUGUESE (PT-EU) SPECIALIST CONVERSION

**Use when**: Target is Lisbon/Iberian accent specifically. Adds dialect anchoring on top of Prompt 1.

```
Convert the following lyrics to Suno-optimized phonetic script targeting
EUROPEAN PORTUGUESE (PT-EU) — Lisbon dialect. The model defaults to Brazilian;
you must aggressively counteract this.

ADDITIONAL PT-EU RULES (apply on top of standard nasal/palatal rules):

VOWEL REDUCTION (Lisbon dialect characteristic):
- Unstressed "e" at word start → reduce to near-silent schwa: write as "-"
  (e.g., estar → sh-TAR, esperar → sh-peh-RAR)
- Unstressed "o" word-internally → reduce: "u" quality (e.g., bonito → boo-NEE-too)

CONSONANT SHARPENING:
- All terminal "s" → "sh" mandatory
- "de" before vowel → "dj" (e.g., cidade → see-DAH-djee)
- "te" terminal → "tch" (e.g., morte → MOR-tch)
- Double "r" or initial "r" → hard guttural: write "rr" (e.g., rio → RREE-oo)

STYLE BOX ANCHORS (paste these into Suno's style field alongside your genre tags):
"European Portuguese, Lisbon accent, Portugal, Iberian diction, not Brazilian,
not American, no PT-BR, authentic Fado phrasing"

NEGATIVE PROMPTS (paste into Suno's negative prompt field):
"Brazilian Portuguese, American accent, English phonology, PT-BR, Anglicized,
samba, bossa nova inflection"

LYRICS TO CONVERT:
[PASTE LYRICS HERE]
```

---

## PROMPT 3 — SINGLE WORD / LINE REPAIR

**Use when**: One specific word keeps mispronouncing across regenerations. Surgical fix.

```
I am using Suno AI to generate Portuguese vocals. The following word/line
is mispronouncing. Give me 3 alternative Suno-optimized phonetic spellings,
ranked from most to least aggressive intervention.

For each option provide:
- The phonetic spelling
- Which specific Suno failure it targets (nasality / palatalization / stress / sibilant)
- A one-line rationale

MISPRONOUNCING WORD OR LINE:
[PASTE HERE]

INTENDED SOUND (describe or provide IPA if known):
[DESCRIBE THE SOUND YOU WANT]

DIALECT TARGET: [ ] European PT  [ ] Brazilian PT  [ ] Universal
```

---

## PROMPT 4 — WAVEFORM PATCH GENERATOR

**Use when**: Track is mostly correct but 2–4 words need surgical overwrite in Suno's waveform editor.

```
I have a Suno-generated Portuguese track that is mostly correct. I need
phonetic patch strings for ONLY the following mispronounced segments,
formatted for pasting directly into Suno's waveform editor overwrite field.

Rules for patch strings:
- Maximum 6 characters if possible (editor window is narrow)
- Use CAPS for the stressed syllable only
- Prefer English-looking approximations that trigger correct audio tokens
- No IPA — Latin script only

SEGMENTS TO PATCH:
1. [word] at timestamp [X:XX] — sounds like [describe error]
2. [word] at timestamp [X:XX] — sounds like [describe error]

DIALECT: [PT-EU / PT-BR / Universal]
```

---

## PROMPT 5 — FULL SONG PIPELINE (Dirty → Clean Sheet)

**Use when**: Building a track from scratch using the Dirty/Clean lyric strategy.

```
I am producing a Portuguese song in Suno using the Dirty Lyric Sheet method.
I need TWO versions of my lyrics:

VERSION A — "DIRTY" PHONETIC SHEET (for Suno input)
Apply full phonetic transformation: nasal decomposition, palatal substitution,
stress capitalization, sibilant replacement, syllable hyphenation.
This version will NEVER be shown publicly. It is for AI ears only.

VERSION B — "CLEAN" DISPLAY SHEET (for public lyrics display)
Standard correct Portuguese orthography. Grammatically clean. Accent marks correct.
This is restored AFTER final remaster. Do not phonetically alter anything.

FORMAT:
[SECTION TAG e.g., Verse 1] (Portuguese)
VERSION A:
[phonetic lines]

VERSION B:
[clean lines]

[repeat for all sections]

DIALECT TARGET: [PT-EU / PT-BR]
GENRE CONTEXT: [e.g., Fado, Pop, Hip-Hop — affects pacing rules]

LYRICS:
[PASTE FULL SONG LYRICS HERE]
```

---

## PROMPT 6 — STYLE BOX TEMPLATE GENERATOR

**Use when**: You need to build the Suno style prompt + negative prompt for a Portuguese track.

```
Generate a Suno style box entry and negative prompt for a Portuguese vocal track.

Inputs:
- Dialect: [PT-EU / PT-BR / Universal]
- Genre: [e.g., Fado, Funk Carioca, MPB, Pop, R&B]
- Vocal character: [e.g., male baritone, female soprano, saudade, passionate]
- Reference artists (optional): [e.g., Amália Rodrigues, Tim Maia, Ana Moura]

Output format:
STYLE BOX (max 120 characters):
[generated style string]

NEGATIVE PROMPT (max 80 characters):
[generated negative string]

SECTION LANGUAGE TAG (paste before each lyric section in brackets):
[generated tag]
```

---

## QUICK REFERENCE: THE 10 MOST COMMON SUNO PORTUGUESE ERRORS

| Error | What Suno Does | Phonetic Fix |
|---|---|---|
| ão | Flat "ow" | SAWN-g |
| lh | Hard "l" + "h" | ly / li |
| nh | Hard "n" + "h" | ny |
| também | "tam-bem" | tam-BAY-ing |
| Terminal s (PT-EU) | "z" or dental s | sh |
| saudade | Rushed cluster | SAU-da-de |
| Unstressed first syllable | Capitalized/stressed | lowercase start |
| Nasal om | English "om" | o-ong |
| faz / vez | "faz" English | fah-sh / veh-sh |
| r initial | Soft English r | rr (double) |
