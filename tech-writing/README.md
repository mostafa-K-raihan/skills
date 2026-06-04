# Tech Writing

[![skills.sh](https://skills.sh/b/peizh/tech-writing)](https://skills.sh/peizh/tech-writing)

An agent skill for drafting, rewriting, reviewing, and structuring technical content.

It helps an agent write clear, concise, reader-first documentation, README files, design docs, API docs, tutorials, onboarding guides, release notes, specs, comments, CLI help, and support content.

## Install

List the skill without installing:

```bash
npx skills add peizh/tech-writing --list
```

Install and let the CLI pick the detected agent:

```bash
npx skills add peizh/tech-writing --skill tech-writing
```

Install globally for the detected agent without prompts:

```bash
npx skills add peizh/tech-writing --skill tech-writing -g -y
```

Install for a specific agent:

```bash
# Codex
npx skills add peizh/tech-writing --skill tech-writing -a codex

# Claude Code
npx skills add peizh/tech-writing --skill tech-writing -a claude-code

# Cursor
npx skills add peizh/tech-writing --skill tech-writing -a cursor

# Windsurf
npx skills add peizh/tech-writing --skill tech-writing -a windsurf

# GitHub Copilot
npx skills add peizh/tech-writing --skill tech-writing -a github-copilot

# Gemini CLI
npx skills add peizh/tech-writing --skill tech-writing -a gemini-cli

# OpenCode
npx skills add peizh/tech-writing --skill tech-writing -a opencode
```

Install for multiple agents:

```bash
npx skills add peizh/tech-writing --skill tech-writing --agent codex claude-code cursor
```

Install globally for all agents supported by the CLI:

```bash
npx skills add peizh/tech-writing --skill tech-writing --agent '*' -g -y
```

## Use

Example prompts:

```text
Use $tech-writing to rewrite this README for clarity and scanning.
```

```text
Use $tech-writing to review this API doc and identify missing prerequisites, unclear terms, and weak examples.
```

The skill is most useful when:

- documentation is correct but hard to scan
- a design doc, tutorial, README, or spec needs clearer structure
- API or CLI reference content needs consistent terms and exact commands
- error messages should explain the failure and recovery path
- technical content needs to be condensed, expanded, reviewed, or rewritten without changing facts

## Structure

```text
.
├── SKILL.md
├── references/
│   └── chinese-technical-prose.md
└── agents/
    └── openai.yaml
```

`SKILL.md` contains the core workflow, review checklist, rewrite heuristics, response modes, and style guardrails. `references/chinese-technical-prose.md` adds focused guidance for Chinese evidence-first prose, narrator-style filler removal, and buzzword cleanup. `agents/openai.yaml` provides optional OpenAI/Codex UI metadata.

## Notes

This skill is an original workflow artifact inspired by common technical writing practice. It does not include or redistribute third-party course text, examples, or copyrighted source material.

See [NOTICE.md](NOTICE.md) for attribution and copyright boundaries.
