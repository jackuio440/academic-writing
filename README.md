# academic-writing

A Claude skill for writing, drafting, revising, and polishing academic manuscripts — including journal articles, theses, peer reviewer rebuttals, and abstracts.

Designed to:
- Apply discipline-appropriate section conventions (Introduction, Methods, Results, Discussion, Conclusion, Abstract, Captions, Rebuttal)
- Preserve the author's voice and confidence in revisions, rather than reflexively softening confident language
- Never fabricate statistics, citations, author names, or quantitative qualifiers the user did not state
- Handle bilingual workflows where the conversation language differs from the manuscript language
- Work across disciplines (medicine, biomedical sciences, social sciences, ecology, humanities, etc.)

## Installation

### Option 1: Install from the packaged `.skill` file (recommended)

1. Download `academic-writing.skill` from the [Releases](../../releases) page (or build it yourself — see below).
2. In Claude.ai, go to **Settings → Capabilities → Skills** and upload the `.skill` file.

### Option 2: Build from source

Clone this repo and package it yourself using Anthropic's `skill-creator`:

```bash
git clone https://github.com/<your-username>/academic-writing.git
cd academic-writing
# Then use skill-creator's package_skill.py to produce a .skill file
```

## Structure

```
academic-writing/
├── README.md
├── LICENSE
└── SKILL.md         # The skill definition (YAML frontmatter + instructions)
```

## How it works

The skill is a single `SKILL.md` file with YAML frontmatter declaring when it should trigger, followed by markdown instructions Claude reads when the skill is loaded. Six numbered steps cover task identification, section conventions, grounding rules, citation styles, revision-mode discipline, and output format.

Key behaviors:

| Behavior | What it means |
|---|---|
| **Grounding** | Never invents quantitative qualifiers ("more than five decades" when you only said "since the 1970s"). Uses `[INSERT VALUE]` and `[CITE]` placeholders. |
| **Voice preservation** | In revision mode, classifies each edit as Mechanical / Structural / Voice. Voice-altering edits are flagged in the Change Summary so you can revert. |
| **Bilingual handling** | Distinguishes conversation language from manuscript language; supports workflows like "discuss in Chinese, output English abstract." |
| **Editor's note discipline** | Only flags significant decisions (restructuring, scope-cutting, claim-softening, journal assumptions) — not routine style choices. |

## When the skill triggers

The skill triggers whenever you ask Claude to write, draft, revise, structure, or polish any section of an academic paper, journal article, or thesis — including responses to peer reviewers, reformatting to a target journal's style, or improving the academic tone of pasted text.

It does **not** trigger for slide decks, grant proposals, blog posts, or non-academic essays.

## Contributing

Issues and pull requests are welcome. If you have a use case that isn't well-handled (e.g., a section convention that's missing, a discipline whose norms differ), open an issue with an example prompt and the output you'd want.

## License

See [LICENSE](LICENSE).
