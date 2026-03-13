# Make Interfaces Feel Better

An [Agent Skill](https://docs.anthropic.com/en/docs/claude-code/skills) based on the article [Details that make interfaces feel better](https://jakub.kr/writing/details-that-make-interfaces-feel-better) by Jakub Krehel.

This skill teaches AI coding assistants (Claude Code, Codex, etc.) the small design engineering details that compound into a great interface.

## What it covers

- Text wrapping (`text-wrap: balance` / `pretty`)
- Concentric border radius for nested elements
- Contextual icon animations with opacity, scale, and blur
- Font smoothing on macOS
- Tabular numbers for dynamic values
- Interruptible animations (CSS transitions vs keyframes)
- Enter animations with split and stagger
- Subtle exit animations
- Optical vs geometric alignment
- Shadows instead of borders
- Image outlines for depth

## Installation

Clone this repo into your Claude Code skills directory:

```bash
# Personal (all projects)
git clone https://github.com/jakubkrehel/make-interfaces-feel-better ~/.claude/skills/make-interfaces-feel-better

# Project-specific
git clone https://github.com/jakubkrehel/make-interfaces-feel-better .claude/skills/make-interfaces-feel-better
```

Or add it as a [Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins).

## Usage

Once installed, Claude will automatically apply these principles when building UI components, reviewing frontend code, or implementing animations.

You can also invoke it manually:

```
/make-interfaces-feel-better
```
