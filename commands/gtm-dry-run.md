---
name: gtm-dry-run
description: Shows what would run, in what order, at what cost. Executes nothing.
---

# /gtm-dry-run [account-slug]

## Output

1. Which swarm applies, and why
2. The wave graph, with agents per wave
3. Which agents will be skipped and the reason — tier, missing connector,
   private company, touch cap reached
4. Estimated cost per wave and total, against the ceiling in
   `spec/boundaries.md`
5. Which spec files each wave reads, and whether any have expired
6. Where the human gates fall

## Why this exists

This runs on a schedule, on the user's own API key. Someone should be able to
see what a Monday costs before the first Monday.

## Rule

Execute nothing. No API calls beyond what is needed to read local files.
