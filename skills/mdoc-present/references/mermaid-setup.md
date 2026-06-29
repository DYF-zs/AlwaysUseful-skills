# Mermaid Setup

Use this reference only when the Markdown contains a Mermaid code fence. The goal is to make Mermaid diagrams match the canonical glass document style.

## Markup

Render each Mermaid code fence as:

```html
<div class="flowchart-wrap">
  <pre class="mermaid">
flowchart TD
  A["Start"] --> B["Next step"]
  </pre>
</div>
```

Copy the Mermaid source exactly, escaping only what HTML requires.

## CDN and Initialization

Append this module script near the end of `<body>`, after the reveal script:

```html
<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';

mermaid.initialize({
  startOnLoad: true,
  theme: 'base',
  themeVariables: {
    primaryColor: 'rgba(255,255,255,0.75)',
    primaryTextColor: '#1a1a1a',
    primaryBorderColor: 'rgba(0,0,0,0.08)',
    lineColor: '#c8c4bc',
    secondaryColor: 'rgba(255,255,255,0.75)',
    tertiaryColor: 'rgba(255,255,255,0.75)',
    edgeLabelBackground: 'transparent',
    background: 'transparent',
    fontSize: '10px'
  },
  flowchart: {
    htmlLabels: true,
    curve: 'basis',
    nodeSpacing: 8,
    rankSpacing: 14,
    padding: 8
  }
});

setTimeout(() => {
  document.querySelectorAll('.flowchart-wrap .node rect, .flowchart-wrap .node polygon').forEach(el => {
    el.removeAttribute('fill');
    el.removeAttribute('style');
  });
  document.querySelectorAll('.flowchart-wrap .labelBkg').forEach(el => {
    el.style.background = 'transparent';
    el.style.backgroundColor = 'transparent';
  });
}, 500);
</script>
```

## Required CSS

The canonical CSS in `design-tokens.md` already includes `.flowchart-wrap` and Mermaid override rules. Do not duplicate them unless the output omits the canonical CSS for some reason.

The important overrides are:

- Mermaid canvas background must remain transparent.
- Node shapes use translucent white fill, soft border, 8px radius, and subtle drop shadow.
- Edge labels must be transparent. Mermaid v11 uses HTML `div.labelBkg` when `htmlLabels: true`, so both CSS and the cleanup script are required.
- Diagrams must be horizontally scrollable through `.flowchart-wrap { overflow-x: auto; }`.
