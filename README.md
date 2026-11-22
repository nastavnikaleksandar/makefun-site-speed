[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/nastavnikaleksandar/limited/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/nastavnikaleksandar/limited/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

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

The goal is exact output equivalence, not changing the generated site.

## Runtime

The challenge specifies Node.js 22. The entry is dependency-free and uses only Node.js built-ins plus the vendored challenge source.

## Local validation

The current working version has passed the three published practice cases with exact output matching. It was also checked against the reference implementation with randomized Markdown inputs and word-count equivalence tests.

On the development machine, repeated local runs measured approximately 0.85–0.90 seconds wall time versus approximately 1.33–1.34 seconds for the unmodified baseline (about 33–36% lower wall time). These are local measurements, not a prediction of the final server benchmark or leaderboard position.

## Source and licences

The challenge reference source and upstream attribution are documented in:

- `SOURCE.txt`
- `vendor/makefun-site/LICENSE`
- `vendor/makefun-site/NOTICE`

The root `LICENSE` is retained from the challenge kit. Please preserve all licence and notice files when redistributing this project.

## Challenge

Static Site Generator Speed Challenge  
https://make.fun/bounty/site-generator-speed-01-run-20261122

[executed on device: aleksandar-System-Product-Name (bcb0ae1d-a24f-4ff3-ae8f-5e3532f78819)]