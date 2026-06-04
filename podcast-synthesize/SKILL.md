---
name: podcast-synthesize
description: Synthesize a podcast episode from a YouTube URL into structured markdown. Fetches transcript, extracts key claims/frameworks/examples, saves to ~/playground/pensieve/podcasts/{topic}/. Use when user shares a YouTube link and wants it synthesized, or says "synthesize this podcast", "process this episode", "add to knowledge base".
---

## Goal
Turn a YouTube podcast episode into a structured research doc saved to the podcasts knowledge base at `~/playground/podcasts/`.

## Steps

### 1. Get inputs
Ask user for:
- YouTube URL (if not already provided)
- Topic/category for this episode (e.g. `software-engineering`, `leadership`, `life`) — create folder on-demand

### 2. Fetch transcript
Use `yt-dlp` to download auto-generated or manual subtitles:
```bash
yt-dlp --write-auto-sub --sub-lang en --skip-download --output "/tmp/podcast_transcript" "{URL}"
```
Then read the `.vtt` or `.srt` file from `/tmp/`. If yt-dlp unavailable, ask user to paste transcript or use `youtube_transcript_api` via Python.

Alternative via Python if yt-dlp fails:
```bash
pip install youtube-transcript-api -q
python3 -c "
from youtube_transcript_api import YouTubeTranscriptApi
import sys, json
vid = sys.argv[1].split('v=')[-1].split('&')[0]
t = YouTubeTranscriptApi.get_transcript(vid)
for s in t: print(f'[{int(s[\"start\"]//60):02d}:{int(s[\"start\"]%60):02d}] {s[\"text\"]}')
" "{URL}"
```

### 3. Extract metadata
From the transcript and YouTube page, extract:
- Episode title
- Podcast/channel name
- Guest name(s) if any
- Approximate duration

### 4. Synthesize into template
Produce a markdown doc following this exact template:

```markdown
---
title: "{Episode Title}"
source: "{Podcast/Channel Name}"
url: "{YouTube URL}"
date: "{YYYY-MM-DD}"
topic: "{topic}"
guests: ["{Guest Name}"]
tags: ["{topic}", "{additional tags}"]
---

# {Episode Title}

**Source:** {Podcast Name} | **Guest:** {Guest} | **Date:** {Date}

## Core Thesis
{1-2 sentence summary of the episode's central argument}

## Key Claims
- [MM:SS] {claim}
- [MM:SS] {claim}
...

## Mental Models & Frameworks
- **{Framework Name}**: {brief description and how to apply it}
...

## Real Examples Mentioned
- {example}: {context}
...

## Quotable Moments
> "{exact quote}" — {speaker} [MM:SS]

## My Take
{Critical assessment — what holds up, what's missing, what's debatable}

## Research Threads
- [ ] {thing to dig deeper on}
- [ ] {related concept to explore}
...

## Related Notes
- [[{related episode slug}]]
```

### 5. Save file
- Slug = lowercase episode title, spaces → hyphens, remove special chars
- Path: `~/playground/pensieve/podcasts/{topic}/{slug}.md`
- Create topic folder if it doesn't exist

```bash
mkdir -p ~/playground/podcasts/{topic}
```

### 6. Update INDEX.md
Append entry to `~/playground/pensieve/INDEX.md`:
```markdown
| {Date} | [{Title}](./{topic}/{slug}.md) | {source} | {tags} |
```

If INDEX.md doesn't exist, create it with header:
```markdown
# Podcast Knowledge Base Index

| Date | Episode | Source | Tags |
|------|---------|--------|------|
```

### 7. Confirm
Tell user: file saved at path, INDEX.md updated, suggest `git add . && git commit`.
