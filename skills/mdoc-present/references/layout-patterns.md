# Canonical Layout Patterns

Use these patterns when the source Markdown is more than a plain report and needs a polished presentation rhythm. Keep the content source-faithful; these patterns only change structure and emphasis.

## Hero Summary

Use the first paragraph after `#` as `.hero-desc` when it describes the whole document.

```html
<header class="hero">
  <h1 class="reveal-blur">Product Solution Overview</h1>
  <div class="hero-underline"></div>
  <p class="hero-desc reveal-blur">A concise summary of the page's scope, audience, and core value.</p>
  <div class="hero-tags reveal-blur">
    <span class="hero-tag">Integration</span>
    <span class="hero-tag">AI Workflow</span>
  </div>
</header>
```

If the paragraphs after `#` define levels, scope, assumptions, or disclaimers instead of summarizing the page, render them as `.note-block.reveal` below the hero.

## Value Tables

Use `.value-pill` for short label-like table cells in value, capability, scenario, or category columns.

```html
<div class="table-wrap">
  <table>
    <thead>
      <tr><th>Scenario</th><th>Value</th><th>Description</th></tr>
    </thead>
    <tbody>
      <tr>
        <td>Customer support</td>
        <td><span class="value-pill">Faster response</span></td>
        <td>Route common questions to an AI assistant while preserving the original chat experience.</td>
      </tr>
    </tbody>
  </table>
</div>
```

Do not wrap long explanatory sentences in `.value-pill`.

## Flow Cards

Use `.flow-cards` for practical sequences where each step has a title and detail.

```html
<div class="flow-cards">
  <div class="flow-card">
    <div class="flow-card-num">1</div>
    <div class="flow-card-title">Prepare the application</div>
    <div class="flow-card-desc">Configure the agent, knowledge base, or workflow before connecting it to chat.</div>
    <div class="flow-card-check">Done when the agent can answer independently.</div>
  </div>
  <div class="flow-card">
    <div class="flow-card-num">2</div>
    <div class="flow-card-title">Connect the entry point</div>
    <div class="flow-card-desc">Expose the agent in the existing app conversation surface.</div>
    <div class="flow-card-check">Done when a user can send the first message.</div>
  </div>
</div>
```

Prefer a plain ordered list when steps are short one-line actions without supporting detail.

## Glass Cards

Use `.glass-row` plus `.glass-card` for feature summaries, comparison points, or key metrics that should be scanned before detailed tables.

```html
<div class="glass-row">
  <div class="glass-card">
    <h4>Capability</h4>
    <p>Short explanation of a core capability or benefit.</p>
  </div>
  <div class="glass-card teal">
    <h4>Outcome</h4>
    <p>Short explanation of a business or product outcome.</p>
  </div>
</div>
```

Keep cards compact. Use tables for dense capability breakdowns and `.note` for caveats.
