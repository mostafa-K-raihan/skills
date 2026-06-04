---
name: capture-idea
description: Capture and refine a new idea through grilling, then save a structured detail doc to ~/playground/pensieve/ideas/{name}/index.md. Use when user says "add idea", "capture idea", "log this idea", "save this idea", or invokes /capture-idea.
---

## Goal
Turn a raw idea into a refined, actionable document via grilling, then log it to the Pensieve knowledge base.

## Structure
Each idea lives in its own folder:
```
~/playground/pensieve/
  INDEX.md               ← master map of all ideas
  {name}/
    index.md             ← full idea detail doc
```

## Steps

### 1. Get the raw idea
If not provided in args, ask: "What's the idea? One sentence."

### 2. Grill the idea
Invoke the `/grill-me` skill with the idea as input. Run the full grilling loop — ask one question at a time, provide a recommended answer, resolve each decision branch until you have:
- Clear problem statement
- Target audience / user
- Core value proposition
- Key open questions resolved
- Rough shape of the solution

Do NOT skip grilling. This is the core step.

### 3. Create idea folder and detail doc
After grilling, create `~/playground/pensieve/ideas/{name}/index.md`:

```markdown
---
name: {kebab-case-slug}
status: idea
created: {YYYY-MM-DD}
tags: [{relevant tags}]
---

# {Idea Title}

## Problem
{What problem does this solve? Who has it?}

## Solution
{What is the idea, concisely?}

## Why Now
{What makes this worth doing / timely?}

## Target Audience
{Who is this for?}

## Key Decisions Made
- {decision}: {rationale}
- ...

## Open Questions
- [ ] {unresolved question}
- ...

## Next Steps
- [ ] {first concrete action}
- ...

## Notes
{Anything else from the grilling session worth preserving}
```

### 4. Update INDEX.md
Append a row to `~/playground/pensieve/INDEX.md`:
```
| idea | [{name}](./{name}/index.md) | {tags} |
```

### 5. Commit and push
```bash
cd ~/playground/pensieve
git add .
git commit -m "feat: capture idea {name}"
git push
```

### 6. Confirm
Tell user:
- Detail doc at `~/playground/pensieve/ideas/{name}/index.md`
- Logged in `INDEX.md`
- Pushed to https://github.com/mostafa-K-raihan/Pensieve
- "Start your next session from this doc — it has everything you need to continue."
