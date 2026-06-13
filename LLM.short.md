# b-style Editorial Guide (short)

For AI agents building editorial content: articles, landing sections, CMS blocks. Use **only** `b-*` classes. No inline styles, no Tailwind, no unprefixed Bulma.

Full guide: `LLM.md` | Demos: `index.html`

## Editorial shell

```html
<section class="b-section">
  <div class="b-container">
    <div class="b-content">...</div>
  </div>
</section>
```

## Typography & b-content

Wrap prose in `.b-content`. Use semantic `h1–h4`, `p`, `small`, `ul/ol`, `blockquote`, `a`.

```html
<div class="b-content">
  <h2>Section heading</h2>
  <p>Body paragraph with <strong>emphasis</strong>.</p>
</div>
```

## Title and Subtitle

Outside `.b-content` for hero/section headers: `.b-title` + `.b-subtitle`. Sizes: `.b-is-1` … `.b-is-6`.

```html
<p class="b-title b-is-3">Article title</p>
<p class="b-subtitle b-is-5">Deck or summary line</p>
```

## Colors

Semantic tokens: `primary`, `link`, `info`, `success`, `warning`, `danger`, `dark`, `light`.

```html
<span class="b-tag b-is-info">Label</span>
<p class="b-has-text-success">Positive text</p>
<div class="b-box b-has-background-primary b-has-text-primary-invert">Highlight</div>
```

## Buttons

```html
<div class="b-buttons">
  <a class="b-button b-is-primary" href="#">Read more</a>
  <a class="b-button b-is-outlined" href="#">Share</a>
</div>
```

## Notifications

```html
<div class="b-notification b-is-info">
  <button class="b-delete"></button>
  <strong>Note</strong> — Editorial callout text.
</div>
```

## Messages

```html
<div class="b-message b-is-warning">
  <div class="b-message-header"><p>Editor's note</p></div>
  <div class="b-message-body">Clarification or disclaimer.</div>
</div>
```

## Box

Grouped block or sidebar callout:

```html
<div class="b-box">
  <p class="b-title b-is-5">Related</p>
  <p>Supporting content.</p>
</div>
```

## Tables

Always wrap in `.b-table-container` for horizontal scroll on mobile.

```html
<div class="b-table-container">
  <table class="b-table b-is-striped b-is-fullwidth">
    <thead><tr><th>Col</th></tr></thead>
    <tbody><tr><td>Data</td></tr></tbody>
  </table>
</div>
```

## Images

```html
<figure class="b-image b-is-16by9 b-is-fullwidth">
  <img src="photo.jpg" alt="Description" />
</figure>
```

Ratios: `b-is-square`, `b-is-4by3`, `b-is-16by9`. Optional: `b-is-rounded` on `img`.

## Tabs

```html
<div class="b-tabs b-is-boxed">
  <ul>
    <li class="b-is-active"><a>Tab A</a></li>
    <li><a>Tab B</a></li>
  </ul>
</div>
```

## Columns

Multi-column editorial layouts:

```html
<div class="b-columns b-is-multiline">
  <div class="b-column b-is-two-thirds"><div class="b-content">Main</div></div>
  <div class="b-column"><div class="b-box">Aside</div></div>
</div>
```

## Helpers

- Text: `b-has-text-centered`, `b-has-text-weight-bold`, `b-is-italic`
- Spacing: `b-mb-4`, `b-mb-5`, `b-mt-4`, `b-p-4`
- Visibility: `b-is-hidden-touch`, `b-is-hidden-mobile`

## Anti-patterns

```html
<!-- WRONG -->
<div style="color:red" class="flex">...</div>
<button class="button is-primary">Go</button>

<!-- CORRECT -->
<div class="b-box b-has-text-danger">...</div>
<a class="b-button b-is-primary" href="#">Go</a>
```
