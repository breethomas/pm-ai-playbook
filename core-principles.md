# Core Principles for AI-Assisted Work

Universal principles for working with AI on sustained tasks — coding, strategy docs, pitches, analysis, or any work that spans multiple sessions.

---

## The Maturity Model

Where you are today determines what to focus on next.

### Level 1: Ad Hoc

**What it looks like:** No context. Every session starts cold. You re-explain who you are, what you're working on, and how you like things done. Quality varies wildly because the AI has nothing to build on.

**How to level up:**
- Create reference files: who you are, what you work on, who your people are
- Establish a session management practice (see below)
- Start saving work in small checkpoints instead of big batches

### Level 2: Planned

**What it looks like:** Reference files exist. The AI starts warm — it knows your role, your team, your priorities. Quality gates define "done." You have a repeatable process for starting and ending sessions.

**How to level up:**
- Add skills for your repeating workflows (meeting prep, inbox triage, backlog processing)
- Create reusable patterns from solved problems (see [patterns/](patterns/))
- Break work into phases with clear dependencies

### Level 3: Systematic

**What it looks like:** Skills define quality standards. The system knows your patterns — how you like specs written, how you prep for meetings, what your backlog processing looks like. You invoke workflows by describing what you need; the AI knows what good looks like for your context.

**How to level up:**
- Build evaluation criteria for AI output quality
- Let skills get leaner as the model proves it can handle the domain
- Dogfood your own workflows — use them daily, notice what breaks

### Level 4: Optimized

**What it looks like:** Your preferences are so well-captured that you steer and the system drives. It knows you — your communication style, your strategic framework, your quality bar. You focus on decisions and direction. The AI handles routine execution because the context architecture gives it everything it needs.

**The goal isn't to reach Level 4 on day one.** It's to know where you are and what the next step looks like. Higher levels mean the system needs less instruction from you, not more process around it.

---

## Principles

### 1. Context First

Before doing the work, establish context:
- **Reference files** — who you are, who your people are, what your domains look like
- **Preferences** — how you like things done, your quality bar, your communication style
- **Goals and priorities** — what matters right now, what you're working toward
- **Patterns to follow** — link to similar past work

Context files > trying to explain everything in chat. Reference files survive session restarts. Chat history doesn't. The AI doesn't need step-by-step instructions — it needs to understand your world.

### 2. Plan Big Work in Phases

For multi-session or multi-step work, create a punch list.

Structure by dependencies:
1. **Blockers first** — fix what prevents accurate progress
2. **Core work second** — the actual deliverable
3. **Polish third** — refinement, formatting, edge cases
4. **Verification last** — confirm everything holds together

Update the document as you work:
- Mark items complete with dates
- Add findings and decisions inline
- Create follow-up items for deferred work

A punch list keeps you focused and gives visibility into progress.

### 3. Checkpoint Frequently

Save after every meaningful unit of progress, not just when "done."

- Get one thing working -> save/commit
- Complete one section -> save/commit
- Fix one issue -> save/commit
- Do NOT wait until the entire deliverable is complete

**Why:** You always have a last known good state to return to. If something goes wrong, you revert one small change instead of losing hours of work.

### 4. Quality Gates Protect; Perfectionism Blocks

Shipping fast is good. Shipping sloppy work is not. But polishing forever is worse.

Quality gates catch catastrophic failure — broken builds, wrong data, embarrassing errors. They should be fast, focused checks, not comprehensive reviews that block iteration.

Before publishing, sending, or merging, ask:
- **Is this creating more work than it saves?**
- **Will this be easy to maintain or build on?**
- **Did I follow established patterns or force my own?**

If the answer to any is "no" — fix the critical issue and ship. Don't let perfect be the enemy of done.

### 5. Know When to Ask

You're not expected to know everything. Pause before:
- Creating new patterns when established ones exist
- Deviating from conventions
- Making decisions that affect others
- Shipping something you're not confident about

**It's better to ask than to create work for others cleaning up after you.**

### 6. The 6-Month Test

Ask: "If I had to modify this in 6 months with no memory of creating it, would I be annoyed?"

If yes — simplify, document intent, or restructure before shipping.

This applies to code, docs, processes, and project organization equally.

### 7. Clean Up Before Milestones

Before major deliverables (releases, submissions, publications), do a housekeeping pass.

**Remove:**
- Stale documentation that no longer reflects reality
- Artifacts from past debugging or exploration
- Abandoned experiments and dead drafts

**Keep:**
- The source of truth (current configs, active docs)
- Session notes and decision logs
- Active work in progress

The best time to clean up is before shipping, not after.

### 8. Keep It Lean

- Use straightforward approaches over clever ones
- Don't over-engineer for hypothetical future needs
- Remove what's unused — if removing it breaks nothing, it shouldn't be there
- Ask: "Do I really need this, or can I do it simply?"

### 9. Discover Before Building

Before adding something new, search for existing patterns.

This applies to code, docs, processes, and templates:

1. **Ask "how is this currently done?"**
2. **Search for existing patterns** — past work, templates, conventions
3. **Look at similar past work** — what's been done before?
4. **Check before creating** — don't duplicate what exists

**Red flags that you're about to duplicate:**
- Building a new template for something that already has one
- "I'll create a helper to..."
- Adding a new process when an existing one covers the case

### 10. Revisit with New Models

AI models improve fast. Step-by-step instructions that were necessary six months ago may be unnecessary today.

When a new model ships, check your skills:
- Can any procedural steps be removed because the model handles them natively?
- Are you compensating for limitations that no longer exist?
- Can a skill be expressed as "here's what good looks like" instead of "here's how to do it"?

Skills should get leaner over time, not fatter. The goal is to encode your judgment and preferences — not to write a manual for the AI.

---

## Session Management

Context rot is real. Auto-compaction fires at ~167,000 tokens, compressing everything into a lossy summary. The AI doesn't know it happened. Managing sessions is as important as managing the work itself.

### When to Restart

The trigger depends on the type of work:

**Coding sessions** -- restart after 2-3 major tasks. Coding sessions tend to be focused on a small number of files, so context pressure builds slowly.

**Strategic/research/writing sessions** -- restart after reading 10+ diverse sources or after 60+ minutes of deep work. These sessions read more files per task (transcripts, reference docs, prior drafts, Notion pages, Slack threads) and hit compaction faster than coding sessions with fewer completed "tasks."

**Any session** -- restart when you notice:
- AI suggesting approaches different from what you established
- Having to re-explain things covered earlier
- AI "forgetting" files it read recently (a sign compaction fired)
- Output quality dropping suddenly rather than gradually

### Before Restarting: Capture State

Create a session notes file with:

1. **Accomplished** — what got done
2. **Current state** — what's working, what's in progress
3. **What's next** — immediate steps, known issues
4. **Context for next session** — patterns established, decisions made, key info AI needs

### Where to Save

**Team projects:**
```
.claude/sessions/YYYY-MM-DD-feature-name.md
# or
docs/sessions/YYYY-MM-DD-your-name.md
```

**Solo projects:**
```
.claude/sessions/YYYY-MM-DD.md
# or
dev-log.md  # Append to running log
```

### Starting Fresh

1. **Load context** — point AI to session notes and project context files
2. **Verify understanding** — confirm AI knows where you left off
3. **Break down next task** — smaller tasks = better output

### Session Notes Template

```markdown
# [Date] - [What You Worked On]

## Done
- [Task 1]
- [Task 2]

## Current State
- [What's working]
- [What's in progress]

## Next
1. [Immediate task]
2. [Following task]

## Patterns / Decisions
- [Key decision and why]
- [Pattern established for future reference]

## Resume Prompt
[What to tell the AI to load context for the next session]
```

---

## Working with AI

### Your Role

The AI is your collaborator, but you're responsible for:
- **Directing the approach** — "Follow the pattern in X"
- **Verifying quality** — check output against standards
- **Making judgment calls** — "Is this good enough or should I refine?"

The AI helps you execute. You ensure the output is responsible.

### Task Breakdown

**The smaller the task, the better the output.**

Break work into focused chunks:
- **Bad:** "Write the quarterly strategy update"
- **Good:** "Draft the Top 3 section for the exec update, following last week's format"

Each task should be completable in one focused session.

### Context Files Over Chat

Structure what the AI needs to know in files, not conversation:
- **Project context** — what the AI needs to know about this work
- **Patterns to follow** — link to similar past work
- **Decisions made** — why you're taking this approach

Files persist across sessions. Chat history doesn't.

---

*These principles apply to any sustained AI-assisted work. For coding-specific standards, see [coding/](coding/).*
