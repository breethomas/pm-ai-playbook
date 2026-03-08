# Skill Definition: PM AI Playbook

Auto-trigger configuration for Bette OS and Claude Code skill systems.

---

## Trigger

This skill should activate when:
- Claude detects coding work (file edits to source code, PR creation, test runs)
- User explicitly starts a coding session
- User references coding guardrails, quality gates, or pre-commit checks

This skill should NOT activate when:
- Operational work (email, Slack, calendar, meeting prep)
- Strategy and planning (docs, pitches, roadmaps) — core-principles.md covers these via project CLAUDE.md, not the skill
- Quick file edits (updating a markdown file, fixing a typo)

## What to Load

**Always (on trigger):**
- `core-principles.md` — universal principles, maturity model, session management

**For coding sessions:**
- `coding/quality-gates.md` — pre-commit checklist, PM-who-codes role clarity
- `coding/test-first.md` — AI-generated test suites before modifying code

**When relevant:**
- `coding/solo-projects.md` — when working on a solo project (no team codebase)
- `coding/prompt-engineering.md` — when modifying AI prompts
- `patterns/` — when project has captured patterns

## Integration

### Claude Code Global CLAUDE.md

```markdown
## Coding Standards

At the start of any coding session, load the PM AI Playbook:
- Read core-principles.md for universal working principles
- Read coding/quality-gates.md for pre-commit standards
- Read coding/test-first.md for the test-first pattern
- Check patterns/ for project-specific solved patterns
```

### Bette OS Skill File

```yaml
name: bette-work
description: Quality gates, session management, and maturity model for AI-assisted work
trigger:
  - file_edit: "*.{ts,tsx,js,jsx,py,rb,rs,go}"
  - command: "/coding-guardrails"
  - natural_language:
    - "coding session"
    - "start coding"
    - "quality gates"
    - "pre-commit"
context:
  always:
    - core-principles.md
    - coding/quality-gates.md
    - coding/test-first.md
  conditional:
    - file: coding/solo-projects.md
      when: "no team CLAUDE.md detected"
    - file: coding/prompt-engineering.md
      when: "editing prompt files"
    - directory: patterns/
      when: "patterns directory has content"
```

---

*This file defines how the playbook integrates with AI operating systems. It is not loaded directly — it's configuration.*
