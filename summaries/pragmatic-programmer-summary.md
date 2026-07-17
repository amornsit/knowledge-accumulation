---
title: The Pragmatic Programmer (20th Anniversary Edition)
created: 2026-07-17
tags: [software-craft, pragmatism, design, testing, career, classics]
source: Andrew Hunt & David Thomas, "The Pragmatic Programmer: Your Journey to Mastery, 20th Anniversary Edition" — Addison-Wesley, 2019, ISBN 978-0-13-595705-9
---

# The Pragmatic Programmer (20th Anniversary Edition)

> Being pragmatic is a mindset, not a toolset: take responsibility for your craft,
> and judge every decision by whether it keeps your knowledge and your code **easy
> to change** — the two master principles being DRY (don't duplicate knowledge) and
> ETC (easier to change).

## Context

Hunt and Thomas's 1999 classic, rewritten for its 20th anniversary (2019). It is
not about any one language or methodology; it's a collection of ~100 short,
practical **tips** organized into 53 topics across 9 chapters, aimed at turning a
coder into a *pragmatic* programmer — someone who thinks about what they're doing
while they do it, takes responsibility, and continually improves. The 2nd edition
keeps the beloved metaphors (broken windows, stone soup, tracer bullets, rubber
ducking) and adds a new organizing principle (**ETC**), plus material on
concurrency/actors, functional-style **transforms**, **property-based testing**,
security, naming, agility as a behavior, and even developer **ethics**. The through
line: software development is a continuous, human, craft-driven activity, and small
disciplined habits compound into mastery.

## Key points

- **Take agency and care about your craft.** *"You Have Agency"* and *"Provide
  Options, Don't Make Lame Excuses."* Pragmatic programmers own their work, their
  careers, and their mistakes — they offer solutions instead of blame, invest
  **regularly in a knowledge portfolio** (learn new languages/tools on a schedule,
  diversify, manage risk), and communicate deliberately.
- **DRY — Don't Repeat Yourself.** *Every piece of knowledge must have a single,
  unambiguous, authoritative representation within a system.* DRY is about
  duplicated **knowledge/intent**, not duplicated text; the enemies are copy-paste,
  but also comments that restate code, and structures that force the same fact to
  be maintained in two places.
- **ETC — Easier To Change (the new master principle).** Good design is design
  that's easier to change; every value the book teaches — decoupling,
  orthogonality, DRY, single responsibility — is a special case of ETC. When two
  paths are equally reasonable, take the one that keeps future change cheaper.
- **Pragmatic paranoia: you can't write perfect software, so defend against
  yourself.** Design by Contract, assertions, *crash early / dead programs tell no
  lies*, balance resources (whoever allocates deallocates), and *take small
  steps—always* (don't outrun your headlights: never take a step bigger than you
  can see).
- **Tracer bullets and prototypes over big up-front everything.** Build a thin,
  working **end-to-end** skeleton early (tracer bullets) and iterate; use
  throwaway **prototypes** to learn about risky unknowns. Requirements are *learned
  in a feedback loop with the user*, not gathered like ripe fruit — *no one knows
  exactly what they want.*

## Details

### Chapter 1 — A Pragmatic Philosophy (the mindset)

The attitude that underlies everything. **Software entropy / broken windows:** one
unfixed bad design or hack invites more decay, so *don't live with broken windows*
— fix or at least flag them. **Stone soup and boiled frogs:** be a **catalyst for
change** (show people a compelling start and they'll join in), but also watch that
you're not the frog slowly boiling as the project drifts — *remember the big
picture.* **Good-enough software:** quality is a requirements issue you negotiate
with users; know when to stop polishing. **Knowledge portfolio:** treat learning
like financial investing — invest regularly, diversify, manage risk, review.
**Communicate!** knowing your audience and delivering ideas well is part of the job.

### Chapter 2 — A Pragmatic Approach (core design values)

Opens with **the essence of good design = ETC**. Then the pillars: **DRY** and
**orthogonality** (eliminate effects between unrelated things — independent,
decoupled components so a change in one place doesn't ripple). **Reversibility:**
there are no final decisions; avoid one-way doors by hiding decisions behind
abstractions. **Tracer bullets** (a working thin slice through all layers, refined
in place) vs. **prototypes** (disposable experiments to answer a question).
**Domain languages** (program close to the problem domain) and **estimating**
(estimate to avoid surprises; iterate the schedule with the code; give ranges and
learn from actuals).

### Chapter 3 — The Basic Tools

Invest in mastering tools that outlast fashions: keep knowledge in **plain text**
(human-readable, won't go obsolete, easy to leverage), wield **command shells**,
achieve **editor fluency** (one editor, well, as an extension of your hand),
**always use version control** (for *everything*, a time machine for your work),
and debug with discipline — *fix the problem, not the blame*, **don't panic**,
`select` isn't broken (*the bug is almost always yours*), *don't assume it—prove
it*. New in this edition: keep an **engineering daybook** to track what you did,
what you learned, and what you were about to do.

### Chapter 4 — Pragmatic Paranoia

Defensive programming, because *you can't write perfect software.* **Design by
Contract** (pre-/post-conditions and invariants make a routine promise exactly what
it does — no more, no less). **Dead programs tell no lies** — crash early rather
than limping on with corrupt state. **Assertive programming** — use assertions for
things that can *never* happen (not for normal error handling). **Balance
resources** — the code that allocates should free; act atomically. **Don't outrun
your headlights** — take small, verifiable steps and avoid predicting the far future.

### Chapters 5 & 6 — Bend or Break, and Concurrency (keeping code flexible)

Reduce coupling so systems bend instead of snapping: **Tell, Don't Ask**, the **Law
of Demeter** (*don't chain method calls* through strangers), **avoid global data**,
and prefer **composition/interfaces over inheritance** (*don't pay inheritance
tax*; use interfaces, delegation, and mixins). **Transforming programming** (new):
think of programs as **pipelines that transform data** (input → series of
transforms → output), a functional lens that reduces hidden state. **Configuration:**
parameterize with external config; put policy in metadata. Concurrency gets its own
chapter: **break temporal coupling** (don't assume things must happen in one order),
*shared state is incorrect state*, **random failures are often concurrency issues**,
and prefer **actors/processes** (message passing, no shared state) and
**blackboards** to coordinate.

### Chapter 7 — While You Are Coding

Coding is active, thoughtful work, not transcription. **Listen to your inner
lizard** (new) — pay attention to nagging doubts and instinct. **Don't program by
coincidence** — rely only on things you understand and can rely on; know *why* your
code works, not just *that* it does. Know **algorithm speed** (estimate Big-O, then
*test your estimates*). **Refactor early, refactor often** — like weeding a garden,
not a special event. On testing, the reframing is sharp: **testing is not about
finding bugs, it's about design** — *a test is the first user of your code*, so
writing testable code forces good decoupling (**Test to Code**, not code-then-test).
New: **property-based testing** to shake out cases you didn't think of, a **security**
topic (*keep it simple, minimize attack surface, patch quickly*), and **naming
things** well (and renaming when meaning drifts).

### Chapters 8 & 9 — Before the Project, and Pragmatic Projects

Requirements live in **the requirements pit**: *no one knows exactly what they
want*; *requirements are learned in a feedback loop*; **dig, don't gather**, and
**work with a user to think like a user.** Solve impossible puzzles by **finding the
box** (the real constraints), and **don't go into the code alone** (pair/mob).
**Agile is not a noun** — it's *how* you do things: make a small step, get feedback,
adjust. For teams: keep them **small and stable**, **organize around functionality**
(full-stack feature teams, not skill silos), automate ruthlessly (**version control
drives builds/tests/releases**; *don't use manual procedures*), **test early, often,
and automatically** (*coding ain't done 'til all the tests run*), **delight your
users** by understanding and gently exceeding their expectations, and **sign your
work** (pride and craftsmanship). The book closes on **ethics** — *first, do no
harm*; *don't enable scumbags* — and *It's Your Life*: you can change it.

### The two principles to keep

If you remember nothing else: **DRY** (one authoritative source for each piece of
knowledge) and **ETC** (prefer whatever is easier to change). Almost every specific
tip is an application of one or both.

## Related

- [[mythical-man-month-summary]] — Brooks on the human/managerial nature of software;
  the pragmatic mindset is the individual-scale counterpart to his team-scale lessons.
- [[test-driven-development-by-example-summary]] — "a test is the first user of your
  code" and small-steps discipline, made into a concrete loop.
- [[working-effectively-with-legacy-code-summary]] — decoupling and testability as
  the tools for the "easier to change" (ETC) codebase this book argues for.

---

*Source: Andrew Hunt & David Thomas, "The Pragmatic Programmer: Your Journey to Mastery, 20th Anniversary Edition" — Addison-Wesley, 2019, ISBN 978-0-13-595705-9.*
