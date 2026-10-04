---
name: persona-critique
description: Converts the persona's reaction into specific, actionable notes.
cadence: on-demand
permission: autonomous
model: cheap
depends_on: [buyer-persona]
reversible: true
reads: []
writes: []
requires: []
---

# Persona critique

## Purpose

The persona reacts. This agent turns that reaction into instructions a rewrite
can act on.

## Procedure

1. Where did the reader stop, and what specifically caused it?
2. Which claims were unearned — asserted without evidence the reader would
   accept?
3. What did the message assume about the reader that was wrong?
4. What work is the reader being asked to do that the sender should have done?
5. Is the ask proportionate to the relationship? A meeting request on first
   contact usually is not.
6. What is the single highest-leverage change?

## Output

An ordered list, most important first. Each item states the problem and the
evidence from the persona's reaction, not a rewritten sentence.

## Rules

- Do not rewrite. Diagnosis and treatment are separate steps on purpose.
- Rank ruthlessly. Six equally weighted notes produce a message that has been
  edited six times and improved once.
- If the persona would not have read past the first line, the only note that
  matters is the first line.
