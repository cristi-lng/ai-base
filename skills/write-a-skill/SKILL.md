---
name: ai-base-write-a-skill
description: Create new skills or edit existing ones. Use when the user wants to create, write, author, or build a new skill, or edit, update, revise, fix, or improve an existing skill (SKILL.md).
---

# Writing Skills

## Instructions

Do NOT write or modify any skill files until you know which flow applies and have the inputs that flow requires.

Route by intent:

- Creating a new skill → follow **Creating a skill**.
- Editing an existing skill → follow **Editing a skill**.

## Creating a skill

Do NOT create the skill in a global or shared location unless the user asks — default to the current project. Follow these steps in order:

1. **Gather requirements.** Do NOT proceed until you know: the task/domain and its specific use cases; whether executable scripts are needed or just instructions; any reference materials to include.
2. **Decide structure.** Default to a single `SKILL.md`. Estimate up front whether the content will stay small, and split per **Reference › Structure** as it approaches ~100 lines. Do NOT add extra files or scripts unless a threshold there is met.
3. **Write the description.** Apply **Reference › Description**. This is the highest-leverage part — a vague description means the skill never triggers.
4. **Write the instructions.** Apply **Reference › Rules** before phrasing anything.
5. **Review.** Run the **Review checklist** with the user.

## Editing a skill

1. **Read first.** Read the existing `SKILL.md` and every file it links before changing anything, so you preserve its structure and terminology.
2. **Stay in scope.** Change only what the request requires. Do NOT rewrite or restructure sections the request does not touch. Do NOT rename the skill or move its files unless asked.
3. **Route by change type** and apply only that Reference section:
   - Description change → **Reference › Description**.
   - Rule or content change → **Reference › Rules**.
   - Size or file-layout change → re-check thresholds in **Reference › Structure**.
4. **Re-validate.** If the edit changed length, confirm `SKILL.md` stays near ~100 lines. If it added a link, confirm links stay one level deep (no reference file linking to another reference file).
5. **Review.** Run the **Review checklist** with the user.

## Reference

### Structure

```
skill-name/
├── SKILL.md           # Main instructions (required)
├── REFERENCE.md       # Detailed docs (only if SKILL.md would exceed ~100 lines)
├── EXAMPLES.md        # Usage examples (only if needed)
└── scripts/           # Utility scripts (only if needed)
```

- Split into a reference file only when `SKILL.md` would exceed ~100 lines, content spans distinct domains, or advanced features are rarely needed.
- Add a script only when the operation is deterministic (validation, formatting), the same code would otherwise be regenerated repeatedly, or errors need explicit handling.
- Do NOT let a reference file link to another reference file (keep links one level deep).

### Description

- Max 1024 chars. First sentence = what it does. Second sentence = "Use when [trigger phrases the user would actually say: keywords, contexts, file types]".
- Good: `Extract text and tables from PDF files. Use when the user needs to pull text or tables out of a PDF.`
- Bad: `Helps with documents.` — gives the agent no way to distinguish it from other skills.

### Rules

- First read `./writing-rules-research.md`; it governs how to phrase every rule.
- Do NOT fill the skill with generic best-practices the model already knows; prioritize domain-specific context it can't guess about this project or task.
- Prefer negative constraints ("Do not X") over positive directives ("Do X").
- Prefer state-dependent rules ("If X, then Y") over state-independent ones ("always X").
- Do NOT include vague directives like "follow code style" or "handle edge cases" — they measurably hurt.
- Do NOT pad instructions with rationale, background, or restated context; keep them to the actionable minimum.
- Do NOT include time-sensitive information. Keep terminology consistent throughout.

Use this shape:

```md
---
name: skill-name
description: Brief description. Use when [specific triggers].
---

# Skill Name

## Instructions

[Rules and steps, phrased as constraints]

## Reference

[Examples, or link to separate files: See REFERENCE.md]
```

## Review checklist

Present the draft or diff to the user and verify only the items the work touched:

- [ ] Description states what it does + "Use when..." triggers
- [ ] `SKILL.md` stays near ~100 lines
- [ ] Rules follow `./writing-rules-research.md` (negative, state-dependent constraints)
- [ ] Concrete examples included; no time-sensitive info; consistent terminology
- [ ] Links stay one level deep

Ask: does this cover your use cases? Anything missing or unclear? Apply the user's feedback before finishing.
