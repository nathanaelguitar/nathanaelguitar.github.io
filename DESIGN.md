# Design

Recorded from the built page, not from intention. `index.html` is the only artifact;
everything below is in its `<style>` block.

## The world

A seamless cyclorama. The page is one continuous light field descending from blackout to
full day, and each project is a numbered lighting cue on it. The conceit is load-bearing,
not decorative: cue numbers are permalinks and the nav, real metrics are channel levels,
and a private repository is an **unpatched channel** — a dashed jack with no `href`, which
is how the page shows unlinkable work without ever producing a 404.

Refused deliberately: the dark-terminal developer portfolio, and its cream-and-serif
editorial opposite.

## Color

Drenched. The surface *is* the color; there is no neutral ground anywhere on the page.

Thirteen **holds** (a cue's steady state, a flat color) alternate with twelve **fades**
(the light moving between cues, a gradient). This mirrors how lighting cues actually
behave — a fade happens, then the state holds — and it is also what makes the type legible:
dense reading always happens on a hold or on the settled end of a fade.

| Cue | Hold | Ink | Dim |
|---|---|---|---|
| 00 | `#050506` | white | `#8FA0D8` |
| 10 | `#060B22` | white | `#8FA0D8` |
| 20 | `#071640` | white | `#A8B8F0` |
| 30 | `#0A2060` | white | `#A8B8F0` |
| 40 | `#142A86` | white | `#B6C4FF` |
| 50 | `#2A1E92` | white | `#B6C4FF` |
| 60 | `#4A1F9E` | white | `#D9C4FF` |
| 70 | `#6A1FA8` | white | `#D9C4FF` |
| 80 | `#8B2596` | white | `#F2CCE8` |
| 90 | `#A32C7A` | white | `#F2CCE8` |
| 100 | `#D9518F` | `#240A1B` | `#2E0A1F` |
| 110 | `#FFD7E6` | `#240A1B` | `#6E2A50` |
| 120 | `#FFFFFF` | `#240A1B` | `#6E2A50` |

Pure palette hues — cobalt `#0A2BFF`, rose-gather `#D24BFF`, rose `#FF7BAE` — appear only
as the **peak of a fade**, never as a hold. Two rules govern them:

1. **The peak sits at 40–45% of the band, not the middle.** The pure hue floods the top of
   the viewport at full strength, while the type below it sits on a ground that still
   clears AA. Peaking at 62–70% put the cue address at 3.65:1 and failed.
2. **Large type only on the peak.** Body copy never sits there.

**The ink flip is the page's one structural event.** At cue 100 the ground crosses the
luminance threshold where white text stops working, and the whole page inverts to plum
`#240A1B` — light-on-dark becomes dark-on-light. This is daybreak, and it is the reason the
descent has a middle.

Secondary text is tinted from the band's own hue (`--dim`), never gray.

## Type

- **Display** — Saira Stencil One, **self-hosted** (`fonts/saira-stencil-one-latin.woff2`,
  13.5 KB). A CDN failure must never drop the focal element to a system face; the stack
  falls back to Saira, never to Impact.
- **Body** — Saira, weight 300, measure capped at `68ch`.
- **Measurement** — JetBrains Mono with tabular numerals, used *only* for levels, values,
  addresses, and schedules. Never as a costume for "technical".

Display is capped at `6rem`. Headings balance; more space sits above a heading than below.

## Components

- **`.open` / `.hold`** — every cue is a fade band plus a steady band. `.open--full` (68vh)
  is spent only on cues carrying a real light event: 10, 20, 80, 100, 120. The rest run a
  short 38vh band so the scroll does not pay for thirteen identical empty screens.
- **`.addr`** — the cue's permalink, `<a href="#cue-N">`, mirrored in the rail. Wayfinding,
  not an eyebrow.
- **`.rail`** — fixed cue stack, desktop. Tick widens by `scaleX` on the current cue; its
  ink follows the band it stands in via an `on-day` class set from scroll position.
- **`.scrub`** — mobile. A real horizontal strip of cue anchors, not a progress bar.
- **`.levels` / `.track` / `.fill`** — channel meters. The track is a 15%-opacity ground;
  the fill is `scaleX(var(--v))` where `--v` is the literal proportion. Base rows sit at
  42% opacity, adapter rows at 100%. Every meter prints its exact number beside it.
- **`.jack`** — a patch point. `<a>` when the repo is public; `<span class="jack--dark">`
  with a dashed border and a cap icon when it is private. Opacity stays at .85 so the label
  never falls below AA.
- **`.sched`** — plot tables. Winning rows carry ink weight, not a glyph.
- **`.note`** — caveats, with a vertical `NOTE` marker. These sit *next to* the numbers they
  qualify, never below the fold. This is the page's credibility mechanism.
- **`.rig`** — authored SVG schematics in plot grammar: 1.4 stroke, `currentColor`, channel
  numbers in circles, dashed strokes for optional or inferred paths.
- **`.grain`** — fixed fractal-noise overlay at `z-index:0`, **below** all type. It sat
  above at `z-index:80` with `mix-blend-mode:overlay`, silently compositing over every
  measured contrast ratio.

## Motion

One authored moment, in two registers of the same grammar:

- **Body content travels** — `translateY(1.6rem)` + `blur(6px)` → settled, 0.9s
  exponential ease-out, staggered by `.d1` / `.d2`.
- **Cue titles come up on the dimmer** — no translation at all, `blur(14px)` → sharp over
  1.15s. A lamp reaching its level, not a card sliding in.

Meters fill once on entry. Everything is `IntersectionObserver`-driven and unobserved after
firing. `prefers-reduced-motion: reduce` renders every final state immediately.

No property that triggers layout is ever animated — bars and ticks use `scaleX`, the
contact rows use `translateX`.

## Accessibility

WCAG AA is an obligation, and it was verified against **measured** grounds rather than
assumed: every solid hold, plus each fade sampled at the real position of the address and
title within its band. Zero failures; the tightest case is the cue title on the
rose-gather peak at 3.96:1 against a 3:1 large-text threshold.

Semantic landmarks, `aria-labelledby` on every section, heading order without skips, real
`<table>` markup with `scope` (the confusion matrix included), keyboard-operable
navigation, visible focus, a skip link, and full legibility with JavaScript disabled —
the reveal styles are scoped under `.js`, which only exists once the script runs.

## Constraints this world must keep

- No dead links. Private work is shown as unpatched, never hyperlinked.
- Every metric traces to a file in the repository it describes; the caveat sits beside the
  number. Do not compress or relocate `.note` content to save space.
- Single self-contained file, no build step, no framework. 15.7 KB gzipped before fonts.
