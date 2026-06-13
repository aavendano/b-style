# b-style AI Style Guide

Short editorial guide (≤4000 chars): [`LLM.short.md`](LLM.short.md) · copy view: [`llm-short.html`](llm-short.html)

Use this document when generating HTML/UI for projects styled with **b-style**.

## Purpose

b-style is a Bulma 1.x-based design system with a custom `b-` class prefix, fluid typography (Major Third scale), and brand tokens. Your output must use **only** classes defined in b-style.

Visual demos and copyable snippets: open `index.html` in this repository.

---

## Hard rules

1. Use **ONLY** classes prefixed with `b-` from b-style.
2. Do **NOT** add `<style>` blocks, inline `style=""`, or third-party utility frameworks (Tailwind, Bootstrap, unprefixed Bulma).
3. Do **NOT** use unprefixed Bulma classes (`button`, `is-primary`, `navbar`) — always `b-button`, `b-is-primary`, `b-navbar`.
4. Do **NOT** invent class names. If unsure, prefer layout primitives (`b-box`, `b-section`, `b-columns`) and semantic color helpers.
5. Do **NOT** rely on Alpine.js unless interactivity is explicitly required; static markup should work with CSS alone.
6. Prefer semantic HTML inside b-style components (`<button>`, `<a>`, `<nav>`, `<section>`, labels tied to inputs).

---

## Setup

```html
<link rel="stylesheet" href="node_modules/b-style/dist/b-style.min.css">
```

```scss
@use "b-style/bulma" as *;
```

```html
<html lang="en" data-b-theme="light">
```

Toggle theme: `document.documentElement.setAttribute('data-b-theme', 'dark')`.

Optional Alpine bundle: `dist/alpine.js` (includes collapse, intersect, ajax, carousel plugins).

---

## Naming conventions

| Pattern | Example | Use |
|---------|---------|-----|
| Component | `b-button`, `b-card`, `b-navbar` | Base component |
| Modifier | `b-is-primary`, `b-is-small`, `b-is-active` | Variants and states |
| Helper | `b-has-text-centered`, `b-has-background-info` | Utilities |
| Layout | `b-columns`, `b-column`, `b-container` | Grid and page structure |

All Bulma modifiers use the `b-is-` or `b-has-` prefix.

---

## Design tokens

### Colors (semantic)

`primary`, `link`, `info`, `success`, `warning`, `danger`, `dark`, `light`

Apply on components: `b-is-primary`, `b-is-success`, etc.

Text helpers: `b-has-text-primary`, `b-has-text-success`, …

Background helpers: `b-has-background-primary`, `b-has-text-primary-invert`, …

### Breakpoints

| Name | Min width | Typical use |
|------|-----------|-------------|
| tablet | 768px | Tablet layouts |
| desktop | 1152px | Sidebar, full navbar |
| touch | below 1152px | Mobile/tablet |
| widescreen | 1536px | Wide layouts |
| fullhd | 1920px | Full HD |

Responsive visibility: `b-is-hidden-mobile`, `b-is-hidden-tablet`, `b-is-hidden-touch`, `b-is-hidden-desktop`, `b-is-hidden-widescreen`.

Responsive display: `b-is-flex-desktop`, `b-is-block-mobile`, etc.

### Typography

- Semantic content block: `.b-content` wraps headings and paragraphs.
- Titles: `.b-title` with sizes `.b-is-1` … `.b-is-6`.
- Subtitles: `.b-subtitle` with optional `.b-is-5`, etc.
- Weights: `b-has-text-weight-light`, `b-has-text-weight-normal`, `b-has-text-weight-medium`, `b-has-text-weight-semibold`, `b-has-text-weight-bold`, `b-has-text-weight-extrabold`.
- Transform: `b-is-capitalized`, `b-is-uppercase`, `b-is-lowercase`, `b-is-italic`, `b-is-underlined`.

---

## Layout patterns

```html
<section class="b-section">
  <div class="b-container">
    <div class="b-columns b-is-multiline">
      <div class="b-column b-is-half">...</div>
      <div class="b-column">...</div>
    </div>
  </div>
</section>
```

```html
<section class="b-hero b-is-primary b-is-small">
  <div class="b-hero-body">
    <p class="b-title">Page title</p>
    <p class="b-subtitle">Supporting text</p>
  </div>
</section>
```

Column sizes: `b-is-half`, `b-is-one-third`, `b-is-one-quarter`, `b-is-three-quarters`, etc.

Spacing helpers: `b-m-*`, `b-p-*`, `b-mt-4`, `b-mb-5`, `b-px-4`, `b-pb-4` (0–6 scale).

---

## Component reference

### Buttons

```html
<div class="b-buttons">
  <button class="b-button b-is-primary">Primary</button>
  <button class="b-button b-is-primary b-is-outlined">Outlined</button>
  <button class="b-button b-is-primary b-is-light">Light</button>
  <button class="b-button b-is-primary b-is-rounded">Rounded</button>
  <button class="b-button b-is-info b-is-loading">Loading</button>
  <button class="b-button" disabled>Disabled</button>
  <button class="b-button b-is-text">Text</button>
  <button class="b-button b-is-ghost">Ghost</button>
</div>
```

Sizes: `b-is-small`, default, `b-is-medium`, `b-is-large`.

Colors: `b-is-primary`, `b-is-link`, `b-is-info`, `b-is-success`, `b-is-warning`, `b-is-danger`, `b-is-dark`, `b-is-light`.

### Tags

```html
<span class="b-tag b-is-primary">Primary</span>
<span class="b-tag b-is-primary b-is-small">Small</span>

<div class="b-tags b-has-addons">
  <span class="b-tag b-is-dark">Version</span>
  <span class="b-tag b-is-success">1.0.0</span>
</div>
```

### Notifications

```html
<div class="b-notification b-is-success">
  <button class="b-delete"></button>
  <strong>Success</strong> - Operation completed.
</div>
```

Colors: `b-is-primary`, `b-is-success`, `b-is-warning`, `b-is-danger`, `b-is-info`.

### Messages

```html
<div class="b-message b-is-info">
  <div class="b-message-header">
    <p>Information</p>
    <button class="b-delete" aria-label="delete"></button>
  </div>
  <div class="b-message-body">Message content here.</div>
</div>
```

### Progress

```html
<progress class="b-progress b-is-primary" value="70" max="100">70%</progress>
<progress class="b-progress b-is-primary b-is-small" value="70" max="100">Small</progress>
```

### Box

```html
<div class="b-box">
  <p class="b-title b-is-4">Box title</p>
  <p>Content inside a box.</p>
  <div class="b-buttons">
    <button class="b-button b-is-primary">Action</button>
  </div>
</div>
```

### Cards

```html
<div class="b-card">
  <div class="b-card-header">
    <p class="b-card-header-title">Card title</p>
  </div>
  <div class="b-card-content">
    <div class="b-content"><p>Card body.</p></div>
  </div>
  <footer class="b-card-footer">
    <a href="#" class="b-card-footer-item">Edit</a>
    <a href="#" class="b-card-footer-item b-has-text-danger">Delete</a>
  </footer>
</div>
```

### Tables

```html
<div class="b-table-container">
  <table class="b-table b-is-striped b-is-hoverable b-is-fullwidth">
    <thead>
      <tr><th>Name</th><th>Status</th></tr>
    </thead>
    <tbody>
      <tr>
        <td>Item</td>
        <td><span class="b-tag b-is-success b-is-light">Active</span></td>
      </tr>
    </tbody>
  </table>
</div>
```

### Forms

```html
<div class="b-field">
  <label class="b-label">Email</label>
  <div class="b-control">
    <input class="b-input" type="email" placeholder="you@example.com" />
  </div>
  <p class="b-help b-is-success">Email verified.</p>
</div>

<div class="b-field">
  <label class="b-label">Category</label>
  <div class="b-control">
    <div class="b-select b-is-fullwidth">
      <select><option>Choose...</option></select>
    </div>
  </div>
</div>

<div class="b-field">
  <div class="b-control">
    <label class="b-checkbox">
      <input type="checkbox" checked />
      Accept terms
    </label>
  </div>
</div>

<div class="b-field b-is-grouped">
  <div class="b-control">
    <button class="b-button b-is-primary">Submit</button>
  </div>
</div>
```

Input states: `b-is-success`, `b-is-danger` on `.b-input`, `.b-textarea`, `.b-select`.

### Tabs

```html
<div class="b-tabs">
  <ul>
    <li class="b-is-active"><a>Home</a></li>
    <li><a>Profile</a></li>
  </ul>
</div>

<div class="b-tabs b-is-boxed">...</div>
<div class="b-tabs b-is-toggle b-is-toggle-rounded">...</div>
```

### Breadcrumb

```html
<nav class="b-breadcrumb" aria-label="breadcrumbs">
  <ul>
    <li><a href="#">Home</a></li>
    <li class="b-is-active"><a aria-current="page">Current</a></li>
  </ul>
</nav>
```

Separators: `b-has-arrow-separator`, `b-has-bullet-separator`.

### Panel

```html
<div class="b-panel b-is-primary">
  <p class="b-panel-heading">Section</p>
  <a class="b-panel-block b-is-active">Active item</a>
  <a class="b-panel-block">Item</a>
</div>
```

### Navbar

```html
<nav class="b-navbar b-is-primary b-is-fixed-top-touch" role="navigation">
  <div class="b-navbar-brand">
    <a class="b-navbar-item" href="#"><strong>Brand</strong></a>
    <a role="button" class="b-navbar-burger" aria-label="menu" aria-expanded="false">
      <span></span><span></span><span></span><span></span>
    </a>
  </div>
  <div class="b-navbar-menu">
    <div class="b-navbar-start">
      <a class="b-navbar-item b-is-active">Home</a>
    </div>
    <div class="b-navbar-end">
      <div class="b-navbar-item">
        <a class="b-button b-is-primary">Sign up</a>
      </div>
    </div>
  </div>
</nav>
```

Mobile menu: toggle `.b-is-active` on `.b-navbar-burger` and `.b-navbar-menu`.

Fixed navbar offset: add `b-has-navbar-fixed-top-touch` on `<html>`.

Dropdown: `b-navbar-item b-has-dropdown b-is-hoverable` with `.b-navbar-dropdown`.

### Drawer (custom)

```html
<div class="b-drawer b-is-active">
  <div class="b-drawer-background"></div>
  <div class="b-drawer-panel">
    <nav class="b-menu">...</nav>
  </div>
</div>
```

Toggle `.b-is-active` on `.b-drawer`. Optional scroll lock: `b-is-clipped` on `<html>`.

### Menu (sidebar)

```html
<aside class="b-menu">
  <p class="b-menu-label">Section</p>
  <ul class="b-menu-list">
    <li><a class="b-is-active" href="#">Active</a></li>
    <li><a href="#">Link</a></li>
  </ul>
</aside>
```

### Level

```html
<div class="b-level b-is-mobile">
  <div class="b-level-left"><p class="b-heading">Label</p></div>
  <div class="b-level-right"><p class="b-title">Value</p></div>
</div>
```

### Footer

```html
<footer class="b-footer">
  <div class="b-content b-has-text-centered">
    <p>Footer text</p>
  </div>
</footer>
```

---

## Common task → class mapping

| Task | Classes |
|------|---------|
| Primary CTA | `b-button b-is-primary` |
| Secondary action | `b-button b-is-outlined` or `b-is-light` |
| Status badge | `b-tag b-is-success b-is-light` |
| Page wrapper | `b-section` > `b-container` |
| Two-column layout | `b-columns b-is-multiline` + `b-column b-is-half` |
| Card grid | `b-columns b-is-multiline` + `b-column` + `b-card` |
| Alert banner | `b-notification b-is-warning` or `b-message b-is-danger` |
| Form error | `b-input b-is-danger` + `b-help b-is-danger` |
| Center text | `b-has-text-centered` |
| Hide on mobile | `b-is-hidden-touch` or `b-is-hidden-mobile` |
| Sticky sidebar | `b-is-position-sticky` (desktop) |

---

## Anti-patterns (do NOT do this)

```html
<!-- WRONG: unprefixed Bulma -->
<button class="button is-primary">Save</button>

<!-- WRONG: inline styles -->
<div style="padding: 16px; color: purple">Content</div>

<!-- WRONG: Tailwind / custom utilities -->
<div class="flex gap-4 p-6 rounded-lg">Content</div>

<!-- WRONG: invented classes -->
<div class="b-card-elevated b-shadow-lg">Content</div>

<!-- WRONG: custom CSS class on top of b-style -->
<div class="my-custom-card b-box">Content</div>
```

```html
<!-- CORRECT -->
<div class="b-box b-mb-5">
  <p class="b-title b-is-4">Title</p>
  <button class="b-button b-is-primary">Save</button>
</div>
```

---

## Custom b-style modules (in dist/b-style.css)

Available beyond standard Bulma:

- **Drawer**: `.b-drawer`, `.b-drawer-background`, `.b-drawer-panel`
- **Overlays**: `.b-has-image-overlay`, `.b-badge-{color}`, `.b-overlay-gradient-bottom`
- **Carousel**: `.b-carousel-wrapper`, `.b-carousel`, `.b-carousel-item`
- **Card horizontal**: `.b-card-horizontal`, `.b-header-vertical`

Use only when the UI pattern requires them. See `index.html` catalog for visual reference.

---

## Agent checklist

Before returning HTML:

- [ ] Every class starts with `b-` (or is standard HTML without styling role)
- [ ] No inline styles or `<style>` tags
- [ ] Colors use semantic tokens (`b-is-primary`, not hex values)
- [ ] Layout uses `b-section`, `b-container`, `b-columns` where appropriate
- [ ] Forms use `b-field` > `b-label` + `b-control` structure
- [ ] Interactive navbar includes burger + menu toggle pattern on touch
- [ ] Theme attribute set on `<html data-b-theme="light">` when relevant

---

## References

- Interactive catalog: `index.html`
- Copyable snippets: each section in `index.html` under **Copy** buttons
- Package install: `npm install github:aavendano/b-style`
- SCSS entry: `@use "b-style/bulma" as *;`
