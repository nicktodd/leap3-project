# Week 5 - Project Friday Guidance

## What each track has been learning

**Software Engineering track:** HTML, CSS, JavaScript in the browser, fetch/HTTP, Angular
fundamentals, project structure and tooling, components, services and dependency injection, HTTP
communication, connecting to the Spring Boot backend, OpenAPI-generated clients, reactive forms,
routing, authenticated flows and testing with Playwright.

**Systems Analyst track:** UI/UX literacy and stakeholder demos: user-centred design, WCAG
accessibility as a requirement, wireframing and low-fidelity prototyping in Figma, AI-assisted
wireframe drafting and review, turning a wireframe into an annotated specification, specifying UI
states, validating a spec against WCAG, usability testing, access control from the user's side and
a role and permission matrix, reading an OpenAPI contract, and structuring and delivering a demo
to stakeholders, including handling pushback.

> **These are suggestions, not a plan.** What follows is matched to what both tracks have
> just been taught, so it's a sensible default for this week. In practice your team runs its
> own project: you decide what goes into each sprint, in what order, and who picks it up.
> Doing something earlier, later or differently is fine, as long as it's a choice your team
> made and can explain.

## Context

This week's deliverable is the trading UI: sign-in, a dashboard, an order ticket and an order
history, wired up to your own real backend, not a mock. The real auth service arrives next week,
so sign-in this week runs against whatever your team decided in week 4, left open, stubbed or
built early, and gets replaced or revisited in week 6. BR-10, BR-11 and BR-13 are what it has to
show, and section 6's Joanna persona, not a trading professional, is who it has to work for.

## Analyst focus

This is the week the two tracks overlap most. The analyst track ends the week with an
annotated screen specification pack.

The screen spec and the UI are being produced in the same week, so don't run them as a
hand-over. Build them together: wireframes first, agreed quickly, then the spec and the build
tightening against each other through the week. If your team would rather start wireframing
earlier from the week 3 user stories, that's a perfectly good choice.

## Handoffs

- **Analysts to engineers:** wireframes and an annotated screen spec for each required view,
  including its states: empty, loading, error, permission-denied, and an order that's accepted
  but not yet resolved, documented as a state diagram. WCAG expectations are part of the spec,
  not a later check.
- **Analysts to engineers, for next week:** a role and permission matrix, what each role may see
  and do, and how the UI behaves when it isn't allowed. This is the specification the auth
  service is built against in week 6.
- **Joint:** API contract sign-off. Your analysts can now read it in detail against the use cases
  and the screen spec.
- **Analysts lead:** a usability test with someone who hasn't seen the UI, and the demo to your
  customer instructor.

## The trap to avoid

- BR-06/BR-07 already established that accepting an order and executing it are separate steps.
  The response your UI gets back from placing an order is not the final outcome. What does your
  interface do with an order that's been accepted but not yet resolved, render it as if
  something's broken, or as genuinely still working? Section 9.2 needs a client who never
  wonders whether their action registered, how does your design deliver that?
- Client-side validation isn't enforcement. The rules you already built into your backend
  services still have to hold regardless of what this form does. Treat validation here as
  helping Joanna avoid an easy mistake, per section 9.5, not as a second place the business
  rules live.
- Every error your backend can return has to reach the screen as something Joanna can act on,
  not raw or internal text. Branch on whatever error codes your own services define, and decide
  what a non-technical user needs to be told for each one. Your analysts wrote down what each
  error means to the business last week; this is where it gets used.
- A session token belongs only with your own services. If anything in this UI calls a
  third-party API directly, from the browser, a market data source or anything else, that's
  worth a second look: should that call be happening here at all, or somewhere server-side that
  can hold the credential instead?
- Nothing secret belongs in a browser bundle, no API key, no signing secret, nothing you'd mind
  a user reading in dev tools, because they can.
- On the analyst side: a screen spec that only describes the happy path. The empty, error and
  still-working states are the ones engineers have to guess at, and every guess is a likely
  defect.

## Suggested Friday session

- Walk your screens as a team against the requirements spec, the screen spec and your earlier
  customer meeting notes, does what you're building actually show what the customer said they
  needed, and would Joanna manage it without help?
- Agree the component and state boundaries before building spreads across the team, so the
  login, dashboard, order ticket and blotter don't each reinvent how they talk to the backend.
- Decide how you're generating or writing your API calls against your own backend contracts, and keep it consistent across the team.
- Work through the questions above and agree your answers.
- Plan your test coverage: what's a unit test, what needs Playwright, and who owns which. The
  UI states in the screen spec are a ready-made list of things to test.
- Run a short usability test, analyst-led, with someone outside your team: watch them place an
  order without helping, and turn what you saw into prioritised changes on the backlog.
- This is the first week with something a non-technical person can actually use rather than
  read about. Show it to your customer instructor before Friday's over, place an order in front
  of them if you can, and bring back what they made of it, not just whether it worked. Your
  analysts have just been taught how to structure exactly this kind of demo and handle pushback
  in it, so let them lead it.
- Refine the backlog with the weeks still ahead in mind - what has to be true of the platform
  end to end before the applied project week's gap-closing can start from a solid base rather
  than a shaky one?

## What to present to the class

- A demo of the UI against the real backend, not a mock.
- The screen spec, and one place the spec and the build disagreed and what you did about it.
- What your customer instructor thought when they saw it, praise, confusion or otherwise, and
  what the usability test found.
- How you're handling an order that's accepted but not yet resolved.
- Your test coverage and what it does and doesn't catch.
- An updated backlog, and what you're carrying into the applied project week.
