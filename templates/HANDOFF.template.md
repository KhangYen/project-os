# HANDOFF - resume {{PROJECT_NAME}} in any new chat

Written: {{DATE}}. Read top to bottom, continue as if the previous conversation never ended.

## How to resume

1. User style: {{USER_STYLE_NOTES}}.
2. Read state files here: PLAN.md, GOALS.md, PROGRESS.md (top 3 entries), LEARNINGS.md.{{IF_RESEARCH}} RESEARCH-LOG.md before any research.{{/IF_RESEARCH}}
3. Trust: see top of PROGRESS.md. Locked, do NOT re-litigate: {{LOCKED_DECISIONS}}.
4. {{IF_FLEET}}Fleet: sibling skills at {{SIBLING_PATHS}}; retros shared ({{RETRO_CADENCE}}).{{/IF_FLEET}}

## The project in one breath

{{ONE_BREATH}}

## Where we are right now

{{CURRENT_STATE}}

**Next session queue:**
1. {{QUEUE_1}}
2. {{QUEUE_2}}

## Where everything lives

- This skill: `~/.claude/skills/{{KEBAB_NAME}}/`
- {{OTHER_LOCATIONS}}

## How the user resumes

Any of these in a new chat: `/{{KEBAB_NAME}}` · "{{TRIGGER_PHRASE_1}}" · "Read ~/.claude/skills/{{KEBAB_NAME}}/HANDOFF.md and continue".

## Maintenance rule

Session ends mid-task → update "Where we are right now" first. Every session owes a LEARNINGS.md entry (LEARN step){{IF_RESEARCH}}, research owes RESEARCH-LOG.md{{/IF_RESEARCH}}, applied skill changes owe SKILL-CHANGELOG.md.
