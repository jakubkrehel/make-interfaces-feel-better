# Layout & Spacing

Border radius, optical alignment, shadows, and image outlines.

## Concentric Border Radius

When nesting rounded elements, the outer radius must equal the inner radius plus the padding between them:

```
outerRadius = innerRadius + padding
```

### Example

```css
/* Good — concentric radii */
.card {
  border-radius: 20px; /* 12 + 8 */
  padding: 8px;
}
.card-inner {
  border-radius: 12px;
}

/* Bad — same radius on both */
.card {
  border-radius: 12px;
  padding: 8px;
}
.card-inner {
  border-radius: 12px;
}
```

### Tailwind Example

```tsx
// Good — outer radius accounts for padding
<div className="rounded-2xl p-2">       {/* 16px radius, 8px padding */}
  <div className="rounded-lg">          {/* 8px radius = 16 - 8 ✓ */}
    ...
  </div>
</div>

// Bad — same radius on both
<div className="rounded-xl p-2">
  <div className="rounded-xl">          {/* same radius, looks off */}
    ...
  </div>
</div>
```

Mismatched border radii on nested elements is one of the most common things that makes interfaces feel off. Always calculate concentrically.

## Optical Alignment

When geometric centering looks off, align optically instead.

### Buttons with Text + Icon

Use slightly less padding on the icon side to make the button feel balanced:

```css
/* Good — less padding on icon side */
.button-with-icon {
  padding-left: 16px;
  padding-right: 12px; /* icon side, less padding */
}

/* Bad — equal padding looks like icon is pushed too far right */
.button-with-icon {
  padding: 0 16px;
}
```

```tsx
// Tailwind
<button className="pl-4 pr-3 flex items-center gap-2">
  <span>Continue</span>
  <ArrowRightIcon />
</button>
```

### Play Button Triangles

Play icons are triangular and their geometric center is not their visual center. Shift slightly right:

```css
/* Good — optically centered */
.play-button svg {
  margin-left: 2px; /* shift right to account for triangle shape */
}

/* Bad — geometrically centered but looks off */
.play-button svg {
  /* no adjustment */
}
```

### Asymmetric Icons (Stars, Arrows, Carets)

Some icons have uneven visual weight. The best fix is adjusting the SVG directly so no extra margin/padding is needed in the component code.

```tsx
// Best — fix in the SVG itself
// Adjust the viewBox or path to visually center the icon

// Fallback — adjust with margin
<span className="ml-px">
  <StarIcon />
</span>
```

## Shadows Instead of Borders

Prefer subtle `box-shadow` over solid borders for depth. Shadows adapt to any background since they use transparency; solid borders don't. This also helps when using images or multiple colors as backgrounds — solid border colors don't work well on backgrounds other than the ones they were designed for.

### Shadow as Border (Light Mode)

The shadow is comprised of three layers. The first acts as a 1px border ring, the second adds subtle lift, and the third provides ambient depth:

```css
:root {
  --shadow-border:
    0px 0px 0px 1px rgba(0, 0, 0, 0.06),
    0px 1px 2px -1px rgba(0, 0, 0, 0.06),
    0px 2px 4px 0px rgba(0, 0, 0, 0.04);
  --shadow-border-hover:
    0px 0px 0px 1px rgba(0, 0, 0, 0.08),
    0px 1px 2px -1px rgba(0, 0, 0, 0.08),
    0px 2px 4px 0px rgba(0, 0, 0, 0.06);
}
```

### Shadow as Border (Dark Mode)

In dark mode, simplify to a single white ring — layered depth shadows aren't visible on dark backgrounds:

```css
/* Dark mode — adapt to whatever setup the project uses
   (prefers-color-scheme, class, data attribute, etc.) */
--shadow-border: 0 0 0 1px rgba(255, 255, 255, 0.08);
--shadow-border-hover: 0 0 0 1px rgba(255, 255, 255, 0.13);
```

### Usage with Hover Transition

Apply the variable and add `transition-[box-shadow]` for a smooth hover:

```css
.card {
  box-shadow: var(--shadow-border);
  transition-property: box-shadow;
  transition-duration: 150ms;
  transition-timing-function: ease;
}

.card:hover {
  box-shadow: var(--shadow-border-hover);
}
```

### When to Use Shadows vs. Borders

| Use shadows | Use borders |
| --- | --- |
| Cards, containers with depth | Dividers between list items |
| Elevated elements (dropdowns, modals) | Table cell boundaries |
| Elements on varied backgrounds | Form input outlines (for accessibility) |
| Hover/focus states for lift effect | Hairline separators in dense UI |

## Image Outlines

Add a subtle `1px` outline with low opacity to images. This creates consistent depth, especially in design systems where other elements use borders or shadows.

### Light Mode

```css
img {
  outline: 1px solid rgba(0, 0, 0, 0.1);
  outline-offset: -1px; /* inset so it doesn't add to layout */
}
```

### Dark Mode

```css
img {
  outline: 1px solid rgba(255, 255, 255, 0.1);
  outline-offset: -1px;
}
```

### Tailwind with Dark Mode

```tsx
<img
  className="outline outline-1 -outline-offset-1 outline-black/10 dark:outline-white/10"
  src={src}
  alt={alt}
/>
```

**Why outline instead of border?** `outline` doesn't affect layout (no added width/height), and `outline-offset: -1px` keeps it inset so images stay their intended size.
