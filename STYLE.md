# rd icon style guide (draft 1)

`rd` is the icon library made for rdicons. This is the spec every icon is drawn and checked against.

## Principles

1. **Real strokes, never outlined shapes.** Every icon is made of strokes, so the stroke-width control on the website, in the Figma plugin and in the React package works.
2. **Light by default.** Default stroke is **1.5**, not 2. Users make it bolder if they want.
3. **Soft, not round-for-the-sake-of-it.** Round caps and joins, generous corner radii, curves that lean toward a squircle.
4. **One signature, applied everywhere.** The set must be recognizable from a few icons. Two candidate signatures are drawn in `variants` and one will be chosen.
5. **Consistency beats detail.** Same radii, same gaps, same optical weight in every icon.

## Grid

| | |
|---|---|
| Canvas | 24 × 24 |
| Live area | 20 × 20 (2 px margin all around). Round or very wide shapes may touch 22 |
| Stroke | 1.5, `stroke-linecap="round"`, `stroke-linejoin="round"`, `fill="none"` |
| Colour | `currentColor` only. No hard-coded colours, no opacity tricks |
| Gaps | Minimum 2 px between separate strokes, so nothing clots at 16 px |
| Sizes tested | 16, 20, 24, 32, 48 |

## Corner radii

| Variant | Large containers (cards, files, windows) | Small shapes (door, tab, knob) |
|---|---|---|
| A, Open corner | 3 | 1.5 |
| B, Soft | 4.5 to 5 | 2 |

## Signatures under test

- **A, Open corner.** Closed shapes are not fully closed: a small gap (about 3 px) opens at the **top-right**, centred on the 45° point. Icons made only of open lines (download, code, sliders) already follow the rule. It echoes the brackets in the rdicons logo.
- **B, Soft.** No gaps. All shapes are closed and use the larger radii. Recognizable by softness alone.

A and B can also be combined later (open corner with soft radii).

## Rules for every icon

- Built from the fewest elements that read clearly (usually 1 to 4).
- No stroke is shorter than 1.5 px.
- Align horizontal and vertical edges to the half pixel so 1.5 px strokes stay crisp (use x.5 / x.0 coordinates consistently).
- Names are lowercase-kebab-case English nouns, using the most common word (`home` is also searchable as `house`).
- Every icon is checked by script: attributes, grid, no stray fills, no colour.


