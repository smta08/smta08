# assets

Hand-written SVGs for the profile README. GitHub serves them directly, with no external image services.

| File | Used in |
|---|---|
| `hero.svg` | Top banner. The commit lines are real commits from lifeos and ApplyFlow. |
| `lifeos-architecture.svg` | 01 · LifeOS |
| `card-applyflow.svg`, `card-nutriguard.svg` | 02 · Also shipped |
| `stack-radar.svg` | 04 · Stack radar |

**Editing:** open any file in a text editor and change the `<text>` content. Colours are CSS variables in each file's `<style>` block (`--ink`, `--muted`, `--accent`…), with a dark-mode override under `@media (prefers-color-scheme: dark)`. Animations stop when the viewer has reduced motion turned on.

**Radar chips:** each chip is a `<rect>` plus a `<text>`. When you add one, give the rect a width of about `characters × 7.6 + 24` and move the following chips right.

Keep the `<title>` and the `alt` text in README.md in sync with what each image says, because screen readers and search only see the text.
