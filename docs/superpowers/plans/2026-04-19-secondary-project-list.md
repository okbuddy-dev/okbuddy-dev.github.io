# Secondary Project List — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a dense, text-only secondary project list below the existing featured cards in the portfolio section.

**Architecture:** All changes are in `index.html` — CSS styles for the new `.project-list` and `.project-list-item` classes in the existing `<style>` block, plus HTML markup for the "Other projects" subsection inside the portfolio `<section>`. No new files, no JS, no data layer.

**Tech Stack:** Static HTML + CSS (existing site stack)

---

### Task 1: Add CSS styles for the secondary list

**Files:**
- Modify: `index.html:178` (insert after `.project-link` rule, before the Contact section CSS)

- [ ] **Step 1: Add `.project-list` container styles**

Insert the following CSS block after line 178 (after the `.project-link` closing `}`), before the `/* ── Contact ── */` comment:

```css
.project-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-top: 3rem;
}

.project-list-item {
  display: block;
  text-decoration: none;
  color: inherit;
  padding: 0.4rem 0;
  border-bottom: 1px solid var(--border);
  transition: background 0.3s, border-color 0.3s;
}

.project-list-item:last-child {
  border-bottom: none;
}

.project-list-item:hover {
  background: var(--bg-hover);
  border-bottom-color: var(--accent-dim);
}

.project-list-item .item-name {
  color: var(--heading);
  font-size: 0.92rem;
}

.project-list-item .item-desc {
  color: var(--text-dim);
  font-size: 0.82rem;
  margin-top: 2px;
}

.project-list-item .item-link {
  font-size: 0.78rem;
  color: var(--accent);
  font-weight: 500;
  margin-top: 4px;
}
```

- [ ] **Step 2: Verify CSS is syntactically valid**

Open `index.html` in a browser and confirm the page renders without layout breakage. The new styles won't have visible effect yet since no HTML uses them.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add CSS for secondary project list"
```

---

### Task 2: Add HTML markup for the secondary list

**Files:**
- Modify: `index.html:301` (insert after `</div>` closing `.portfolio-grid`, before `</section>`)

- [ ] **Step 1: Add the "Other projects" label and list items**

Insert the following HTML after line 301 (after the `</div>` that closes `.portfolio-grid`), before the `</section>` that closes the portfolio section:

```html
      <div class="section-label" style="margin-top:3rem">Other projects</div>
      <div class="project-list">

        <a href="https://tool.okbuddy.dev" class="project-list-item">
          <div class="item-name">Some Tool</div>
          <div class="item-desc">A quick CLI thing I threw together.</div>
          <div class="item-link">tool.okbuddy.dev →</div>
        </a>

        <a href="https://thing.okbuddy.dev" class="project-list-item">
          <div class="item-name">Another Thing</div>
          <div class="item-desc">Experiment with websockets.</div>
          <div class="item-link">thing.okbuddy.dev →</div>
        </a>

        <a href="https://old.okbuddy.dev" class="project-list-item">
          <div class="item-name">Old Project</div>
          <div class="item-desc">First thing I ever shipped.</div>
          <div class="item-link">old.okbuddy.dev →</div>
        </a>

      </div>
```

_These are placeholder entries with dummy URLs. Replace with real projects before merge._

- [ ] **Step 2: Verify rendering in browser**

Open `index.html` in a browser and confirm:
- "Other projects" label appears below the featured cards
- Three list items render stacked: name, description, link
- Bottom-border divider between items (none on last item)
- Hover on a row shows `bg-hover` background and accent-colored bottom border
- Entire row is clickable (links to the project URL)
- No layout breakage on desktop or narrow viewport

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add secondary project list markup"
```

---

### Task 3: Responsive style check (no changes expected)

**Files:**
- Modify: `index.html:240-255` (existing `@media` block, only if needed)

- [ ] **Step 1: Test at 640px-wide viewport**

Resize browser to mobile width (≤640px). The secondary list is already stacked and uses no grid columns or side-by-side layout, so it should work without any additional responsive rules. Verify:
- List items remain readable and properly spaced
- No horizontal overflow
- Hover behavior still works on touch devices (not critical but verify no breakage)

- [ ] **Step 2: If no changes needed, commit is skipped. If a responsive fix was required, commit it.**

---

### Task 4: Replace placeholder entries with real projects (manual)

**Files:**
- Modify: `index.html` (the `.project-list` HTML added in Task 2)

- [ ] **Step 1: Replace the three placeholder entries with actual project data**

Update each `<a class="project-list-item">` with real `href`, name, description, and link text. Add or remove entries to match the actual set of secondary projects.

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "feat: populate secondary project list with real entries"
```