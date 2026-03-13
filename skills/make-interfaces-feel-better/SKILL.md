---
name: make-interfaces-feel-better
description: Design engineering principles for making interfaces feel polished. Use when building UI components, reviewing frontend code, implementing animations, hover states, shadows, borders, typography, micro-interactions, enter/exit animations, or any visual detail work. Triggers on UI polish, design details, "make it feel better", "feels off", stagger animations, border radius, optical alignment, font smoothing, tabular numbers, image outlines, box shadows.
---

# Details that make interfaces feel better

Great interfaces rarely come from a single thing. It's usually a collection of small details that compound into a great experience. Apply these principles when building or reviewing UI code.

## Text wrapping

Use `text-wrap: balance` (or Tailwind's `text-balance`) on headings and short text blocks. It distributes text evenly across lines, avoiding orphaned words.

Use `text-wrap: pretty` as an alternative — it optimizes the last line to avoid orphans but is slightly more expensive.

## Concentric border radius

When nesting rounded elements, the outer radius must equal the inner radius plus the padding between them:

```
outerRadius = innerRadius + padding
```

Mismatched border radii on nested elements is one of the most common things that makes interfaces feel off. Always calculate concentrically.

## Animate icons contextually

When icons appear or disappear contextually (e.g., on hover, on state change), animate them with `opacity`, `scale`, and `blur` rather than just toggling visibility. This makes transitions feel responsive.

Spring animations (e.g., via Motion/Framer Motion) work particularly well for icon transitions.

## Font smoothing (macOS)

On macOS, text can render heavier than intended. Apply `-webkit-font-smoothing: antialiased` (or Tailwind's `antialiased` class) to the root layout so all text renders crisper and thinner.

## Tabular numbers

When numbers update dynamically (counters, prices, timers), use `font-variant-numeric: tabular-nums` (or Tailwind's `tabular-nums`) to prevent layout shift. This makes all digits equal width.

Note: some fonts like Inter change the visual appearance of numerals with this property.

## Interruptible animations

- **CSS transitions**: interpolate toward the latest state and can be interrupted mid-animation. Use these for interactive state changes (hover, toggle, open/close).
- **CSS keyframe animations**: run on a fixed timeline and don't retarget. Use these for staged sequences that run once (enter animations, loading states).

Users change intent mid-interaction. If animations aren't interruptible, the interface feels broken. Always prefer CSS transitions for interactive elements.

## Enter animations: split and stagger

Don't animate a single large container. Break content into semantic chunks and animate each individually:

1. Split into logical groups (title, description, buttons)
2. Stagger with ~100ms delay between groups
3. For titles, consider splitting into individual words with ~80ms stagger
4. Combine `opacity`, `blur`, and `translateY` for enter animations

## Exit animations: keep them subtle

Exit animations should be softer and less attention-grabbing than enter animations:

- Use a small fixed `translateY` value (e.g., `-12px`) instead of the full container height
- Keep some directional movement to indicate where the element went
- Don't remove exit animation entirely — subtle motion preserves context

## Optical alignment over geometric alignment

When geometric centering looks off, align optically instead:

- Buttons with text + icon: use slightly less padding on the icon side
- Play button triangles: shift slightly right to account for visual weight
- Asymmetric icons (stars, arrows): adjust with margin/padding, or fix in the SVG itself

The best fix for icons is adjusting the SVG directly so no extra margin/padding is needed.

## Shadows instead of borders

Prefer subtle `box-shadow` over solid borders for depth:

```css
box-shadow:
  0px 1px 1px rgba(0, 0, 0, 0.03),
  0px 4px 6px rgba(0, 0, 0, 0.02),
  0px 1px 2px rgba(0, 0, 0, 0.04);
```

- Layer multiple shadows for natural depth (typically 3 shadows)
- For hover states, use the same shadows but slightly darker
- Add `transition-property: box-shadow` for smooth hover transitions
- Shadows adapt to any background since they use transparency; solid borders don't

## Image outlines

Add a subtle `1px` outline with low opacity to images:

```css
outline: 1px solid rgba(0, 0, 0, 0.1); /* light mode */
outline: 1px solid rgba(255, 255, 255, 0.1); /* dark mode */
```

This creates consistent depth, especially in design systems where other elements use borders.
