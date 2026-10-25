# TYPECHECK.md — GATE T

Reel: `pinned-docs-pitch`  |  Checked: 2026-10-24T21:43  |  Overall: PASS  |  Beats checked: 20  |  FAILs: 0

Spec: `skills/make/kerning/reference/type-spec.md` §8.  Floor: 1.9% frame-height.  Contrast: 4.5:1 WCAG.  Kern threshold: 3.5× expected advance.  Wordy budget: 2 elements.

| beat | lane | polarity | worst finding | status | fix |
|------|------|----------|---------------|--------|-----|
| BIDEA | bookend | light | min-size §8.1: min text-run height 71px >= floor 41px | PASS | — |
| BDEFS | bookend | dark | no-wordy-card §8.5: no prose payload found | PASS | — |
| B00 | manim | light | min-size §8.1: min text-run height 88px >= floor 41px | PASS | — |
| B01 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px (individual-char fallback at 2×) | PASS | — |
| B02 | card | light | no-wordy-card §8.5: no prose payload found | PASS | — |
| B03 | manim | light | min-size §8.1: min text-run height 54px >= floor 41px | PASS | — |
| B04 | manim | light | min-size §8.1: min text-run height 103px >= floor 41px | PASS | — |
| B05 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px (individual-char fallback at 2×) | PASS | — |
| B06 | manim | light | min-size §8.1: min text-run height 88px >= floor 41px | PASS | — |
| B07 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px (individual-char fallback at 2×) | PASS | — |
| B08 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px (individual-char fallback at 2×) | PASS | — |
| B09 | manim | light | min-size §8.1: min text-run height 89px >= floor 41px | PASS | — |
| B10 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px (individual-char fallback at 2×) | PASS | — |
| B11 | manim | light | min-size §8.1: min text-run height 681px >= floor 41px | PASS | — |
| B12 | manim | light | min-size §8.1: min text-run height 389px >= floor 41px | PASS | — |
| B13 | card | light | no-wordy-card §8.5: no prose payload found | PASS | — |
| B14 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px (individual-char fallback at 2×) | PASS | — |
| B15 | manim | light | min-size §8.1: min text-run height 90px >= floor 41px | PASS | — |
| B16 | manim | light | min-size §8.1: min text-run height 53px >= floor 41px | PASS | — |
| BOUT | manim | light | min-size §8.1: min text-run height 90px >= floor 41px | PASS | — |

---

## Failures requiring action before cut

*None — GATE T PASS.*
---

## Check summary

| Check | Beats checked | FAILs |
|-------|---------------|-------|
| no-wordy-card §8.5 | 3 | 0 |
| min-size §8.1 | 20 | 0 |
| overflow §8.2 | 20 | 0 |
| contrast §8.3 | 20 | 0 |
| contrast-local §8.3b | 20 | 0 |
| bbox-overlap §8.6b | 20 | 0 |
| card-clip §8.13 | 20 | 0 |
| kerning §8.4 | 16 | 0 |
| redundancy §8.10 (advisory) | 2 | 0 (advisory — no exit effect) |

---

*GATE T: any FAIL blocks `./art run` and `./art final`. Fix the flagged beats and re-run `scripts/type_check.py` until green.*
