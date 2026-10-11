# Week 4 - Project Time Guidance

## What each track has been learning

**Software Engineering track:** Microservices, Spring Boot, layered architecture, REST API design,
contract-first design with OpenAPI, DTOs and validation, persistence with MyBatis, JWT validation
and error handling.

**Systems Analyst track:** OOAD, UML and domain modelling: object-oriented analysis, UML class
diagrams in Mermaid, use case models and specifications, sequence diagrams (including AI-generated
ones, validated), non-functional requirements written for engineering teams, state and activity
modelling of a trade's lifecycle, advanced SQL, safe querying of production data, and validating a
domain model against real data.

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

This week's deliverable is a REST service that exposes your existing domain rules and
data over HTTP: something a client can call to place an order and see the result,
secured, and returning errors in a form a caller can act on.

## Analyst focus

Midweek the analyst track has a joint domain-model reconciliation with the engineers, and
the week ends with an analysis and design pack.

Their state model of a trade is the same question the engineers answered in code last week,
asked from the business side. If the two don't agree, one of them is wrong, and it's worth
finding out which before the API fixes it in place.

## Handoffs

- **Analysts to engineers:** a state model of the trade lifecycle and a sequence diagram of
  placing an order end to end. Also NFRs that turn section 9.1 and 9.2 into something testable
  ("close to immediate" needs a number), and the business meaning of each error case the domain
  defines: what Joanna should be told, and what she can do about it. That becomes the error
  shape in the contract and the error messages in next week's UI.
- **Engineers to analysts:** the draft API contract. Analysts check each operation against a use
  case, and check the error responses against the error meanings above. The contract is formally
  signed off next week, once the analysts have been taught to read OpenAPI in detail.
- **Joint:** reconcile the analysts' domain model and state model with the engineers' classes and
  order states, and record what changed on each side.
- **Analysts, with SQL:** after concurrent orders have been run against one account, reconcile
  the cash balance against the order history in the database. It's one of the clearest ways to
  show BR-09 actually holds.

## The trap to avoid

This is the first time your domain gets called by something real. That's worth treating
as a test of earlier decisions, not just this week's build:

- Did the domain module survive being wired into a real service unmodified, or did you find
  yourself bending a rule to fit the controller, or adding a business decision at the service
  layer instead of calling into the domain? Notice it now, it gets more expensive to unpick the
  more that gets built on top of it.
- This week's contract-first lesson exists for a reason: design the shape of the API, and what an
  error looks like, before you write a controller. What's actually in your contract, and would it
  make sense to someone who's never seen your database? Your analysts are a good test of exactly
  that.
- BR-09 says the fill, the cash movement and the trade record have to succeed or fail together,
  even under failure. What in your service actually enforces that? "They should be atomic" is a
  hope. What makes it true?
- The spec's own assumptions (section 10) say a representative sign-in fixture would exist so
  delivery isn't blocked waiting on a real identity solution, because building real authentication
  is later work. That's your team's decision to make, not something this guide imposes: leave the
  service open for now and pick it up as a backlog item, stand up a throwaway stub just enough to
  test the JWT validation you're taught this week, or build real authentication early if you'd
  rather do it once. All three are legitimate. What isn't is drifting into one of them without
  choosing.
- On the analyst side: a sequence diagram of the design you wish you had. Draw it from what's
  actually running, and where that differs from what you'd want, say so.

## Suggested project session

- Design your API contract as a team before anyone writes a controller: the operations, the
  shape of a response, and what an error looks like, consistently, across every one of them.
- Trace one order end to end through your layers and check whether a business decision has
  leaked into the wrong one. The analysts' sequence diagram is a good thing to trace against.
- Decide as a team whether you're leaving this service open for now, stubbing authentication, or
  building it for real, and record the decision rather than letting it happen by default.
- Walk through error handling: what does the API actually return for each failure case your
  domain already defines, and does it match what the analysts say the business needs it to mean?
- Get the service running as a container in your own environment, alongside what you've already
  built.
- Revisit the OWASP Top 10 material from earlier against this specific service, not as a
  checklist exercise, what actually applies here?
- Refine the backlog against what building the API has taught you about the schema and the
  rules underneath it.

## What to present to the class

- A walkthrough of your API contract and how the implementation satisfies it.
- The trade's state model, and whether it matched the order states in code.
- Your team's decision on authentication this week, open, stubbed, or built for real, and why.
- One place an earlier decision caused friction here, and how you handled it. Hint - you are allowed to change things!
- How you're enforcing BR-09 in this service, and the query that shows it held.
- An updated backlog.
