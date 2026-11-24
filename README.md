# The World in One Day — 24 November 2026

[![news-image-20261124](https://img.shields.io/badge/make.fun-news--image--20261124-gold)](https://make.fun)
[![repo](https://img.shields.io/badge/repo-badboy0771%2Fnews--image--20261124-blue)](https://github.com/badboy0771/news-image-20261124)

A single 1024x1024 image summing up Tuesday 24 November 2026 in the format of a
world atlas in gold on navy: a numbered world map on top, eight story cards
below. The day's eight stories are the collapse of the COP31 climate talks in
Antalya with no fossil-fuel deal, the Wall Street sell-off after the US
midterms that wiped out about $1 trillion in a day, the factory fire in
Cikande (Banten) that killed at least 24 people with around 30 still missing,
the Russian strikes on the Kyiv region, the India–Nepal pact signed by Modi
and Shah with eight deals and a Rs 15,000 crore package, the Seoul reshuffle
naming a new foreign minister and intel chief, Dhaka vowing to arrest
ex-PM Hasina on her return, and the first India–New Zealand Test ending in a
draw with New Zealand 239 for 5.

## How it works

`main.ts` is a single self-contained Node program (stdlib only: `node:zlib`,
`node:fs`, `node:path`). It rasterizes everything from scratch: a vertical
navy gradient background, an equirectangular world map built from hand-drawn
continent polygons in gold with dark-gold outlines, a 30-degree graticule,
eight numbered red pins placed at the stories' locations, and eight story
cards with a red number badge, a cream headline and two muted sub-lines. All
text is drawn with a hand-built 5x7 bitmap font (uppercase A–Z, digits and
punctuation, no external font files). The pixel buffer is encoded to PNG by a
hand-written encoder (CRC32, IHDR/IDAT/IEND, `deflateSync` level 9, filter
byte 0 per row). There is no network access, no clock and no randomness, so
every run produces a byte-identical `entry.png`.

## Local check

```sh
MAKEFUN_OUTPUT_DIR=out node main.ts
```

Exits 0 and writes `out/entry.png` (1024x1024 RGBA, under 1 MiB). Running it
again from any other working directory produces the same SHA-256.

## License

MIT — see [LICENSE](LICENSE).
