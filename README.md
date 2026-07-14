# Project OS

**Your AI project dies in week three, and you never see it coming.**

Not with a crash. With a session that ends five minutes early because you're tired, and a rule that quietly stops being enforced, and nobody notices — because the agent that would have noticed forgot everything the moment the chat closed.

Project OS is the scaffolding that makes long-horizon projects survive an agent with no memory. It's a Claude Code skill. It's free, it's MIT, and everything in it is machinery you can read in twenty minutes.

---

## The failure it exists to prevent

Here is a real one, dated, from this project's own files.

On 2026-07-14 I scaffolded a new project skill. Its single load-bearing constraint was a **2 hour/week cap on human time** — the whole thing was designed around that number. The scaffold stated the cap in **four separate files**.

It shipped with **zero mechanism to measure it.** No week boundary. No recording trigger. The one mode that asked "how many hours did you spend?" only fired after a sale — and the project had months of work before its first sale could possibly happen. A session six weeks later would have read "0 hours used," truthfully, while the human ground themselves into the floor.

I had self-certified those files as complete about an hour earlier.

A cold verifier — a fresh agent with no memory of writing them — found it in minutes.

**The rule that came out of it, which is now the spine of this whole system:**

> For every rule you write, name the mechanism that enforces it and the file where the evidence lands. **A rule with no trigger is a wish.** Stating a constraint three times in three files feels like rigor. It is the same wish, written thrice.

That is the entire disease. Your project doesn't die because you ran out of ideas. It dies because a rule stopped being enforced and the enforcement was never anywhere but in your head — and your head is not in the next session, and neither is the agent's.

---

## Why this keeps happening to everyone

I went looking for evidence that solo builders were shipping businesses with AI coding agents. Thirty days of data, pulled 2026-07-14:

**20 Reddit threads about Claude Code. 6,181 upvotes. 1,095 comments. Zero revenue screenshots.**

The top posts were a status light (3,508 points), a meme about what a Claude Code session feels like (1,244 points), and a poem.

That absence is the whole thing. Building is not the bottleneck anymore — the agents fixed that. **Finishing** is the bottleneck. People start extraordinary things and abandon them in silence, and there is no post about it, because nobody writes a thread called "I stopped opening my own project."

---

## What it actually does

Project OS turns a long-running goal into a managed project with files that survive the session. You run `/project-os`, answer four questions, and it generates a complete operating-system skill for your project.

**Files are the memory.** The agent is stateless. Your project cannot be.

| File | Job |
|---|---|
| `SKILL.md` | The session loop. Read state → propose 1-3 actions → execute by trust level → log. |
| `PLAN.md` | The approach, the rejected alternatives (so you stop re-litigating them), and the **kill criteria**. |
| `GOALS.md` | Targets with dates. Explicitly subordinate to the kill criteria. |
| `PROGRESS.md` | Dated session log + metrics. If it's not here, it didn't happen. |
| `LEARNINGS.md` | Every correction you gave the agent, verbatim, plus the rule that would have prevented it. |
| `PROBLEMS.md` | Evidence backlog. Nothing gets built without a row here. |
| `HANDOFF.md` | Lets a brand-new chat resume cold, six weeks later, with no context. |

And the four mechanisms that do the actual work:

- **Trust ladder.** The agent starts at `confirm-all` and asks before everything. Four clean sessions in a row → `auto-safe`. Any correction from you drops it a level. Autonomy is earned, never inherited from another project that's going well.
- **Kill criteria, written at genesis.** A number and a date, committed before anyone is emotionally attached. "Fewer than 25 stars by October 31 → this dies." Written on day one, when you can still be honest, because on day ninety you will not be.
- **Mandatory LEARN step.** Every session appends to `LEARNINGS.md` or the session is not finished. This rule is stated bluntly because it died of neglect once already and had to be resurrected.
- **Evolve mode.** The skill rewrites its own rules — but only from logged evidence, only inside guardrails, max three changes a pass, every change citing a specific learning, with rollback notes. The kill criteria and the trust rules are locked and it cannot touch them.

---

## Install

Requires [Claude Code](https://claude.com/claude-code).

```bash
git clone https://github.com/KhangYen/project-os.git ~/.claude/skills/project-os
```

Then, in any Claude Code session:

```
/project-os
```

It interviews you (name, goal, hours/week, money/month, what only *you* are allowed to do, and your honest kill condition), then writes a complete project skill into `~/.claude/skills/<your-project>/`.

Start the next session with `/<your-project>` and it picks up exactly where you stopped.

That's the whole install. No dependencies, no account, no server. It's markdown.

---

## What it is not

It is **not** a productivity system, and it will not make you do the work.

It is a set of tripwires. It notices that you said two hours a week and are on hour nine. It notices that the thing you swore you'd kill in October is still limping in December. It cannot make you honest — it can only make it *awkward to lie*, which turns out to be most of the battle.

It also will not tell you *what* to put in your kill criteria, or how to price your own hours, or which of the five ways these projects die is currently killing yours. That's judgment, and judgment doesn't fit in a template.

---

## The templates are free forever

Everything above is the machinery, and machinery gets copied — that is fine, that is what it's *for*. Take it, fork it, strip the attribution, use it for something I'd disapprove of. MIT.

What the templates can't give you is the part that hurts: **why** trust starts at confirm-all instead of somewhere useful, **what** actually belongs in a kill criterion versus what just sounds brave, and what a real evolve diff looks like when it's rolling back a change that quietly made things worse.

I'm writing that down separately, with the receipts — every claim tied to a dated entry from a real project, failures included. It'll be linked here when it exists. *(Coming: the Project OS Playbook.)*

If you only ever use the free files, that's a completely fine outcome. They're the good ones.

---

## Provenance

This isn't a hypothetical framework. It's the extracted pattern from three live projects being run this way right now, and the receipts are dated in their own logs — including the one at the top of this page, where the system caught its own author shipping a cap he couldn't measure.

It took **nine verification passes and eight refutations** to get a single one of these rules correct. Each fix was sincere, felt complete, and was wrong in a new place. The three rules that came out of that are the ones I'd hand you first:

1. **A rule fails at whatever layer you haven't checked yet.** Every fix moved the failure one layer outward.
2. **A summary of a rule is a second copy of that rule, and second copies rot.** The last surviving bug was a "helpful summary" of a rule in a file nobody thought to check, which had silently become the *old, refuted* version — and a cold session would have followed it, because it sat under a heading that said "do not skip."
3. **Grep for meaning, not for strings.** Three broken copies survived a search because they'd been reworded. If you're hunting a concept, enumerate its synonyms, or you will certify your own blind spot.

---

MIT License. Built with, and for, [Claude Code](https://claude.com/claude-code).
