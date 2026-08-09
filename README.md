# Bear Brown Tools

A collection of Agent Skills for writing, teaching, branding, music, and
software design. Each skill is a self-contained folder with a `SKILL.md` —
instructions plus a description that tells Claude when to use it.

These began life as claude.ai Projects, refined over several years of teaching
and consulting. They are personas with discipline: phase gates, pushback on
weak briefs, evidence rules, and honest output registers.

## Layout

```
skills/     ready to use — named by function, task-led descriptions
drafts/     converted but awaiting a reviewed description ("Use when …")
template/   starting point for a new skill
```

## Using a skill

**claude.ai / Cowork** — upload a skill folder via Settings → Skills (or zip
the folder and attach it).

**Claude Code** — copy a folder into `~/.claude/skills/`:

```bash
cp -R skills/brand-comms-audit ~/.claude/skills/
```

**Anywhere else** — `SKILL.md` is plain Markdown; paste the body as a system
prompt.

## Highlights

| Skill | What it does |
|---|---|
| `software-design-doc` | problem definition → ship-ready SDD, phase-gated |
| `ai-build-planner` | splits a build into AI-buildable vs human-only work |
| `brand-comms-audit` | touchpoint audit → evidence-traceable strategy memo |
| `peer-review` | eight-dimension manuscript review, full paper lifecycle |
| `game-design-doc` | senior-designer GDD consultant with scope pushback |
| `venture-pitch` | ten slides, eight minutes, jargon audited |
| `playlist-fraud-audit` | forensic streaming-fraud detection |
| `public-domain-song-research` | song origins, texts, singable respellings |
| `syllabus-architect` | outcomes-first syllabus design with alignment audits |
| `socratic-prompt-coach` | does your prompt teach, or think for the student? |

Tone packs (`tone-*`) provide writing registers for the shared writing skills — named for the register, inspirations credited inside (wonder, naturalist, scenic, spare, witness, aphoristic).

## Status

Skills in `drafts/` work but their descriptions haven't been reviewed for
automatic triggering — invoke them explicitly. A plugin marketplace manifest
will follow; the folder layout will not change when it does.

## License

MIT
