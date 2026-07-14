---
name: project-os
description: Use when the user invokes /project-os, wants to create a new self-improving project skill, says "scaffold a skill for X", "new project operating system", "make a skill like the passive-income one for X", or wants to turn any long-running goal (income stream, study plan, habit, business experiment) into a managed project with state files and session loops.
metadata:
  provenance: self-improving-skills

---
# Project OS - scaffold a self-improving project operating system

## Overview

Generates a complete operating-system skill for any long-running project, from the battle-tested pattern behind `passive-income` and `income-tools`: state files as memory, session loop, trust ladder, mandatory learning capture, self-improvement mode with guardrails, kill criteria, and a handoff file so any new chat resumes cold.

Templates live in `templates/` next to this file. Never point a new project at the templates directly - always copy-and-fill into a new skill directory.

## The pattern in one breath

Files are the memory (sessions are stateless). The loop reads state → proposes few actions → executes by trust level → logs everything. Trust is earned (confirm-all → auto-safe → auto-full), corrections drop it. Every session owes a learning. Every 2 weeks a retro checks targets against written kill criteria so the project cannot become a zombie. The skill edits its own rules only from logged evidence, inside guardrails, with rollback notes.

## Scaffold flow (follow in order)

1. **Interview** (AskUserQuestion, one round, max 4 questions). Collect:
   - Project name + one-sentence goal ("one breath")
   - Human budget (hrs/week) and money budget ($/month)
   - What only the HUMAN may do (publish/pay/send/post equivalents - the outward-facing acts)
   - Success target + honest kill condition ("if X by DATE, we pivot/stop")
   Derive yourself (confirm only if odd): retro cadence (default every 2 weeks), whether the project needs research memory (RESEARCH-LOG only if the project does recurring external research), first 3 goals with dates.

2. **Create** `~/.claude/skills/<kebab-name>/` and fill from `templates/`: SKILL.md, PLAN.md, GOALS.md, PROGRESS.md, LEARNINGS.md, SKILL-CHANGELOG.md, HANDOFF.md (+ RESEARCH-LOG.md if research applies). Replace every `{{PLACEHOLDER}}`; delete optional blocks that don't apply. No placeholder may survive - grep for `{{` before finishing.

3. **Wire the fleet**: if the user runs sibling project skills, add a fleet note to each sibling's HANDOFF.md (shared retro dates if cadences align). Add/update the auto-memory index entry so future chats recall the project exists.

4. **Genesis log**: first SKILL-CHANGELOG.md entry (what was scaffolded, why, rollback = delete directory). First PROGRESS.md entry with the next-session queue. Trust starts at confirm-all, always - new projects earn autonomy, never inherit it.

5. **Verify before ending**: read the generated SKILL.md as if you were a cold new session - can you run a full session loop from it alone? If any step needs knowledge not in the files, fix the files, not the explanation.

## Hard rules for every generated skill

- **Problem-first (user doctrine, 2026-07-09):** if the project builds or sells anything, generate a PROBLEMS.md evidence backlog and the rule "no solution gets built unless it traces to an evidence-backed problem row (real threads/upvotes/own logged pain)". Find real problem → solve with AI → automate. Cleverness without evidence parks unbuilt.
- Trust starts confirm-all. AUTO_PUBLISH (or domain equivalent) starts false.
- **Every state field needs a step that writes it.** A field is not a mechanism; a field plus a trigger is. Before finishing, take each field the generated skill *reads* (trust level, clean-session counter, human-minutes, any budget or cap) and name the loop step that *updates* it. If you cannot name one, the field is decoration and the rule behind it is a wish - add the trigger or cut the field. This is not hypothetical: the trust counter shipped with a slot and no writer, so the ladder could never move off `confirm-all` and `auto-safe` was unreachable by construction. It read as complete because the field was *there*.
- LEARN step is mandatory and non-negotiable in the generated loop - a session without a LEARNINGS entry is not finished (this rule died of neglect once; it stays explicit).
- Kill criteria must be concrete (number + date), written at genesis while nobody is emotionally attached.
- Evolve guardrails: locked decisions/kill criteria/trust rules untouchable, max 3 changes per pass, every change cites a logged learning, rollback notes always.
- Outward-facing actions (the HUMAN list from the interview) never automate without an explicit user flip recorded in PLAN.md.

## Red Flags

- Skipping the interview and guessing constraints → the kill criteria will be fiction.
- Leaving `{{PLACEHOLDER}}` text in generated files.
- Copying a sibling skill's trust level or clean-session streak into a new project.
- Generating extra modes/files "for later" - scaffold only what the project needs on day one; evolve adds the rest from evidence.
