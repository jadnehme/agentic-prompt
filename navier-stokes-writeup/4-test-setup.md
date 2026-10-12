# Test setup

How the materials were gathered and the paper reviewer was run, so the test can be reproduced.

## Materials

| Item | Version used |
| --- | --- |
| Paper | "Finite time blowup for Navier–Stokes" by OpenAI, the original 165-page PDF (generated 2026-09-08, archived 17:29 UTC). The live link now serves a 166-page revision. |
| Announcement | The earliest [web.archive.org](https://web.archive.org/) capture of [openai.com/index/navier-stokes-solution](https://openai.com/index/navier-stokes-solution/), 2026-09-08 17:15 UTC, saved as plain text |
| Lean code | [`openai/NavierStokesAndEuler`](https://github.com/openai/NavierStokesAndEuler) at commit `f9e8bc5`, the version the critique examined, downloaded as a source archive (no clone, so no later commit messages) |

These aren't included here because they aren't mine to republish.

## Gathering prompt

Run in a separate session from the reviewer.

```text
Create a local folder called ns-review and put the sources below in it. This is for a review exercise, so collect only what's listed: no notes, summaries, commentary or extra files.

1. Lean code: download the source archive for commit f9e8bc5 of openai/NavierStokesAndEuler (github.com/openai/NavierStokesAndEuler/archive/f9e8bc5.zip) and unzip it into ns-review/lean/. Don't clone, don't download dependencies such as Mathlib, and don't install Lean or build anything.
2. Announcement: OpenAI's post at https://openai.com/index/navier-stokes-solution/, as first published: use the earliest snapshot on web.archive.org, not the live page. Download the page itself and save its text verbatim to ns-review/announcement.txt, including the title, headings, captions and footnotes. Don't use a tool that summarizes or rewrites pages.
3. Paper: OpenAI's paper "Finite time blowup for Navier–Stokes," as linked from that snapshot, saved as ns-review/paper.pdf. If the link now serves a revised version, find the original from around September 8, 2026.

Don't search for or download anything else about this work, including reviews, critiques or news coverage.

When done, report:
- a file count and total size for each folder
- the commit you downloaded, its date, and how you confirmed it's f9e8bc5
- the dates of the announcement snapshot and the paper version, and where you got each
- anything you couldn't get, and why

Don't summarize or comment on the contents.
```

## Checks before running

1. **The issue is present.** The paper's Lemma 8.6, equation (8.19), states the bound with m+4 derivatives, and its proof says "four more derivatives." In `NavierStokes/SmoothFamilyTorusInverse.lean`, `norm_derivativeWord_inverse_le` (around line 1059) has hypotheses with `w.length + 5`.
2. **Nothing gives it away.** Search the folder for the critics' names and "mistranslation": there should be no results. Check for hidden files, notes or a leftover `CLAUDE.md`.
3. **A clean session.** Move the folder away from any project folder whose `CLAUDE.md` mentions this work. Start the reviewer session inside it, and check with `/context` that nothing about this work is loaded.
4. **No internet.** Deny WebSearch and WebFetch in `/permissions`. An instruction alone doesn't block a tool call.

## Running it

Follow the steps in [`3-paper-reviewer.md`](3-paper-reviewer.md). Optionally, run `/cost` after each step and `/export` at the end to keep the reports.
