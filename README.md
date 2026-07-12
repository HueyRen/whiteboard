# whiteboard

A Claude Code skill for **whiteboard-style product design interviews** — practice mode for drilling the format, and a live executor mode for real interviews.

Turns a live design conversation into a structured 8-step whiteboard (`template.html`) plus generated wireframes, or coaches you through the same 8 steps as a solo practice partner.

## What it does

- **Practice mode** — give it a prompt (or let it pick one from the practice bank), and it walks you through Why → Who → Context → Assumptions → Ideation → Flow → Solution → Summary, one step at a time, catching blind spots and modeling what to say out loud.
- **Live executor mode** — during an actual interview, feed it your meeting transcript and it fills in a shareable HTML whiteboard in real time, plus auto-generates lo-fi/hi-fi wireframes.
- **Reference library** — `SKILL.md` pulls in a `references/` folder on demand (8-step framework, problem-type taxonomy, scoring rubric, red-flag checklist, ASCII wireframe component guide). That folder isn't included in this repo — see below.

## Install

Copy this repo into your Claude Code skills directory:

```bash
git clone https://github.com/HueyRen/whiteboard.git ~/.claude/skills/wb
```

Then invoke it in Claude Code as `/wb`.

**Note:** `SKILL.md` reads from a local `references/` folder (framework guide, problem types, scoring rubric, interviewer strategies, practice bank, wireframe components) that isn't published in this repo. Quick-reference commands (`types`, `redflags`, `signals`, `components`, `interviewer`, `coach`) and practice mode won't have content to pull from until you add your own `references/*.md` files matching the names `SKILL.md` expects.

## How sessions work

The root `template.html` is a **pristine, blank template** — it is never edited in place. Every practice run or real interview creates its own folder:

```
sessions/
  2026-07-12-pet-adoption/
    template.html      # copy of the root template, filled in as you go
    Meeting.md          # live transcript for this session
    company-notes.md    # optional — interviewer/company context you add yourself
    pet-adoption-lofi/  # generated wireframes
```

`sessions/` is gitignored — your real interview transcripts, company notes, and generated wireframes stay local and never get committed.

## Commands

| Command | What it does |
|---|---|
| `/wb [prompt]` | Start a new practice/interview session |
| `/wb s1` … `/wb s8` | Fill or coach one step of the framework |
| `/wb lofi` / `/wb prototype` | Generate wireframes from the current session |
| `/wb review` | Self-review against the scoring rubric |
| `/wb coach [step]` | Deep-dive coaching on one step |
| `/wb types` / `redflags` / `signals` / `time` / `components` / `interviewer` | Quick-reference cards |

See [SKILL.md](SKILL.md) for the full behavior spec.

## Structure

```
SKILL.md          # the skill definition Claude Code reads
template.html     # blank whiteboard template — copied per session, never edited directly
references/       # NOT published here (gitignored) — supply your own, see Install
sessions/          # gitignored — your local practice/interview runs live here
```
