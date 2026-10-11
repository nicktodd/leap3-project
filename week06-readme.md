# Week 6 - Project Time Guidance

## What each track has been learning

**Software Engineering track:** Identity, access management and zero trust, JavaScript and
TypeScript fundamentals, Node.js, NestJS, DTOs and validation in NestJS, secure DB access and
password hashing, and JWT issuing and validation.

**Systems Analyst track:** APIs, cloud and systems literacy: how the platform is built and how
data moves in and out of it, REST fundamentals, reading OpenAPI specs, calling the live APIs in
Postman, reading code without writing it, SOAP vs REST, COBOL and CICS basics, batch processing,
cloud awareness, environments, pipelines and releases, following a change through CI/CD, NFRs in a
cloud context, Kafka and event-based processing, risk, assumption and dependency tracking in JIRA,
impact analysis, and webhook and DEC APIs.

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

This week's deliverable is real authentication: BR-01 needs registration and secure sign-in,
BR-02 needs a client restricted to their own data, and BR-03 needs a session that's time-limited
and revocable. Whatever your team already did about authentication, left it open, stubbed
something, or built it for real, this is the week it either arrives properly or gets revisited
with what you now know. That covers both your week 4 decision about the API and whatever the UI
signed in against in week 5.

## Analyst focus

The analyst track ends the week with a systems and integration analysis, and a joint review
of the built UI against the screen specification.

Two parts of the analysts' week line up directly with this week's build. Moving authentication
from wherever it stands to where it needs to be is a change with a blast radius, which is what
impact analysis is for. And last week's role and permission matrix is the specification for what
the auth service has to enforce.

## Handoffs

- **Analysts to engineers, before the change:** an impact analysis of moving authentication from
  its current state to the real service: every part of the platform that assumes something about
  who's calling it, and what has to change there.
- **Analysts to engineers:** the role and permission matrix from last week, as the spec for BR-02
  and section 9.3.
- **Engineers to analysts:** the running auth service and the protected API, which analysts
  exercise from Postman: a missing token, a tampered token, and one client asking for another
  client's data.
- **Joint, analyst-led:** review the built UI against the screen spec, and raise each gap as a
  defect on the board rather than a comment in a meeting.
- **Analysts:** trace one business rule from the requirement, through the acceptance criteria,
  to the code that enforces it. It's the analyst's half of "every member can walk the platform."

## The trap to avoid

- Zero trust is this week's framing for a reason. Once this service is real, what should every
  other part of your platform stop assuming, that it was previously trusting by default or
  taking on faith?
- BR-02 and section 9.3 need more than "does this token exist": a client may act on their own
  data and never anyone else's, and internal access should be limited to what a role genuinely
  needs. What does your service actually check to guarantee that, and where does the check live?
  Does it match the permission matrix, or has one of them drifted?
- BR-03 needs a session that's revocable, not just time-limited. If a credential is compromised
  right now, what would your team actually have to do to shut that session down before it
  expires on its own? If the honest answer is "wait for it to expire," that's worth surfacing as
  a risk, not quietly accepting.
- This week's teaching covers password hashing properly, argon2 and bcrypt-style algorithms
  rather than a fast general-purpose hash. Apply it here, and make the cost or parameter choice
  deliberately, written down, not a default copied from the first tutorial you find.
- A password, and anything that could reconstruct one, should never reach a log. That's not
  really a design decision, it's a line not to cross, worth checking for directly rather than
  assuming your logging is fine.

## Suggested project session

- Design the auth flow as a team before anyone writes a controller: what's issued at login, what
  a refresh looks like, what a token actually needs to carry to answer BR-02.
- Work through the zero trust and revocation questions above and agree your answers.
- Plan the move from wherever you left authentication to where it needs to be now,
  and what has to change elsewhere in your platform for that to be clean rather than messy.
  Start from the analysts' impact analysis.
- Decide and document your password hashing choice and its parameters.
- Review the UI against the screen spec together, and log what doesn't match.
- Check the NFRs written in week 4 against what's actually been built: which hold, which
  don't, and which you can't yet tell.
- Refine the backlog against anything this week's work has surfaced about account state or
  access.

## What to present to the class

- A walkthrough of your auth flow and the identity decisions behind it.
- How you moved from wherever authentication stood to where it is now, what the impact analysis
  predicted, and any risk in that move.
- How you're guaranteeing BR-02, that a client can only ever reach their own data, checked
  against your permission matrix.
- What the UI review against the screen spec found.
- An updated backlog.

This Friday is the second assessment touchpoint (TP2): the domain, the API, the UI and
authentication, and the analysis and design work behind them.
