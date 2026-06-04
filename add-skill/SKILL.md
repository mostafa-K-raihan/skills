---
name: add-skill
description: Design and create a new agent skill through grilling, save it to ~/.claude/skills/, then publish it to the shared skills repo at github.com/mostafa-K-raihan/skills. Use when user says "add skill", "create skill", "new skill", "build a skill", or invokes /add-skill.
---

## Goal
Design a new agent skill through grilling, write it to `~/.claude/skills/{name}/SKILL.md`, then publish to the shared skills repo so it's available across all agents and machines.

## Steps

### 1. Get the raw idea
If not provided in args, ask: "What should this skill do? One sentence."

### 2. Grill the design
Invoke the `/grill-me` skill. Resolve these branches one question at a time:
- **Trigger** — what exact phrases / invocations should activate this skill?
- **Input** — what does the skill need from the user? (URL, file, free text, nothing?)
- **Output** — what does it produce? (file, message, side effect, git push?)
- **Steps** — what is the high-level sequence of actions?
- **Dependencies** — does it call other skills? use external tools (yt-dlp, gh, git)?
- **Saved artifacts** — where does output go? which paths?
- **Edge cases** — what can go wrong? what should it do when input is missing?

Do NOT skip grilling. The SKILL.md quality depends on it.

### 3. Write the skill
Create `~/.claude/skills/{name}/SKILL.md` using this structure:

```markdown
---
name: {kebab-case-name}
description: {one-line description — used by agent to decide when to invoke}
---

## Goal
{What this skill accomplishes in 1-2 sentences}

## Steps

### 1. {Step name}
{instructions}

### 2. {Step name}
{instructions}

...
```

### 4. Confirm with user
Show the skill summary and ask: "Ready to publish to the shared skills repo?"

Do NOT proceed to publish without explicit confirmation.

### 5. Publish to shared repo
Once confirmed:

```bash
# Copy skill into the shared skills repo
cp -r ~/.claude/skills/{name} ~/.claude/skills/../  # already there

# Stage, commit, push
cd ~/.claude/skills
git add {name}/
git commit -m "feat: add skill {name}"
git push
```

Then update `README.md` in the skills repo — append a new row to the index table:
```markdown
| [{name}](./{name}/SKILL.md) | {one-line description} |
```

Commit and push the README update:
```bash
git add README.md
git commit -m "docs: add {name} to skills index"
git push
```

### 6. Confirm
Tell user:
- Skill live at `~/.claude/skills/{name}/SKILL.md`
- Published to `https://github.com/mostafa-K-raihan/skills`
- Available in all Claude Code sessions immediately (no restart needed)
