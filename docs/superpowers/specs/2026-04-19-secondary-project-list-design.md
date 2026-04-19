# Secondary Project List — Design Spec

**Date:** 2026-04-19  
**Status:** Approved

## Summary

Add a secondary project list below the existing featured portfolio cards. This list is for projects that don't warrant the full card treatment — no image, less emphasis — but still need a name, short description, and link.

## Context

The portfolio section in `index.html` currently has two featured project cards (horizontal layout: thumbnail + info). This works for highlighted projects but doesn't scale for smaller or older work. A lightweight list tier lets the site grow without every addition requiring a full card.

## Design

### Section layout

1. Existing "Portfolio" section label + featured cards (unchanged)
2. New "Other projects" section label (same visual style as "Portfolio" label: uppercase, accent-dim, 0.75rem, 0.12em letter-spacing)
3. Dense list of secondary entries below

### Entry markup

Each entry is an `<a>` element (full-row clickable, consistent with featured cards).

**Stacked layout inside each entry:**
- **Name** — `var(--heading)` color, `0.92rem` font-size
- **Description** — `var(--text-dim)` color, `0.82rem` font-size, ~2px top margin
- **Link** — `var(--accent)` color, `0.78rem` font-size, `font-weight: 500`, ~4px top margin

**Spacing and dividers:**
- `0.75rem` gap between entries
- `border-bottom: 1px solid var(--border)` on all entries except the last (`:last-child` excludes it)
- ~0.4rem vertical padding per entry
- No background or border on the row itself

**Hover behavior** (matches featured card feel):
- `background: var(--bg-hover)`
- `border-bottom-color: var(--accent-dim)`
- Transition on background and border-color (`0.3s`)

### Responsive

On mobile (`max-width: 640px`): same layout, no changes needed — stacked already works at narrow widths.

## What stays the same

- Featured cards: unchanged
- Section labels: "Other projects" reuses the `.section-label` style
- Color tokens, fonts, transition durations: all from existing CSS custom properties
- Footer, contact, nav: untouched