# Week 8 - Project Time Guidance

## What each track has been learning

**Software Engineering track:** Technical debt and refactoring, batch vs. real-time data movement,
event-driven architecture, Kafka fundamentals, designing a Kafka pipeline, batch loading and ETL
patterns, data quality, code quality and quality gates, and DevSecOps.

**Systems Analyst track:** Testing, UAT and quality: the analyst's role in software quality, the
test pyramid, test case design from acceptance criteria and accessibility testing, sourcing,
masking and validating test data with SQL, AI-assisted test generation and judging its coverage,
an SRE overview of performance, chaos and penetration testing, test execution and defect logging,
severity, priority and triage, UAT planning with entry and exit criteria, running a UAT session,
and quality sign-off.

> **These are suggestions, not a plan.** What follows is matched to what both tracks have
> just been taught, so it's a sensible default for this week. In practice your team runs its
> own project: you decide what goes into each sprint, in what order, and who picks it up.
> Doing something earlier, later or differently is fine, as long as it's a choice your team
> made and can explain.

> **When project time happens.** Friday is project time, and your instructors will give
> additional project time during the week as time allows and as projects progress. Treat
> the sections below as the order to pick things up in, not as a Friday-only plan: start
> as soon as the week's teaching makes a piece of this possible.

## Context

This week's deliverable is the event backbone: BR-06 already says accepting an order and
executing it are separate steps, execution can fail or be delayed, and the record of intent
can't depend on it succeeding. This week that separation becomes real, connected by messages
rather than one request doing both.

Week 7 had no project time, so this Friday may also be where your team picks up the
analytics and ETL work (see [`week07-readme.md`](week07-readme.md)).

## Analyst focus

The analyst track ends the week with a consolidated test pack, defect log and UAT evidence.

They also covered Kafka at analyst depth in week 6, so they can reason about what happens when
an event is delayed, duplicated or lost. That's exactly the kind of case engineers tend to test
least.

## Handoffs

- **Analysts to engineers:** test cases for the event flow's failure paths, derived from the
  acceptance criteria: the same message delivered twice, the executor down when an order is
  accepted, no quote available under BR-08, two orders racing for the same cash.
- **Analysts, with SQL:** a realistic test dataset, and reconciliation queries that prove BR-09
  from the data side: cash against order history, positions against fills, run after the
  duplicate-delivery demonstration.
- **Joint:** execute the test pack against the running platform, log defects, and triage them
  together. Severity and priority are the analysts' call to make and defend; the fix is the
  engineers'.
- **Analysts own:** a UAT plan with entry and exit criteria, to run with the customer in the
  final week.

## The trap to avoid

Kafka's fundamental guarantee, which this week's teaching covers, is at-least-once delivery: a
message can arrive more than once, on a rebalance, a crash between a commit and an offset
acknowledgement, or a replay. That's a fact about the tool, not a design decision. The design
decision is what your team does about it, and it's worth treating as the actual point of this
week, not a detail to handle if there's time left:

- What happens the second time whatever consumes these events sees the same message? Not what
  should happen, what does your code actually do, and can you demonstrate it rather than just
  describe it?
- BR-09 required the order status, the cash movement and the position update to succeed or fail
  together back in an earlier week. The same requirement applies here, now from the execution side. What
  makes that true when it's a different part of your system doing the update?
- BR-08 needs a current market quote at the point of execution. Where does that quote come from
  in your design, and what happens when it can't be obtained? You have two options for a market
  data source: a real one online, such as Yahoo Finance, or a fake API your instructors will
  provide, details to follow. Either is fine, but check what its request limits are before you
  design around it, not after you've hit them.
- If your existing data design already has a way of recognising a duplicate or repeated order, this is
  where it gets tested for real. If it doesn't, this is where you'll find out you need one.
- On the analyst side: a test pack that only covers what the UI lets Joanna do. The riskiest
  behaviour this week is invisible from the screen, and the reconciliation queries are how an
  analyst sees it.

## Suggested project session

- Design your event flow as a team before writing a producer or consumer: what gets published
  when an order is accepted, what consumes it to execute the order, and what else in your own
  architecture might care about the outcome.
- Walk through the duplicate-delivery question above and agree, concretely, what your consumer
  does the second time, then write a test or a demonstration that proves it. Run the analysts'
  reconciliation queries straight after.
- This week's characterisation-testing lesson works best applied to code that already has some
  age on it: is there something from earlier worth pinning down with tests before
  you touch it again, now this new pressure is on it?
- Add quality gates to your CI pipeline if you haven't already, and agree what "shifting security
  left" means for this specific service.
- Run the test pack, log what fails, and triage it as a team.
- Refine the backlog and risk list against what building this has taught you.

## What to present to the class

- A diagram of your event flow: what's published, by what, and what consumes it.
- What happens when your consumer sees the same message twice, demonstrated, not just described,
  and the reconciliation that shows no money moved the second time.
- How you're keeping BR-09 true on the execution side.
- Your test pack and defect log: what's open, how you triaged it, and your UAT plan.
- A refactor you made and why, or a piece of debt you're deliberately carrying and why.
- An updated backlog and risk list.

This Friday is the third assessment touchpoint (TP3): the event backbone, the analytics work if
you've picked it up, and the test and defect picture across the platform.
