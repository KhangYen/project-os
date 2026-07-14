---
name: {{KEBAB_NAME}}
description: Use when the user invokes /{{KEBAB_NAME}}, says "{{TRIGGER_PHRASE_1}}", "{{TRIGGER_PHRASE_2}}", or asks about {{PROJECT_TOPIC}} progress, goals, or what to do next on it.
---

# {{PROJECT_NAME}} - Operating System

## Overview

{{ONE_BREATH}}

State files here: PLAN.md (strategy + kill criteria), GOALS.md (targets + review dates), PROGRESS.md (session log + metrics + trust), LEARNINGS.md (what worked/failed + heuristics), SKILL-CHANGELOG.md (applied skill changes + rollbacks){{IF_RESEARCH}}, RESEARCH-LOG.md (research memory + SPENT register){{/IF_RESEARCH}}.

**Core principle:** every session ends with PROGRESS.md updated and at most 1-3 actions moved forward. Human budget: {{HUMAN_BUDGET}}. Money budget: {{MONEY_BUDGET}}.

## Session Loop (mode: work - default)

1. **Read state**: PLAN.md, GOALS.md, PROGRESS.md (last 3 entries), LEARNINGS.md.{{IF_RESEARCH}} Before any research: RESEARCH-LOG.md (avoid spent finds and dead query shapes).{{/IF_RESEARCH}}
2. **Locate phase** in PLAN.md; if a GOALS.md review date has passed, run `retro` mode first.
3. **Propose 1-3 highest-leverage actions**, each labeled CLAUDE (I execute) / HUMAN ({{HUMAN_ONLY_ACTS}}) / PAIR. Respect the human budget.
4. **Check trust level** (top of PROGRESS.md): confirm-all → AskUserQuestion before executing anything; auto-safe → execute CLAUDE-labeled work without asking, confirm the rest; auto-full → confirm only HUMAN tasks and anything irreversible or outward-facing.
5. **Execute** CLAUDE actions. Never {{OUTWARD_VERBS}} - those stay HUMAN until {{AUTOPILOT_FLAG}} is explicitly flipped in PLAN.md.
6. **Update PROGRESS.md**: dated entry - done, results, metrics, blockers, next actions.
7. **LEARN (mandatory, before ending)**: append to LEARNINGS.md under today's date: (a) every user correction verbatim + the rule that would have prevented it; (b) one thing that worked; (c) one thing to do differently. A session that wrote nothing to LEARNINGS.md is not finished.{{IF_RESEARCH}} Research runs also log to RESEARCH-LOG.md.{{/IF_RESEARCH}}
8. **Update the trust counter (same edit, non-optional).** The two lines at the top of PROGRESS.md are the entire record of trust, and **this step is the only thing that writes them.** Skip it and the ladder is decoration: the counter reads 0 forever, `auto-safe` is unreachable, and the project asks permission for everything until you stop using it.
   - **If the user corrected you this session** → **drop `Trust level:` one rung** (`auto-full` → `auto-safe` → `confirm-all`; already at `confirm-all` → it stays) **and set `Clean sessions in a row: 0`.**
     *What counts as a correction:* whatever you just wrote into LEARNINGS.md line (a). If you logged a correction there, it counts here. Not your opinion of whether it was fair, not whether you'd already spotted it - **the log decides, not you**, because the whole point is that the judge and the judged are the same agent.
   - **If there were zero corrections** → **increment `Clean sessions in a row:` by 1.** When it reaches **4** and the level is `confirm-all`, promote to `auto-safe` and reset the counter to 0.
   - **`auto-full` is never reached this way.** It requires an explicit grant from the user, in words. You may not infer one from a good streak.
   - Trust is per-project. Never copy a level or a streak from another project, however well that one is going.

## Other Modes

- **status**: report phase, metrics vs GOALS.md, pending HUMAN tasks. No execution.
- **retro** (every {{RETRO_CADENCE}}, dates in GOALS.md): actuals vs targets; check PLAN.md kill criteria honestly - if triggered, say plainly it is failing and propose the pivot; verdict to PROGRESS.md; lessons to LEARNINGS.md.
- **learn**: after each {{UNIT_OF_OUTPUT}}, record {{KEY_METRICS}} + human-minutes in PROGRESS.md metrics and the LEARNINGS.md table. Once 3+ rows exist, propose exactly one testable heuristic per pass; mark existing ones hypothesis / confirmed / killed. One experiment per {{UNIT_OF_OUTPUT}}, never more.
- **evolve** (at every retro): read LEARNINGS.md{{IF_RESEARCH}} + RESEARCH-LOG.md{{/IF_RESEARCH}} since last pass → propose numbered diffs to this SKILL.md / templates / tactics, each citing the specific logged learning → apply per trust level (confirm-all: only user-approved; auto-safe: tactic diffs may auto-apply, SKILL.md edits still confirmed) → log applied changes to SKILL-CHANGELOG.md with rollback notes. Include a tooling scan: max 2 skill/plugin/MCP proposals with effort-saved estimates; installs always HUMAN-approved.

## Evolve Guardrails

EVOLVE may never change: locked decisions ({{LOCKED_DECISIONS}}), kill criteria, trust rules, {{AUTOPILOT_FLAG}}, or anything with legal/money consequences - those need explicit human sign-off outside evolve. Max 3 applied changes per pass. Every change cites a logged learning. Metric-worsening changes roll back at the next retro, logged as killed experiments.

## Trust Ladder

`confirm-all` → `auto-safe` after 4 consecutive zero-correction sessions → `auto-full` only by explicit user grant. Any correction drops one level.

**Where it lives:** the two lines at the top of PROGRESS.md. **What moves it:** loop step 8, and nothing else. Read it at step 4, write it at step 8. If you are ever unsure what the current level is, the file is right and your memory is wrong.

## Red Flags

- Session ends without PROGRESS.md + LEARNINGS.md entries → not finished; write them.
- **Session ends without touching the trust counter (loop step 8) → not finished.** A counter that never moves means the ladder was never real. If it has read the same number for weeks while sessions have happened, that is the bug, not a coincidence.
- **Logging a correction in LEARNINGS.md and then not dropping the trust level.** These are the same event written in two files; if they disagree, you are grading your own homework.
- Proposing 5+ actions → too many for the budget.
- Skipping a due retro because "things are going fine".
- {{OUTWARD_VERBS}} without HUMAN sign-off while {{AUTOPILOT_FLAG}}=false.
- Reporting metrics from memory instead of reading the files.
{{EXTRA_RED_FLAGS}}
