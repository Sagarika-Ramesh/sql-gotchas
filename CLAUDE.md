# SQL Gotchas, Illustrated — how to add a gotcha

Live site: https://sagarika-ramesh.github.io/sql-gotchas/
Repo: https://github.com/Sagarika-Ramesh/sql-gotchas (GitHub Pages, `main` branch, root folder)

This is a **separate site** from the SQL Cheat Sheets and the ML Interview Prep site, with its own
look. Don't mix their styles. When Sagarika gives a new SQL trap, pitfall or "gotcha", **append** it
here in exactly the style below. Don't redesign.

## File layout

```
index.html    the whole site: one long illustrated article (HTML, CSS and a small script inline)
README.md     optional
```

There are no assets or build step. Edit `index.html` directly.

## Page structure (top to bottom)

1. **Hero**: `.eyebrow` (handwritten), `h1` "SQL Gotchas, <span class="squiggle">Illustrated</span>",
   `.lede`, then `ul.toc` pill links to every section.
2. **Sections**, each `<section id="...">` with a `.kicker` (handwritten label), an `h2`, prose, then
   content. Current order:
   `#rows-vs-days` LEAD vs self-join · `#self-joins` · `#run-order` (logical query order diagram) ·
   `#joins` Join traps (J1–J5) · `#aggregates` (A1–A8) · `#nulls` (N1–N3) ·
   `#strings-dates` (S1–S4) · `#subqueries` (Q1–Q3) · `#performance` (P1–P3) ·
   `#before` Before you write a line · `#postgres` Postgres pocket tools · `#cheatsheet`.
3. **Trap blocks** inside a section: `div.trap` with
   `<h3><span class="n">J6</span>Title</h3>`, an optional `dl.qa` (`Ask` / `Trap` rows), then code
   figures, then an optional 👉 callout. Number with the section's prefix and the next free number
   (J = joins, A = aggregates and windows, N = NULL, S = strings/dates/types, Q = subqueries,
   P = performance). Add a new section (with a new prefix and a `ul.toc` pill) only if nothing fits.
4. **Cheat sheet** (`#cheatsheet`): `.cheats` grid of `.cheat` cards (`<b>Rule</b>` + one sentence).
   Add a card when the new gotcha is a rule worth remembering.
5. `footer` with "Built from my SQL notes doc..." and `<span class="sign">Sagarika</span>`.

## Building blocks (copy the existing markup)

- **Code**: `figure.code > div.code-inner > div.code-head` with a tag, a `.label` and a copy button,
  then `<pre><code class="sql">...</code></pre>`. Tags: `tag bad` = **Trap** (wrong query),
  `tag good` = **Fix** / **Pattern** / **Example**, `tag note` = **Choose** / **Try**.
  Write `<` as `&lt;` inside code. The inline script highlights SQL automatically.
- **Callout**: `div.callout` with `<span class="hand">👉</span><p>...</p>`.
- **Diagram**: `figure.diagram > div.diagram-inner > svg` + `figcaption` (handwritten, white).
  Hand-drawn look: shapes inside `<g class="rough">` (uses the `#rough` SVG filter), arrows with
  `marker-end="url(#arrow)"`, fills from the tokens `f-blue` / `f-purple` / `f-green` / `f-amber` /
  `f-card` (all purple-pink tones now), text classes `t-big` / `t-mid` / `t-small` / `t-mono`,
  `t-red` / `t-green` for bad/good. Every diagram needs a real `aria-label`.
- **Truth / comparison tables**: `.tbl-wrap > table` with `.pill.yes` / `.pill.no` / `.pill.unk`.

## Visual rules

- Light and dark themes both work (tokens on `:root`, redefined for dark). Purple-pink palette:
  frame gradient `#f0a0d0 → #b866cc → #6438a8`, lavender/violet/rose/orchid diagram fills.
- Fonts: **Dancing Script** for the title and section `h2`s (signature look), **Caveat** for
  eyebrow, kickers, captions, trap numbers and diagram labels, **Source Serif 4** body,
  **Bricolage Grotesque** for `h3`s and labels, **JetBrains Mono** for code.
- The main title "SQL Gotchas, Illustrated" is **white** in dark mode (`color: var(--fg)`), near-black
  in light mode. The eyebrow and headings keep their colours.
- Must work at 375px wide with no page-level horizontal scroll.

## Writing rules

- PostgreSQL syntax. Show the **Trap** query, then the **Fix**, and say in one sentence why it fails.
- Run every query against a real Postgres before adding it (a local server works; use
  `CREATE TEMP TABLE` so nothing persists). Never invent outputs.
- Plain, short sentences. Don't copy text or visuals from other cheat-sheet sites; use original
  examples.
- Don't add a link to the cheat-sheets site or "original examples" notes; Sagarika removed those.

## Steps

1. `git clone https://github.com/Sagarika-Ramesh/sql-gotchas.git` (or `git pull`).
2. Add the trap block (and a cheat card if useful) in `index.html`.
3. Check locally with `python3 -m http.server`: light and dark, desktop and 375px.
4. Commit and push to `main`; Pages rebuilds in about a minute. Check the live URL.
