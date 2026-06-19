# Make Interfaces Feel Better

An [Agent Skill](https://docs.anthropic.com/en/docs/claude-code/skills) based on the article [Details that make interfaces feel better](https://jakub.kr/writing/details-that-make-interfaces-feel-better).

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

For Claude Code:

```bash
npx skills add jakubkrehel/make-interfaces-feel-better
```

For Codex or other skill-aware agents, use the complete skill directory:

```
skills/make-interfaces-feel-better/
```

Keep the directory intact. `SKILL.md` links to `typography.md`, `surfaces.md`, `animations.md`, and `performance.md` with relative paths, so copying only `SKILL.md` drops the detailed guidance.

## Usage

Once installed, your agent can apply these principles when building UI components, reviewing frontend code, or implementing animations.

In Claude Code, you can also invoke it manually:

```
/make-interfaces-feel-better
```

## License

MIT. See [LICENSE](LICENSE).
