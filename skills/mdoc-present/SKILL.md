---
name: mdoc-present
description: "Convert any Markdown document into a self-contained HTML presentation page that reuses the built-in canonical visual system: warm paper background, editorial hero, glass sections/cards, numbered sections, responsive tables, value pills, flow cards, badges, and optional Mermaid diagrams."
---

# Markdown to Canonical HTML Presentation

Convert arbitrary Markdown into a polished, self-contained HTML document that uses the built-in canonical style language. Generated pages should feel like documents from the same design system, not a new visual direction.

## Canonical Reference

- Style reference: `references/design-tokens.md`
- Layout patterns: `references/layout-patterns.md`
- Mermaid reference: `references/mermaid-setup.md`

Use the style reference as the canonical source for visual decisions: colors, typography, page width, glass cards, section numbering, table density, badges, value pills, flow cards, motion, and mobile behavior.

## Workflow

1. Read the source Markdown completely.
2. Read `references/design-tokens.md` completely.
3. Read `references/layout-patterns.md` completely when the source contains product方案, value proposition, implementation steps, onboarding flow, capability tables, feature comparisons, or a page-level narrative beyond plain sections.
4. If the Markdown contains a Mermaid code fence, read `references/mermaid-setup.md` completely.
5. Derive the document title from the first `#` heading. If no `#` exists, use the file name.
6. Generate one self-contained `.html` file:
   - Inline all CSS in `<style>`.
   - Set `<html lang>` from the source language when obvious; default to `zh-CN` for Chinese or mixed Chinese/English documents.
   - Use Google Fonts links exactly as specified in the style reference.
   - Use Mermaid CDN only when Mermaid diagrams are present.
   - Do not require external CSS or local assets.
7. Preview or validate the output when the environment allows it. At minimum, inspect the generated HTML for broken tags, missing style blocks, and unescaped Markdown content.

## Non-Negotiable Style Rules

- Use the canonical warm paper background: SVG noise plus `#faf9f6` to `#f0ece4` vertical gradient.
- Use the canonical type stack:
  - `Noto Serif SC` for the hero title.
  - `Noto Sans SC` for body text.
  - `JetBrains Mono` for code.
- Use the canonical layout width: `min(900px, calc(100% - clamp(16px, 4vw, 40px)))`.
- Wrap each `##` section in `.section.reveal` with:
  - `.section-num` values `01`, `02`, `03`, ...
  - The inset left gradient rail.
  - Glass background, white border, and the same shadow stack.
- Use `.subsection` for `###` groups inside a section.
- Use `.table-wrap` around all tables.
- Preserve the canonical badge system for recognized values:
  - `L1`, `L2`, `L3` -> `.level-badge.l1`, `.level-badge.l2`, `.level-badge.l3`
  - `Yes`, `Y`, `是`, `True`, `Done` -> `.badge.badge-yes`
  - `No`, `N`, `否`, `False`, `Not required` -> `.badge.badge-no`
  - `Partial`, `Semi`, `部分`, `In progress` -> `.badge.badge-partial`
  - Other short status values may use `.badge` with the closest semantic variant.
- Use `.summary-table` for summary/total tables, especially tables containing `Total`, `Subtotal`, `合计`, or `小计`.
- Use `.note-block.reveal` for introductory notes, definitions, disclaimers, legends, or metadata that appear before the first `##`.
- Use `.mvp-intro` for short ordered-list flow descriptions under headings such as `MVP`, `Minimum loop`, `Workflow`, `Process`, `流程`, or `闭环`.
- Use `.hero-desc.reveal-blur` for one concise page-level summary under the hero title when the source has an introductory paragraph that describes the whole document.
- Use `.value-pill` for short benefit, capability, scenario, or label cells in tables.
- Use `.flow-cards` with `.flow-card` for implementation, onboarding, integration, launch, or validation steps that have a sequence and per-step explanation.
- Keep all fixed values responsive with `clamp()`, `min()`, or percentage widths.
- Keep tables horizontally scrollable with `overflow-x: auto`.
- Include `-webkit-backdrop-filter` anywhere `backdrop-filter` is used.
- Include print and reduced-motion media rules.

## Markdown Mapping

| Markdown input | HTML output |
|---|---|
| First `# Title` | `<header class="hero">` with `<h1 class="reveal-blur">`, underline, and optional tags |
| First paragraph after `#` when it summarizes the whole document | `<p class="hero-desc reveal-blur">...</p>` inside `.hero` |
| Remaining paragraphs after `#` and before first `##` | `.note-block.reveal` |
| `## Heading` | `<section class="section reveal"><span class="section-num">NN</span><h2>...</h2>...</section>` |
| `### Heading` | `<div class="subsection"><h3>...</h3>...</div>` |
| Normal paragraphs | `<p>` inside the current section/subsection |
| Ordered or unordered lists | Native `<ol>` / `<ul>`; use `<div class="mvp-intro"><ol>...</ol></div>` for short process lists under MVP/流程/闭环 headings |
| Markdown tables | `.table-wrap > table`; center compact status columns when appropriate |
| Table cells containing short value labels | `<span class="value-pill">...</span>` |
| Short feature lists, key metrics, or comparison points | `<div class="glass-row"><div class="glass-card">...</div></div>` |
| Numbered implementation/onboarding steps with title and detail | `<div class="flow-cards"><div class="flow-card">...</div></div>` |
| Inline code | `<code>` |
| Fenced code | `<pre><code>` unless the language is `mermaid` |
| Mermaid code fence | `.flowchart-wrap > <pre class="mermaid">` plus Mermaid setup |
| Blockquote / note text | `.note` inside a section, or `.note-block` before sections |
| Horizontal rule | Prefer section spacing; only emit `<hr>` if it has semantic value |

## Hero Tags

The canonical template uses compact pill tags in the hero. For arbitrary Markdown:

- If the Markdown contains frontmatter fields such as `tags`, `category`, `scenario`, `audience`, or `status`, render them as `.hero-tag`.
- If no metadata exists, infer up to five short tags from prominent terms in the title and top-level headings.
- Keep tags short. Do not invent marketing copy.

## Table Enhancement Rules

When converting tables, apply semantic enhancement without changing the source meaning:

- Add `class="center"` to columns whose header suggests status, level, priority, required, done, count, total, MVP, or yes/no values.
- Convert recognized status and level cell values into badges.
- Convert short value proposition cells into `.value-pill` when the cell is a label-like phrase rather than a sentence. Good candidates are headers or columns named `价值`, `能力`, `场景`, `标签`, `Value`, `Capability`, or `Scenario`.
- Preserve longer descriptive cells as plain text with inline `<code>` where needed.
- If the table is wide, keep `min-width: 600px` from the canonical CSS.
- If a final row label is `Total`, `Grand Total`, `合计`, or similar, add `class="total-row"` to that row.

## Flow Cards

Use flow cards when the Markdown describes a sequence of practical steps and each step includes a compact title plus supporting explanation. Prefer flow cards over a plain ordered list for headings such as `接入流程`, `实施步骤`, `上线流程`, `Integration steps`, `Onboarding`, or `Launch plan`.

Each flow card should contain:

- `.flow-card-num`: the step number.
- `.flow-card-title`: the short action title.
- `.flow-card-desc`: the main explanation.
- Optional `.flow-card-check`: completion criteria, acceptance criteria, or validation standard.

Do not use flow cards for long prose, tables, or lists where items have no meaningful per-step detail.

## Mermaid

For Mermaid code fences, follow `references/mermaid-setup.md` exactly. Keep diagrams visually aligned with the canonical glass style and remove Mermaid's default opaque label backgrounds.

## Output Skeleton

Use this structure for every generated page:

```html
<!DOCTYPE html>
<html lang="{{lang}}">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@400;500;600;700&family=Noto+Serif+SC:wght@400;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<title>{{title}}</title>
<style>
/* Inline the canonical CSS from references/design-tokens.md. */
</style>
</head>
<body>
<header class="hero">
  <h1 class="reveal-blur">{{title}}</h1>
  <div class="hero-underline"></div>
  {{optional_hero_desc}}
  <div class="hero-tags reveal-blur">{{tags}}</div>
</header>
{{optional_note_block}}
<main class="content">
  {{sections}}
</main>
<script>
/* IntersectionObserver reveal script from the style reference. */
</script>
{{optional_mermaid_script}}
</body>
</html>
```

## Quality Bar

Before finishing, verify that:

- The result uses the canonical color palette and typography.
- Every `##` became a numbered glass section.
- Tables are wrapped, scrollable, and visually dense like the canonical template.
- Short value labels in tables use `.value-pill` where it improves scannability.
- Ordered implementation flows use `.flow-cards` when the source provides step-level details.
- `L1/L2/L3` and yes/no values are rendered as badges when present.
- Mermaid diagrams, if present, are wrapped and initialized.
- The page is readable on mobile; `.section-num` hides below `480px`.
- The output is self-contained except for Google Fonts and optional Mermaid CDN.
