[![make.fun · news-image-20261124](https://make.fun/badge/news-image-20261124.svg)](https://make.fun/bounty/news-image-20261124?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261124)
[![rank](https://make.fun/badge/news-image-20261124/sheeran154/makefun-news-image-20261124/rank.svg)](https://make.fun/bounty/news-image-20261124/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261124)
[![reward](https://make.fun/badge/news-image-20261124/sheeran154/makefun-news-image-20261124/reward.svg)](https://make.fun/bounty/news-image-20261124?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261124)

# The World in One Page — 24 November 2026

A make.fun `news-image-20261124` entry: one program that draws a newspaper
front page summing up Tuesday 24 November 2026 in a single image, and writes
it to `/output/entry.png`.

## The day, in five stories

1. **World Court — The Hague.** The International Court of Justice rules
   Myanmar committed genocide against the Rohingya — the first ruling of its
   kind against a state over the minority's persecution.
2. **Tech — Markets.** Nvidia reinstates Jensen Huang as chief executive less
   than two weeks after he resigned; the move follows pressure from
   President Trump.
3. **Security.** Russia warns it could carry out a "preventive" nuclear
   strike; NATO vows to defend space amid reports of a nuclear-armed
   Russian satellite.
4. **Middle East.** Houthi fighters strike Riyadh's tallest tower for the
   second time in five days, injuring 11 people, and close in on Aden.
5. **Health.** The United States loses its measles elimination status after
   more than 25 years.

Plus a markets strip (S&P 500 −0.95%, Brent $87.51 +0.96%, FTSE 100 −0.13%)
and a sport line (Senegal reinstated as 2025 Africa Cup of Nations
champions).

Sources checked on 24–25 November 2026: Just Security's Early Edition,
Principia's daily brief, One Turn's world brief, and The Global Eye.

## How it works

`main.ts` is a pure Node 22 program — standard library only, no network,
no font files, fully deterministic. It:

- paints a 1024×1024 RGB framebuffer (newsprint background, navy masthead,
  hairline rules, one colour-coded pictogram per story),
- renders every letter with an embedded 5×7 bitmap font (upper/lowercase,
  digits, punctuation), so the text stays pixel-crisp at full size,
- encodes the framebuffer as a PNG by hand (CRC32 + `node:zlib` deflate),
  and writes it to `$MAKEFUN_OUTPUT_DIR/entry.png` (default `/output`).

The judge has no news feed, so the page is built to be self-explanatory:
the headlines and decks alone tell the day's news, and each story carries
one small geometric icon (scales, chip, satellite, tower, cross) as a
visual anchor.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
# -> out/entry.png (1024x1024, ~18 KB, well under the 1 MiB limit)
```

## License

MIT — see `LICENSE`.
