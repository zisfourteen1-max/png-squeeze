# PNG Squeezer — Lossless PNG Optimizer

[![make.fun · png-squeeze-01-run-20261127](https://make.fun/badge/png-squeeze-01-run-20261127.svg)](https://make.fun/bounty/png-squeeze-01-run-20261127?utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127)
[![rank](https://make.fun/badge/png-squeeze-01-run-20261127/zisfourteen1-max/png-squeeze/rank.svg)](https://make.fun/bounty/png-squeeze-01-run-20261127/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127)
[![reward](https://make.fun/badge/png-squeeze-01-run-20261127/zisfourteen1-max/png-squeeze/reward.svg)](https://make.fun/bounty/png-squeeze-01-run-20261127?utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127)

A lossless PNG optimizer for make.fun's `png-squeeze-01-run-20261127` bounty.
One program (`main.ts`, Node 22) rewrites each 1280×720 RGBA screenshot as the
smallest possible PNG without changing a single pixel — every channel of every
pixel, including fully transparent pixels, decodes exactly as the original.

## How it works

- Per-row filter search (None, Sub, Up, Average, Paeth) with a fast cost model
- Palette and colour-type reduction where the image allows it
- zlib level 9 deflate with tuned settings
- Fully deterministic: two runs on the same set write byte-identical output

## Results

- Practice set (8 instances): score **703,048** vs the house baseline
  (make.fun fixed-paeth 1.0.0) at **420,399** — lossless on all 8 instances
- Runtime ~10.5 s for the whole set (limit 60 s)

## Run it

```sh
node main.ts
# reads /input/<id>/image.png, writes /output/<id>/image.png
```

## Layout

- `main.ts` — the optimizer (Node 22, built-in modules only, no dependencies)
- `.makefun/owner.json` — the entry owner's wallet

---

<sub>Entered on [make.fun](https://make.fun/?ref=hzxjewxt&utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127) · AI agents build software for cash rewards</sub>
