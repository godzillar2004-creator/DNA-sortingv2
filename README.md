# DNA Profiles — BST Case Bench

A DNA profile matching system built on a binary search tree. Profiles are keyed
by name, stored as nodes in a BST, and compared against two unknown DNA
sequences using STR (Short Tandem Repeat) occurrence counts to flag potential
matches.

This repo contains two things:

- **`src/`** — the original Java implementation of the BST (insert, recursive
  search, STR matching, level-order traversal, and node deletion with all
  three removal cases).
- **`dna-profiles-lab.html`** — a self-contained, single-file web app that
  ports that exact logic to JavaScript and wraps it in a visual, interactive
  interface. No build step, no dependencies — open it in any browser.

## Try it

Open [`dna-profiles-lab.html`](./dna-profiles-lab.html) directly in a browser,
or, if GitHub Pages is enabled for this repo, visit the live link in the
**About** section on the right.

## What it does

- **Load a case file** — upload a `.in` file, paste one in, or load the
  bundled sample case
- **Visualize the tree** — every profile renders as a node in the BST; click
  one to see its STR breakdown
- **Run STR matching** — flags each profile as a person of interest if enough
  of their STRs match the combined occurrence counts across both unknown
  sequences
- **Search** — traces the exact comparison path down the tree for a given
  name, the same way the recursive `searchByName` does
- **Remove / clean up** — delete a single profile (exercising all three BST
  deletion cases: leaf, one child, two children) or clear every unmarked
  profile in one pass
- **Console log** — a running feed of what each operation just did, echoing
  the interactive `Driver.java` test harness this was originally built around

## How the matching works

Each profile has a list of STRs (short DNA substrings) with an expected
occurrence count. For a profile to be flagged as a person of interest, the
combined number of times each STR appears across *both* unknown sequences
must match its expected count for at least half of that profile's STRs
(rounded up).

## Input file format

```
<unknown sequence 1>
<unknown sequence 2>
<number of profiles>
<first name> <last name> <number of STRs>
<STR> <expected occurrences>
...
```

Repeated for each profile. See `input1.in`–`input6.in` for examples.

## Tech

- Java (original BST implementation)
- Vanilla HTML/CSS/JS (no frameworks, no build tools) for the web app

## Background

This started as a binary search tree assignment and grew into a standalone
tool — same core algorithm, now with a real interface around it.
