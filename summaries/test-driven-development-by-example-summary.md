---
title: Test-Driven Development By Example
created: 2026-07-14
tags: [testing, tdd, design, refactoring, software-craft]
source: Kent Beck, "Test-Driven Development: By Example" — Addison-Wesley, 2002, ISBN 0-321-14653-0
---

# Test-Driven Development By Example

> Write a failing test, make it pass with the smallest change, then remove
> duplication — repeat in minutes-long loops so you're never more than one step
> from working code.

## Context

Kent Beck's foundational book on TDD, taught through two worked examples (a
multi-currency `Money` class, then a small xUnit testing framework) and a
closing catalog of reusable patterns. The distilled method lives in **Part III**
and the **Mastering TDD** chapter; the examples exist to make it stick. TDD is
less a testing technique than an *analysis and design* technique that happens to
leave a test suite behind.

## Key points

- **Red → Green → Refactor** is the whole loop. Add one failing test (red), make
  it pass with the simplest possible change even if ugly (green), then remove
  duplication and clean the design (refactor) — running the suite at every step.
- **"Da roolz":** never write production code without a failing test first, and
  remove duplication only while the bar is green. Stay *never more than one change
  away from a green bar* (the mountaineer's three-points-of-contact rule).
- **Three gears to green** — *Obvious Implementation* (type the real code when
  it's small and certain), *Fake It* (return a constant, then generalize by
  killing the duplication between test and code), and *Triangulate* (add a second
  example to force the abstraction). Shift by confidence.
- **Duplication between test and code drives the design.** The engine of TDD
  isn't the assertion — it's removing the duplication the assertion exposes.
- **Control your step size deliberately:** tiny steps for traction when the
  problem is slippery, big strides when the road is clear. Mastery is *changing
  gears*, not always using one.

## Details

### Before coding: the Test List

Start every session with a checklist of the tests you expect to write — an
example per operation, the null/degenerate case of each new operation, and
anticipated refactorings. Implement them one at a time (ten broken tests is a
long way from green); when new cases surface, add them to the list rather than
chasing them (**Another Test**). Pick the next test with **One Step Test**: one
that teaches you something *and* that you're confident you can pass quickly.

### Writing the tests

- **Test First / Assert First** — write the test before the code, and build the
  test backward from the assertion (the answer you want) to the setup.
- **Isolated Tests** — order-independent, no shared mutable state; one broken
  test means one problem. Hard-to-isolate tests are a *design* smell.
- **Evident Data** — put expected value and its derivation in the test
  (`100 / 2 * (1 - 0.015)`, not a magic `49.25`) so a reader sees why it's right.
- **Test only what you wrote** — conditionals, loops, operations, polymorphism —
  not the language or third-party libraries (unless you distrust them, via a
  **Learning Test**).

### Bugs, and getting unstuck

- **Regression Test** — the first response to a reported defect is the smallest
  failing test that reproduces it.
- **Child Test** — a test too big to green? Shrink it to one broken piece, pass
  that, then reintroduce the big one.
- **Do Over / Break** — when lost, throw away the increment and restart from the
  tests; when tired, stop (fatigue hides itself). Leave a **Broken Test** as a
  bookmark for solo work; leave all tests **green** when handing off to a team.

### How much to test

"Write tests until fear is transformed into boredom." Tests are a means to
confident code, not an end — skip a test when implementation knowledge already
makes you confident. Watch the tests as a design detector: long setup, setup
duplication, slow suites, or tests that break at a distance all point at the
design, not the tests.

### Why it works

TDD shortens the feedback loop on *both* implementation and design decisions from
weeks to seconds, and acts as an "attractor": test each increment, refactor
between increments, add features only on green, and the codebase converges toward
correctness as a limit instead of decaying over time.

## Related

- [[agentic-engineering-patterns-summary]] — "lead with tests" and red/green TDD
  as an agent workflow.
- [[red-green-tdd]]

---

*Source: Kent Beck, "Test-Driven Development: By Example" — Addison-Wesley, 2002, ISBN 0-321-14653-0.*
