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
- **Record the answers.** Once I've replied, save what was decided (and why) in
  `02-notes/decisions/0002-project-kickoff-answers.md` before populating anything else.
  The next agent sees the populated files but not this chat — the answers are durable
  context worth keeping.

## Step 3 — Populate the scaffold

### 3a — Preserve every substantial chat artifact in the repo first
**Do this before filling in any planning docs.** The chat is ephemeral; the repo is not.
Anything produced in our conversation that the project needs forever must land in the
repo now — before the chat ends. If our conversation has produced any of the following,
copy them into the scaffold in the folders GSD does not touch:

- **Long-form plans, strategy docs, research write-ups, architectural deep-dives** →
  `02-notes/research/<descriptive-name>.md`.
  Then create or update `02-notes/research/README.md` to index them: one line per file,
  what it is, and when to read it.

- **Working prototype code or proofs-of-concept that have been run and verified** →
  `external/_reference/prototypes/<name>/`.
  Include any rendered proof artifacts (screenshots, sample outputs). Add a `README.md`
  inside that folder explaining what it is, what was proven, and the porting plan into
  `src/` for the relevant phase. (These are vendored per `AGENTS.md §7` — untouchable,
  but explicitly referenced.)

- **Reusable patterns, framework references, or exemplar templates** (e.g. skill
  framework docs, plugin interface specs, prompt patterns, exemplar `SKILL.md` files) →
  framework doc in `02-notes/research/<name>.md`; example files in
  `external/_reference/prototypes/<name>-exemplars/` with a README.

- **Architectural decisions with rationale** → write or expand the relevant ADR in
  `02-notes/decisions/`. ADRs must include the *reasoning and tradeoffs*, not just
  the decision text. "We chose X" is incomplete; "We chose X over Y because Z, tradeoff
  is W" is a durable ADR.

Then **update `AGENTS.md` §3** to list these as named durable-context anchors with their
exact paths. GSD may rewrite `AGENTS.md`, but when it does, these anchors survive in the
files themselves — and a well-seeded §3 gives the next agent (or a GSD rewrite) a map to
find them. Example entry for §3:

```
### Durable-context anchors (GSD-safe locations)
- `02-notes/research/execution-strategy.md` — master project strategy + pipeline design
- `02-notes/research/skill-framework.md` — skill authoring patterns + exemplars
- `external/_reference/prototypes/poc-v1/` — verified proof-of-concept code + port plan
- `02-notes/decisions/` — all load-bearing architectural decisions with rationale
```

### 3b — Fill in the planning docs
Using my idea + answers, fill in the placeholders/TODOs. Specifically:
- **`AGENTS.md`** §1 (what we're building), §2 (tech stack), §3 (durable-context anchors
  per 3a above), §6 (commands), §7 (don't touch).
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
- **Don't edit `external/`** contents — that's vendored. Exception: you MAY create new
  folders under `external/_reference/prototypes/` in Step 3a to preserve chat artifacts;
  that's adding, not editing existing vendored content.
- Keep everything as plain markdown (it must stay Obsidian-readable and CLI-readable).
- Don't invent scope. Where my idea is silent and it's not blocking, make a reasonable
  assumption and **mark it clearly** so I can correct it.

## Step 4 — Deliver
- Re-zip the populated scaffold and give it back to me as a download.
- Give me a short "what I filled in / what I assumed / what's still open" summary.
- End with the exact first 1–3 commands or actions to start Phase 1 in my chosen CLI.
- **Sanity check before zipping — does the repo contain the full plan?** If a future
  agent opened this scaffold cold with no chat history, could they reconstruct *why* every
  major decision was made and *what* was already built? Verify each of the following; if
  any answer is "no," go back and fix it before delivering:
  - Is there a master long-form plan or strategy doc in `02-notes/research/`, indexed by
    a `README.md`?
  - Are working prototypes or verified PoC code preserved in
    `external/_reference/prototypes/` with a port plan?
  - Do ADRs in `02-notes/decisions/` include reasoning and tradeoffs per decision, not
    just the decision assertion?
  - Does `AGENTS.md` §3 explicitly name these durable-context anchors by path?
  - Is `02-notes/decisions/0002-project-kickoff-answers.md` present with the key
    decisions from Step 2?

---

## PROJECT IDEA
<!-- Paste your write-up here, OR delete this section and attach it as a file. -->

(your project idea goes here)
