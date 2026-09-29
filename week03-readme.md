# Week 3 - Project Friday Guidance

## What each track has been learning

**Software Engineering track:** Core Java, OO principles, OOAD, UML class and sequence diagrams,
SOLID, clean code, TDD and JUnit.

**Systems Analyst track:** Business analysis foundations: elicitation techniques and question
design, a paired stakeholder interview, BRDs, functional vs non-functional requirements and
traceability, AI-assisted requirements drafting and critical review, as-is and to-be process
modelling in Mermaid, BPMN, data flow and context diagrams, use cases, user stories and INVEST,
acceptance criteria in Given/When/Then, and spotting seeded errors in an AI-generated requirements
pack.

> **These are suggestions, not a plan.** What follows is matched to what both tracks have
> just been taught, so it's a sensible default for this week. In practice your team runs its
> own project: you decide what goes into each sprint, in what order, and who picks it up.
> Doing something earlier, later or differently is fine, as long as it's a choice your team
> made and can explain.

## Context

This week's deliverable is the trading domain in Java: the entities, rules and lifecycle that
decide whether an order is accepted. You already modelled this same domain as tables. This
week it's objects, and the two aren't quite the same exercise, a table stores
state, an object owns the behaviour that changes it.

## Analyst focus

The analyst track ends the week with a consolidated requirements pack and a refined backlog
in JIRA.

What they've been taught lines up closely with what engineers need this week. The spec's section
2 describes the as-is process: a dealer stands behind every trade and can catch a mistake before
it settles, and in the target platform "that judgement has to be designed into the system
itself." Mapping what that dealer actually checks is the most direct route to what BR-05's
"checked against the firm's trading rules" should resolve to. A Given/When/Then written precisely
enough is also a test case an engineer can write first.

## Handoffs

- **Analysts to engineers:** acceptance criteria for the BR-05 checks and the BR-06 lifecycle,
  written in Given/When/Then, precise enough that an engineer can write the failing test straight
  from them. Also the as-is and to-be process for placing an order.
- **Engineers to analysts:** the class diagram and the order states the engineers have chosen.
  Analysts check them against the stories; the full reconciliation of the two domain models
  happens next week, when the analysts are taught class modelling themselves.
- **Joint:** turning criteria into first tests. An analyst and an engineer pairing on this is one
  of the best uses of Friday.

## The trap to avoid

A week of UML and OOAD makes it tempting to design the class diagram that looks right on a
whiteboard, then move on. Before you do, put it under some pressure from what you already know
about this platform, not a hint about what's coming, just what you've already committed to:

- One of the programme's own objectives is that the firm can extend this platform later without
  rebuilding what came before. Other parts of your own system, later in the programme, are
  going to need to ask "is this order allowed?" How does your design hold up if something other
  than what you're building this week needs to ask that same question? Does answering it require
  a database, a framework, or a specific way of being called, or could it, in principle, be
  answered in isolation?
- BR-05 and BR-06 need an answer here, not just a passing mention: what sequence of checks
  does "checked against the firm's trading rules" actually resolve to, and what does "recorded as
  a commitment before execution" imply about the states an order can be in? Decide the lifecycle
  deliberately, which states exist and which are genuinely terminal, rather than letting it fall
  out of whatever code gets written first.
- How are you representing monetary values? It's worth actually testing what happens to a balance
  across many small operations with whatever type you've chosen, rather than assuming it'll be
  fine.
- On the analyst side: acceptance criteria that restate the requirement ("the order is checked
  against the rules") aren't criteria. If an engineer can't write a test from one without coming
  back to ask what it means, it needs another pass.

None of this has one right answer. What matters is that the decision was made on purpose and your
team can explain why, not that you land on any particular structure.

## Suggested Friday session

- Hold a second customer meeting, led by your analysts this time and using this week's
  elicitation techniques, focused on what the trading desk checks today and which of those
  checks the platform now has to make. Engineers should be in the room.
- Walk a candidate class diagram as a team before anyone writes code. Every member should be
  able to explain why a class exists and where a rule lives, not just the person who drew it.
- Pressure-test it against SOLID: where would a new instrument type or a new order rule force a
  change, and is that change contained or does it ripple?
- Work through the questions above as a team and agree your answers before coding.
- Agree your TDD approach for the week, tests first, and who's pairing with whom. Start the
  tests from the analysts' acceptance criteria.
- Refine the backlog against the domain model you now have, does anything in it need rewording
  now that the rules are concrete? Every story should now carry acceptance criteria.

## What to present to the class

- A walkthrough of your class diagram and the buy/sell rules it encodes.
- The as-is and to-be process for placing an order, and what the dealer's judgement turned into.
- One acceptance criterion traced to the test that checks it.
- The reasoning behind how coupled or independent your rules are from any one caller, and how
  you're representing money, and why.
- A SOLID decision you made deliberately, and what you'd do differently under a different
  requirement.
- An updated backlog.

This Friday is the first assessment touchpoint (TP1): the backlog and its acceptance criteria,
the requirements pack, the data model and data dictionary, and how the team is running itself.
The domain engine itself is assessed at TP2.
