---
title: Working Effectively with Legacy Code
created: 2026-07-14
tags: [testing, legacy-code, refactoring, dependencies, software-craft]
source: Michael Feathers, "Working Effectively with Legacy Code" — Prentice Hall, 2004, ISBN 0-13-117705-2
---

# Working Effectively with Legacy Code

> Legacy code is code without tests; to change it safely, get it under test first —
> break dependencies conservatively, pin current behavior with characterization
> tests, then change under a green bar.

## Context

Michael Feathers' field manual for the most common real-world programming
situation: changing large, poorly-tested, tangled code you didn't write and can't
fully understand. Its reframing is the whole book — **"legacy code is simply code
without tests"** — which turns a vague dread into a concrete engineering problem:
make the code testable, then work test-first. The book is organized as a set of
named answers to problems ("I can't get this class into a test harness", "This
class is too big", "I don't understand the code"), anchored by one algorithm and a
catalog of ~24 dependency-breaking techniques.

## Key points

- **The Legacy Code Dilemma:** to change code safely you need tests, but to get
  tests in place you often must change the code. The escape is to make the
  *smallest, safest* edits needed to install tests — using seams — then let the
  tests make the real change safe.
- **The Legacy Code Change Algorithm:** (1) identify change points, (2) find test
  points, (3) break dependencies, (4) write tests, (5) make changes and refactor.
  Every session should deliver a change *and* leave the area under test — tested
  regions grow like "islands rising out of the ocean."
- **Characterization tests** document what the code *actually does*, not what it
  *should*: put code in a harness, assert something you know is wrong, let the
  failure reveal real behavior, lock that value in, repeat. They're a tripwire for
  future regressions, not a correctness spec.
- **Seams** are places to change behavior *without editing there*; each has an
  **enabling point** where you choose the behavior. Object seams (subclass/override,
  extract interface) are preferred in OO languages; link and preprocessing seams are
  fallbacks for pervasive dependencies.
- **Break dependencies conservatively.** Two obstacles recur — can't *instantiate*
  the object, can't *run* the method in a harness — cleared with the least invasive
  technique from the catalog, in tiny compiler-checked steps.

## Details

### Why "get it under test" beats "just be careful"

Careful editing isn't feedback: a behavior change slips through unnoticed until
production. So the discipline is to invest first in tests that sense change, even at
the cost of slightly uglier code around the "incision points" — the scar heals once
the area is covered.

### Characterization tests, in practice

Because coverage is infinite, these aren't black-box tests: *read the code you're
characterizing*. Get curious, write cases until you understand it, then look at the
specific change you intend and add tests until you're confident they'll **sense any
problem that change could cause**. If you find behavior that looks like a bug, still
pin the actual value (that's the baseline) but mark it suspicious and address it
separately — never "fix" while pinning.

The **Method Use Rule**: before calling a method in legacy code, check whether it
has tests; if not, write them. This spreads coverage exactly where work happens.

### Seams and dependency-breaking

Three seam types map to steps in turning source into a running program: **object**
seams (vary a call by passing/subclassing an object), **link** seams (swap what the
build links against), and **preprocessing** seams (C/C++ macro redefinition). The
catalog of dependency-breaking techniques — Extract Interface, Subclass and Override
Method, Parameterize Constructor, Extract and Override Factory, Break Out Method
Object, Adapt Parameter, and ~18 more — each removes a specific obstacle to getting
an object or method into a harness.

### When you can't get it under test yet: Sprout & Wrap

Sometimes surrounding code is too tangled to characterize now, but you still must
add behavior. **Sprout** the new logic into a new, fully tested method/class and call
it from the old code; or **Wrap** the old method (rename it, add a new one that calls
old + new). These don't cover the legacy code — they stop it from getting worse and
give you a tested beachhead.

### Relationship to TDD

Feathers explicitly advocates TDD for step 5 ("make changes and refactor"). The book
is the *on-ramp* to test-driven work: once the code is pinned under characterization
tests, adding the actual change is ordinary red/green/refactor.

## Related

- [[test-driven-development-by-example-summary]] — the discipline this book hands off
  to once code is under test.

---

*Source: Michael Feathers, "Working Effectively with Legacy Code" — Prentice Hall, 2004, ISBN 0-13-117705-2.*
