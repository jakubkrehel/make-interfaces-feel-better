# AGENTS.md

This file provides guidance to Codex (Codex.ai/code) when working with code in this repository.

## What this repository is

A standalone agent skill for reviewing and improving interface polish, published for installation via `npx skills add jakubkrehel/make-interfaces-feel-better`. It is documentation-only; there is no build, lint, or test tooling.

## Structure

The skill lives in `skills/make-interfaces-feel-better/`:

- `SKILL.md` is the entry point. Its YAML frontmatter contains `name` and `description`. The body contains the philosophy, a **Quick Reference** table, numbered **Core Principles**, a **Common Mistakes** table, and a **Review Output Format** section.
- `typography.md`, `surfaces.md`, `animations.md`, `icons.md`, and `performance.md` contain detailed guidance beyond the entry-point principles. Link to them from the Quick Reference table using relative paths.
- `agents/openai.yaml` contains UI metadata and must stay aligned with the skill's scope.

## Authoring conventions

- Keep the skill focused on interface-polish details. Do not expand it into a complete accessibility, layout, color-system, or UX-writing audit.
- Make principles prescriptive and specific, but scope them when context changes the correct answer. Avoid unconditional rules when reduced motion, interaction frequency, semantics, or an existing design system requires a different approach.
- Match the target project's existing styling system (Tailwind vs. plain CSS vs. CSS-in-JS) rather than imposing one.
- Keep detailed recipes and code examples in the reference files; keep only essential selection guidance in `SKILL.md`.
- Update the frontmatter description and `agents/openai.yaml` when the skill's discovery scope changes.
- Preserve the `quick` and `full` review modes, finding caps, evidence requirements, rejected candidates, verification, and verdict.
