# Design System

## 2025–2026 Trending Design Elements

---

## 1. Color System

### Palette
| Token | Value | Usage |
|-------|-------|-------|
| `--color-primary` | `#6C63FF` | CTA buttons, active states |
| `--color-secondary` | `#FF6584` | Accents, highlights |
| `--color-surface` | `#0F0F1A` | Dark background (default) |
| `--color-surface-alt` | `#1A1A2E` | Card / panel backgrounds |
| `--color-on-surface` | `#E8E8F0` | Body text |
| `--color-muted` | `#6B6B80` | Secondary text, placeholders |
| `--color-border` | `rgba(255,255,255,0.08)` | Glassmorphism borders |

### Trend: Dark Mode First
- Default to dark backgrounds (`#0F0F1A`)
- Provide a light mode override via `[data-theme="light"]`
- Use OKLCH for perceptually uniform color interpolation

```css
:root {
  --color-primary: oklch(60% 0.22 270);
  --color-accent:  oklch(68% 0.20 340);
}
```

---

## 2. Typography

### Type Scale (Fluid)
```css
--text-xs:   clamp(0.75rem,  1vw,  0.875rem);
--text-sm:   clamp(0.875rem, 1.2vw, 1rem);
--text-base: clamp(1rem,     1.5vw, 1.125rem);
--text-lg:   clamp(1.125rem, 2vw,  1.5rem);
--text-xl:   clamp(1.5rem,   3vw,  2.25rem);
--text-2xl:  clamp(2rem,     5vw,  3.75rem);
--text-3xl:  clamp(2.5rem,   7vw,  5.5rem);
```

### Font Stack
- **Display**: `"Cabinet Grotesk"`, `"Syne"`, `"Plus Jakarta Sans"`
- **Body**: `"Inter"`, `"DM Sans"`, system-ui
- **Mono**: `"Geist Mono"`, `"JetBrains Mono"`

### Trend: Variable Fonts + Kinetic Type
```css
@font-face {
  font-family: "Cabinet Grotesk";
  src: url("/fonts/CabinetGrotesk-Variable.woff2") format("woff2");
  font-weight: 100 900;
}

/* Animate font-weight on hover for kinetic effect */
.headline:hover { font-variation-settings: "wght" 800; }
```

---

## 3. Glassmorphism

### Usage
Apply to cards, modals, navigation bars overlaying rich backgrounds.

```css
.glass {
  background: rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(20px) saturate(160%);
  -webkit-backdrop-filter: blur(20px) saturate(160%);
  border: 1px solid rgba(255, 255, 255, 0.10);
  border-radius: 1rem;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.30);
}
```

---

## 4. Bento Grid Layout

A modular, asymmetric card grid used for feature showcases and dashboards.

```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 200px;
  gap: 1rem;
}

.bento-card--wide  { grid-column: span 2; }
.bento-card--tall  { grid-row: span 2; }
.bento-card--large { grid-column: span 2; grid-row: span 2; }
```

Design rules:
- Mix card sizes: `1×1`, `2×1`, `1×2`, `2×2`
- Each card has a single focused purpose (metric, image, text, CTA)
- Subtle gradient or noise texture per card for depth

---

## 5. Micro-interactions & Motion

### Principles
- Duration: `150ms` (instant) → `400ms` (standard) → `700ms` (emphasis)
- Easing: prefer `cubic-bezier(0.34, 1.56, 0.64, 1)` (spring) for interactive elements
- Respect `prefers-reduced-motion`

```css
@media (prefers-reduced-motion: no-preference) {
  .button {
    transition: transform 200ms cubic-bezier(0.34, 1.56, 0.64, 1),
                box-shadow 200ms ease;
  }
  .button:hover  { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(108,99,255,0.40); }
  .button:active { transform: translateY(0px);  box-shadow: none; }
}
```

### Scroll-driven Animations (native CSS)
```css
@keyframes fade-up {
  from { opacity: 0; translate: 0 2rem; }
  to   { opacity: 1; translate: 0 0; }
}

.reveal {
  animation: fade-up linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 30%;
}
```

---

## 6. Noise & Grain Texture

Adds analog warmth and prevents flat-look on solid surfaces.

```css
.noise::after {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: inherit;
  background-image: url("data:image/svg+xml,..."); /* SVG noise filter */
  opacity: 0.04;
  pointer-events: none;
}
```

Alternative: SVG `<feTurbulence>` filter applied via `filter: url(#noise)`.

---

## 7. Aurora / Mesh Gradient Backgrounds

```css
.aurora-bg {
  background:
    radial-gradient(ellipse at 20% 50%, oklch(60% 0.22 270 / 0.5) 0%, transparent 60%),
    radial-gradient(ellipse at 80% 20%, oklch(68% 0.20 340 / 0.4) 0%, transparent 55%),
    radial-gradient(ellipse at 60% 80%, oklch(72% 0.18 200 / 0.3) 0%, transparent 50%),
    #0F0F1A;
  animation: aurora 12s ease-in-out infinite alternate;
}

@keyframes aurora {
  0%   { filter: hue-rotate(0deg)   blur(60px); }
  100% { filter: hue-rotate(40deg)  blur(80px); }
}
```

---

## 8. Spacing & Sizing Tokens

```css
--space-1:  0.25rem;   /*  4px */
--space-2:  0.5rem;    /*  8px */
--space-3:  0.75rem;   /* 12px */
--space-4:  1rem;      /* 16px */
--space-6:  1.5rem;    /* 24px */
--space-8:  2rem;      /* 32px */
--space-12: 3rem;      /* 48px */
--space-16: 4rem;      /* 64px */
--space-24: 6rem;      /* 96px */

--radius-sm: 0.5rem;
--radius-md: 1rem;
--radius-lg: 1.5rem;
--radius-full: 9999px;
```

---

## 9. Component Patterns

### Pill Badge
```css
.badge {
  display: inline-flex;
  align-items: center;
  gap: 0.375rem;
  padding: 0.25rem 0.75rem;
  border-radius: var(--radius-full);
  font-size: var(--text-xs);
  font-weight: 600;
  background: rgba(108, 99, 255, 0.15);
  color: #a89cff;
  border: 1px solid rgba(108, 99, 255, 0.30);
}
```

### Glow Button
```css
.btn-glow {
  position: relative;
  padding: 0.75rem 1.75rem;
  background: var(--color-primary);
  border-radius: var(--radius-full);
  font-weight: 700;
  color: #fff;
  box-shadow: 0 0 0 0 rgba(108, 99, 255, 0);
  transition: box-shadow 300ms ease;
}
.btn-glow:hover {
  box-shadow: 0 0 24px 6px rgba(108, 99, 255, 0.55);
}
```

### Frosted Navigation Bar
```css
.navbar {
  position: sticky;
  top: 0;
  z-index: 100;
  padding: 0.75rem 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(15, 15, 26, 0.70);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}
```

---

## 10. Accessibility Baseline

- **Contrast**: minimum 4.5:1 (WCAG AA) for body text; 3:1 for large text and UI components
- **Focus rings**: always visible, never `outline: none` without a custom replacement
- **Motion**: wrap animations in `@media (prefers-reduced-motion: no-preference)`
- **Semantics**: use native HTML elements (`<button>`, `<nav>`, `<main>`) before reaching for ARIA
- **Color**: never convey information by color alone; pair with icon or label

```css
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 3px;
  border-radius: 4px;
}
```

---

## Quick-reference: Trend Checklist

| Trend | Status |
|-------|--------|
| Dark mode first | ✅ |
| Fluid typography (clamp) | ✅ |
| Variable fonts + kinetic type | ✅ |
| Glassmorphism cards | ✅ |
| Bento grid layout | ✅ |
| Scroll-driven animations (CSS) | ✅ |
| Aurora / mesh gradient bg | ✅ |
| Noise / grain texture | ✅ |
| Glow / neon accents | ✅ |
| OKLCH color space | ✅ |
| Micro-interactions (spring easing) | ✅ |
| Accessibility baseline | ✅ |
