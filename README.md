# makefun-site-fast

[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/banglento/makefun-site-fast/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/banglento/makefun-site-fast/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

A faster drop-in for makefun-site 1.0.0, built for the
[Build a static site faster](https://make.fun/bounty/site-generator-speed-01-run-20261122)
competition on make.fun.

`solve.js` is an independent, dependency-free implementation of makefun-site's
own contract: its front matter, template dialect, Markdown subset, slug rule
and build report, byte for byte. `run(input)` returns the output tree
makefun-site 1.0.0's build returns for one case's site. `main.ts` is the
driver the harness runs: it reads every case from `/input/cases.json` and
writes `/output/answers.json`.

Speed comes from doing less work, not from different answers: cached slugs
with a plain ASCII fast path, Markdown lexed by character dispatch instead of
a regex per line, inline rendering straight into an array, a single-scan word
count, and template rendering appended into one shared output array.

## Layout

- `solve.js` — the entry: `run(input)` answers one case.
- `main.ts` — the harness driver.
- `LICENSE` — MIT.

## Local check

Grade on the practice set with the kit (from the kit directory):

```
node cli/makefun.mjs grade-local --kit . --bot /path/to/makefun-site-fast --driver docker
```
