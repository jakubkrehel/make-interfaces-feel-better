<a href="https://interfaces.dev/">
  <img width="320" height="168" alt="interfaces.dev" src="https://ho1jr3x2dcwdu3t5.public.blob.vercel-storage.com/interfaces-og-image.png" />
</a>

[![skills.sh](https://skills.sh/b/jakubkrehel/make-interfaces-feel-better)](https://skills.sh/jakubkrehel/make-interfaces-feel-better)

An agent skill focused on the small details that make interfaces feel better.

The [skill](skills/make-interfaces-feel-better/SKILL.md) covers animations, typography, icons, hover states, optical alignment, concentric border radius, shadows, hit areas, and other interface details.

Reviews support `quick` and `full` modes. They return prioritized findings with exact locations, proposed changes, reasoning, verification, rejected candidates, and an explicit verdict.

## Install

For Claude Code:

```bash
npx skills add jakubkrehel/make-interfaces-feel-better
```

For Codex or other skill-aware agents, copy the complete skill directory:

```
skills/make-interfaces-feel-better/
```

Keep the directory intact. `SKILL.md` links to `typography.md`, `surfaces.md`, `animations.md`, `icons.md`, and `performance.md` with relative paths, so copying only `SKILL.md` drops the detailed guidance and agent metadata.

## Use

The default review mode is `full`. Pass `quick` for a shorter review, and add the screen, component, or feature after the mode.

In Claude Code:

```text
/make-interfaces-feel-better
/make-interfaces-feel-better quick
/make-interfaces-feel-better full pricing page
```

In Codex:

```text
$make-interfaces-feel-better
$make-interfaces-feel-better quick
$make-interfaces-feel-better full pricing page
```

## License

MIT. See [LICENSE](LICENSE).
