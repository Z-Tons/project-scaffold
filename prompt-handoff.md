<!--
HOW TO USE THIS FILE
1. Start a new Claude session.
2. Attach: (a) the project scaffold .zip, and (b) your project idea write-up
   (as a file, OR pasted into the "PROJECT IDEA" section at the bottom of this file).
3. Paste this entire file as your first message.
That's it — Claude will inspect the scaffold, read your idea, and fill it in.
-->

# Project Kickoff — Bootstrap My Scaffold From My Idea

You are helping me start a **multi-CLI, spec-driven coding project**. I run it with
multiple AI coding tools (e.g. Codex + Claude Code, possibly GSD on top). I've attached:

1. **A project scaffold (.zip)** — an opinionated folder structure with planning docs,
   tool config, a skills folder, and an `external/` area for vendored repos.
2. **My project idea** — either an attached write-up or pasted in the PROJECT IDEA
   section at the bottom of this message.

## Step 1 — Inspect the scaffold (do this first, before anything else)
- Extract the zip and produce a short inventory of the folder tree.
- **Read these files fully so you understand the conventions before writing anything:**
  `AGENTS.md`, `README.md`, `00-planning/handoff.md`, `00-planning/vision.md`,
  `00-planning/requirements.md`, `00-planning/design.md`, `00-planning/roadmap.md`,
  `00-planning/tasks.md`, `skills/README.md`, `external/README.md`,
  `external/GSD-INTEGRATION.md`, and `.codex/config.toml`.
- Then tell me, in ~5 bullets, what you understand about how this project is meant to
  be run (the source-of-truth model, the handoff log, the multi-CLI rules, skills,
  external repos). This confirms you "see" the scaffold correctly before you touch it.

## Step 2 — Read my idea and ask only what's blocking
- Read my project idea (attached file or the section below).
- Ask me a **short** round of clarifying questions — only the ones you genuinely need to
  fill the scaffold well. Cover at minimum, if my write-up doesn't already say:
  - Tech stack (language, framework, storage, hosting, package manager).
  - The single most important thing v1 must do (the "walking skeleton").
  - What's explicitly OUT of scope for now.
  - **GSD-led or docs-led?** (Who owns the spec/plan/task cycle — GSD, or the
    `00-planning/` docs — so we don't keep two systems of record.)
  - Which CLIs I'll actually use.
- Keep it to one focused batch of questions. Don't proceed past this until I answer
  (unless my write-up already answers everything, in which case state your assumptions
  and continue).

## Step 3 — Populate the scaffold
Using my idea + answers, fill in the placeholders/TODOs. Specifically:
- **`AGENTS.md`** §1 (what we're building), §2 (tech stack), §6 (commands), §7 (don't touch).
  This is the single source of truth — get it right; everything else points here.
- **`00-planning/vision.md`** — one-liner, problem, who it's for, success signals, non-goals.
- **`00-planning/requirements.md`** — must-haves for v1, nice-to-haves, constraints.
- **`00-planning/design.md`** — architecture sketch, key components, data model, open questions.
- **`00-planning/roadmap.md`** — Phase 1 walking skeleton → Phase 2 → Phase 3.
- **`00-planning/tasks.md`** — a concrete "Doing now / Up next" list to start Phase 1.
- **`01-features/`** — create the first feature folder by copying `_template/` and specing it.
- **`00-planning/handoff.md`** — set CURRENT STATE for the next agent (active task, next step).
- **`02-notes/decisions/`** — record the GSD-led-vs-docs-led decision (copy the ADR template).
- **`CHANGELOG.md`** — add a "project initialized" line.
- If GSD-led, note in `external/GSD-INTEGRATION.md` / a decision file how GSD and the
  `00-planning/` docs divide responsibility.

## Rules (from the scaffold — follow them while filling it in)
- **`AGENTS.md` is the source of truth.** Don't put rules in `CLAUDE.md`/`.codex`/`.cursorrules`
  that contradict it — those files only point back to `AGENTS.md`.
- **Don't write application code yet.** This step is planning only. Leave `src/`, `tests/`
  empty except their READMEs unless I ask.
- **Don't edit `external/`** contents — that's vendored.
- Keep everything as plain markdown (it must stay Obsidian-readable and CLI-readable).
- Don't invent scope. Where my idea is silent and it's not blocking, make a reasonable
  assumption and **mark it clearly** so I can correct it.

## Step 4 — Deliver
- Re-zip the populated scaffold and give it back to me as a download.
- Give me a short "what I filled in / what I assumed / what's still open" summary.
- End with the exact first 1–3 commands or actions to start Phase 1 in my chosen CLI.

---

## PROJECT IDEA
<!-- Paste your write-up here, OR delete this section and attach it as a file. -->

(your project idea goes here)
