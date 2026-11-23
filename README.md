[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/nastavnikaleksandar/makefun-site-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/nastavnikaleksandar/makefun-site-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

# makefun-site-speed

A performance-focused entry for the make.fun **Static Site Generator Speed Challenge**.

## What this entry does

This project preserves the challenge's required interface and output format:

- `main.ts` reads the supplied cases and writes the answer array.
- `solve.js` exports `run(input)`.
- `vendor/makefun-site/` contains the challenge reference implementation, with its accompanying licence and notices.

The implementation applies two targeted optimizations to the reference code:

1. Markdown inline rendering accumulates plain-text chunks and escapes them in batches, with a fast path for ordinary text.
2. Word counting uses an allocation-free scan with the ECMAScript whitespace rules instead of allocating a regular-expression match array.

The driver adds a third optimization: it serializes and writes each case's answer as it is produced, instead of retaining all answer objects and building one large JSON string. It uses single-element array serialization to preserve JSON array element semantics, including `toJSON` keys and undefined values.

The goal is exact output equivalence, not changing the generated site.

## Runtime

The challenge specifies Node.js 22. The entry is dependency-free and uses only Node.js built-ins plus the vendored challenge source.

## Local validation

The current version passed all three published practice cases with exact output matching. The official local grader ran it twice and reproduced the same result hash.

In paired local runs on Node.js 22.23.5, compared with the first submitted version on the same machine, streaming answer serialization reduced median CPU time and peak memory. These are local measurements, not a prediction of the final server benchmark or leaderboard position.

## Source and licences

The challenge reference source and upstream attribution are documented in:

- `SOURCE.txt`
- `vendor/makefun-site/LICENSE`
- `vendor/makefun-site/NOTICE`

The root `LICENSE` is retained from the challenge kit. Please preserve all licence and notice files when redistributing this project.

## Challenge

Static Site Generator Speed Challenge  
https://make.fun/bounty/site-generator-speed-01-run-20261122
