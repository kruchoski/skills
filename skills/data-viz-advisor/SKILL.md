---
name: data-viz-advisor
description: |
  Select the right visualization type and apply design best practices grounded
  in Tufte, Few, Cairo, Nussbaumer Knaflic, and Hichert (IBCS). Covers chart
  selection, data-ink ratio, the SUCCESS framework, accessibility, and
  anti-patterns. Use BEFORE building charts.
  MANDATORY TRIGGERS: which chart, chart type, data visualization best practices,
  how to visualize, chartjunk, data-ink ratio, Tufte
source: custom
effort: normal
---

# Data Visualization Advisor

## Overview

This skill guides **chart selection and design decisions** — the thinking that happens before you open a spec file. It does NOT cover rendering (that's `vega-lite-charts`) or brand colors (that's `brand-guidelines`).

**Use this skill when:**
- Choosing which chart type fits the data
- Reviewing a chart for design quality
- Checking whether a visualization is misleading or cluttered
- Applying data-ink ratio, graphical integrity, or IBCS standards

**Keywords**: data visualization, chart selection, Tufte, data-ink ratio, chartjunk, IBCS, SUCCESS, small multiples, graphical integrity, accessible charts

---

## Core Principles

### 1. Data-Ink Ratio (Tufte)

**Maximize the share of ink devoted to data.**

Every element on the chart should earn its place. If removing an element doesn't reduce the reader's understanding, remove it.

- Erase non-data ink: decorative borders, background fills, redundant gridlines
- Erase redundant data-ink: data labels that repeat axis values
- Violation: A bar chart with gradient fills, drop shadows, and a textured background

### 2. Graphical Integrity (Tufte)

**The visual representation must be proportional to the data.**

- **Lie Factor** = (size of effect in graphic) / (size of effect in data). Target ≈ 1.0
- Bar charts start at zero — always
- Time-series with money use deflated/standardized units, not nominal dollars
- Show sufficient context — never cherry-pick a flattering date range
- Violation: A y-axis starting at 95% to make a 2% change look dramatic

### 3. Chartjunk Elimination (Tufte)

**Remove all non-informative visual elements.**

- No 3D effects — they distort spatial perception of values
- No decorative backgrounds or images behind data
- Gridlines only when needed to read specific values; use light, dashed lines
- No moiré vibration patterns (hatching, heavy textures)
- Violation: A pie chart with 3D perspective, exploded slices, and gradient fills

### 4. Small Multiples (Tufte)

**Repeat the same chart structure across categories instead of overlaying.**

When comparing 4+ series, side-by-side small multiples are easier to read than a single chart with overlapping lines or stacked segments. Keep axes consistent across panels.

- Use for: time-series by region, distributions by cohort, trends by category
- Violation: 8 lines on one chart that requires a legend to decode

### 5. Audience-First Design (Nussbaumer Knaflic)

**Let the message choose the chart, not the other way around.**

- Start with: "What question does this answer for the audience?"
- Limit to 2-3 concepts per chart — cognitive load kills comprehension
- Highlight the insight: accent color for the key finding, grey everything else
- A chart the audience can't read in 5 seconds needs redesigning
- Violation: A scatter plot with 12 color-coded series and no annotation

### 6. Functional Aesthetics (Cairo)

**Design must be beautiful AND functional — beauty without function is decoration.**

- Aesthetics serve comprehension: clean alignment, balanced white space, intentional typography
- Visual hierarchy guides the eye: title → insight → supporting data
- Don't sacrifice clarity for style; don't sacrifice style for laziness

### 7. SUCCESS Framework (Hichert/IBCS)

**The International Business Communication Standards — the closest thing to an industry standard for business charts and dashboards.**

Synthesizes Tufte, Few, Zelazny, and Minto into seven actionable rules:

| Rule | Meaning | Practice |
|------|---------|----------|
| **S**ay | Convey a message | Lead with the insight in the title, not a description |
| **U**nify | Semantic notation | Same meaning → same visual encoding everywhere |
| **C**ondense | Information density | Pack more signal into less space; sparklines, small multiples |
| **C**heck | Visual integrity | Proportional scales, no truncation, no distortion |
| **E**xpress | Proper visualization | Match chart type to data relationship (see matrix below) |
| **S**implify | Avoid clutter | Remove chartjunk, minimize non-data elements |
| **S**tructure | Organize content | Logical grouping, consistent layout across a report |

> **Note:** IBCS is especially relevant for consulting deliverables, where chart-heavy reports benefit from consistent notation and message-first design. See [ibcs.com](https://www.ibcs.com/) for the full standard.

---

## Chart Selection Matrix

Match the **data question** to the chart type. When in doubt, default to bar or line — they have the highest reader familiarity and lowest cognitive load.

| Data Question | Best Charts | Also Works | Avoid |
|---|---|---|---|
| **Compare** values across categories | Bar (horizontal), dot plot | Lollipop | Pie (>5 categories) |
| **Rank** items by value | Sorted bar | Slope chart (for rank change) | Unsorted bars |
| **Show parts** of a whole | Stacked bar, treemap | Donut (≤5 slices) | Pie (>5), 3D pie |
| **Track change** over time | Line | Area (if stacking) | Bar (for continuous time) |
| **Show distribution** | Histogram, box plot | Violin, strip/jitter | Pie |
| **Reveal correlation** | Scatter, bubble | Heatmap (matrix) | Line (implies causation) |
| **Compare across groups + time** | Small multiples | Grouped bar | Spaghetti chart |
| **Show geographic patterns** | Choropleth, dot map | Cartogram | Rainbow color scales |
| **Highlight a single number** | Big number + sparkline | Gauge | Pie with one slice highlighted |

### Quick Decision Flow

```
What are you showing?
├── One number → Big number + trend sparkline
├── Category comparison → Bar chart (sorted if ranking)
├── Parts of a whole → Stacked bar (or donut if ≤5)
├── Change over time → Line chart
├── Relationship between variables → Scatter plot
├── Distribution → Histogram or box plot
└── Multiple series, same structure → Small multiples
```

---

## Design Checklist

Apply before finalizing any chart:

- [ ] **Purpose**: What question does this answer? (Write it as the chart title)
- [ ] **Chart type**: Does it match the data relationship? (Check matrix above)
- [ ] **Data-ink**: Can anything be removed without losing meaning?
- [ ] **Labels**: Axes, title, and data source all present?
- [ ] **Direct labeling**: Can data points be labeled directly instead of using a legend?
- [ ] **Color**: Is color encoding meaning, not decorating?
- [ ] **Highlight**: Is the key insight visually prominent? (Accent color + grey)
- [ ] **Accessibility**: Does it work without color? (Pattern, position, or labels)
- [ ] **Contrast**: WCAG AA — 4.5:1 for text, 3:1 for large elements
- [ ] **Context**: Is enough data shown to avoid misleading the reader?
- [ ] **Message**: Would a non-expert understand the takeaway in 5 seconds?

---

## Anti-Patterns

| Don't | Why |
|-------|-----|
| 3D charts | Distorts perception of values; back bars appear smaller |
| Truncated y-axis (without clear notation) | Exaggerates small changes; violates graphical integrity |
| Dual y-axes with mismatched scales | Creates false visual correlation between unrelated series |
| Pie charts with 6+ slices | Humans can't accurately compare angles past 5 segments |
| Rainbow color schemes | No natural ordering; hostile to colorblind readers |
| Decorative backgrounds behind data | Reduces contrast and adds visual noise |
| Legend when direct labeling works | Forces reader to bounce between legend and data |
| Nominal dollars in time-series | Conflates inflation with real change; use constant dollars |
| "Chart title: Sales by Region" | Describes the chart, doesn't convey a message — use "East region leads with 40% share" instead |
| Same color for different meanings | Violates IBCS Unify rule — consistent encoding matters across a deck |

---

## Accessibility Standards

- **Color is never the sole differentiator** — pair with pattern, position, shape, or direct labels
- **Test with colorblind simulation** — use Sim Daltonism (macOS) or similar tools
- **Direct label > legend** — reduces cognitive load and works better for screen readers
- **Provide text summary** — state the key finding in words alongside the chart
- **WCAG AA contrast** — 4.5:1 for normal text, 3:1 for large text and graphical elements
- **Avoid red/green as a pair** — most common colorblindness (protanopia/deuteranopia)

---

## Integration with Other Skills

| For... | Use... |
|--------|--------|
| Building the chart (Vega-Lite specs) | `vega-lite-charts` |
| Brand colors and typography | `brand-guidelines` |
| Embedding charts in slides | `marp-formatting` |
| Embedding charts in documents | `typst-formatting` |

### Workflow

```
data-viz-advisor (select chart type, apply design principles)
    → vega-lite-charts (build the spec, render to SVG)
        → marp-formatting / typst-formatting (embed in deliverable)
```

---

## Sources & Further Reading

- Tufte, E. — *The Visual Display of Quantitative Information* (1983)
- Few, S. — *Show Me the Numbers* (2012)
- Cairo, A. — *The Functional Art* (2012), *The Truthful Art* (2016)
- Nussbaumer Knaflic, C. — *Storytelling with Data* (2015)
- Hichert, R. & Faisst, J. — *International Business Communication Standards* (IBCS v1.2)
- IBCS Association — [ibcs.com](https://www.ibcs.com/)
