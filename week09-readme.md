# Week 9 - Project Week Guidance

## What each track has been learning

**Software Engineering track:** No new teaching content: the whole week is applied project work.

**Systems Analyst track:** No new teaching content: the whole week is applied project work, with
the emphasis on planning, roadmap and estimation, and requirements, test and impact work against
the live build, with instructor 1-2-1s.

> **These are suggestions, not a plan.** What follows is matched to what both tracks have
> just been taught, so it's a sensible default for this week. In practice your team runs its
> own project: you decide what goes into each sprint, in what order, and who picks it up.
> Doing something earlier, later or differently is fine, as long as it's a choice your team
> made and can explain.

## Context

There's no new teaching content this week, the whole week is dedicated to project work. This is
where your team closes the gap between what the platform is supposed to do, the business
requirements spec, and what it currently, genuinely does, end to end, before deployment
later in the programme.

Because this is a full week rather than a Friday, the guidance below is a suggested shape for
the whole week, not just one day.

## Analyst focus

In practice your analysts run the audit that decides what the week is spent on, own the
conversation with the customer about what won't get done, and re-run the test pack as fixes
land.

## Handoffs

- **Analysts own:** the traceability audit, each requirement traced to its stories, its tests
  and its current status, and the priorities that come out of it, agreed with the customer.
- **Analysts to engineers:** the BR-18 recommendation, drawn from the ranked extension ideas in
  week 7, with its justification.
- **Engineers to analysts:** each fix as it lands, so the relevant tests can be re-run and the
  defect closed or reopened.
- **Joint:** the decision log, and the end-to-end integration test.

## Suggested week shape

- Start with an audit. Walk BR-01 through BR-18, and the service expectations in
  section 9, as a team, and mark each one done, partial, or not started, against what's actually
  running right now, not what a backlog item says. Your analysts should lead this, and a
  traceability matrix, requirement to story to test to status, is the natural way to record it.
- Prioritise ruthlessly. With a week left before deployment, close the highest-priority gaps
  first, Must before Should before Could, rather than whichever is more interesting to build. If
  you genuinely can't close everything, this is a real question for your customer instructor
  rather than a call your team makes alone, they've sat through every demo and know what
  actually matters to them.
- Use the open defect log alongside the audit. A Must requirement with an open high-severity
  defect against it isn't done.
- If the platform already holds up end to end with time to spare, BR-18 asks for one additional
  capability that extends its value, justified against the other options you considered. That's
  worth attempting once the core platform is solid, not before. The analysts' ranked extension
  ideas are the starting point for choosing.
- If the analytics and ETL work from week 7 hasn't been picked up yet, it belongs in the
  audit like everything else.
- Integration test the whole platform together, not week by week: place an order end to end
  through the real UI against the real services, and see where it actually breaks. Re-run the
  test pack against it as a regression check.
- Revisit the risk list from every earlier week, which risks are still open, and which have
  you now resolved or knowingly accepted?
- Keep a running decision log of what you chose to fix, what you chose to leave, and why, you'll
  want it for the final showcase.

## What to present to the class

- A status against the business requirements spec: what's solid, what's partial, what
  you deliberately didn't get to and why, shown from the traceability matrix.
- If you built one, the additional capability from BR-18 and the reasoning behind choosing it.
- The open defects, and which of them you'd ship with.
- An updated backlog and risk list, this is your last checkpoint before deployment.
