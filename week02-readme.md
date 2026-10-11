# Week 2 - Project Time Guidance

## What each track has been learning

**Software Engineering track:** Two parallel strands. **Pipelines:** a deeper dive on CI/CD,
Docker multi-stage builds, Infrastructure as Code (IaC) concepts, building a CI pipeline, the
OWASP Top 10 and Secure Code Warrior. **Data Systems:** data systems concepts, Postgres, SQL
fundamentals through subqueries and joins, data quality, RDBMS modelling, ER diagrams, choosing
between relational and NoSQL stores, and Snowflake as a cloud data warehouse.

**Systems Analyst track:** The trading domain and data systems: the investment lifecycle, risk,
regulation and the control environment, data fluency for analysts, OLTP vs OLAP, relational
fundamentals, SQL from SELECT through joins, subqueries and CTEs, ER diagrams in Mermaid,
normalisation, translating business requirements into a data model, data quality dimensions,
profiling a dataset and writing validation rules, data integration and mainframe recordkeeping,
and producing a data dictionary. The analyst track's Friday includes a joint schema sign-off.

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

This week's project time covers two things. The first is starting to run as a team the way the rest of the
programme expects: working with a customer, and standing up a backlog. The second is your
platform's own data model. Go back to the business requirements spec, this is where BR-06,
BR-09, BR-14/15 and BR-16 stop being sentences on a page and start being decisions about what
you store and how.

## Analyst focus

Your analysts spent the week on the trading domain and on data, and were taught JIRA and
Confluence in week 1, which they'll use all programme. They haven't been taught elicitation yet,
that's next week, when they'll lead a second, structured customer interview. This week's meeting
is a joint first conversation, but the analysts' domain knowledge makes them the natural people to
ask what engineers tend to skip: who checks a trade today, what Risk and Compliance actually need
to see (section 9.4), and what "reporting" means to Finance.

On the data side, this is a week with two models of the same data: the analysts' model worked
forward from the requirements, and the engineers' schema worked forward from access patterns.
Neither is the right one by default. Where they disagree is where the interesting questions are.

## Handoffs

- **Joint:** the plan for the customer meeting, and the meeting itself.
- **Analysts own:** the notes from the meeting, confirmed back to the customer in writing, and
  the list of questions it left open.
- **Joint, analyst-led:** the first cut of the backlog. Engineers size and challenge it; analysts
  own refining it from here on.
- **Analysts to engineers:** a data dictionary that says what each field means to the business,
  not just its type: allowed values, which requirement needs it, and where the value comes from.
  Also data validation rules written as testable criteria, which become constraints or tests.
- **Analysts, into the repo:** a requirements-first ER diagram in Mermaid, committed next to the
  engineers' schema.
- **Engineers to analysts:** the capabilities-to-storage breakdown, the schema and the
  migrations.
- **Joint:** reconcile the two models, record where they differed and what you decided, and sign
  off the schema as a team.

## Part 1: Running as a team

### Suggested session

1. Plan for, and then hold, a customer meeting with your nominated customer instructor, in
   another room. Plan it together, and agree beforehand who's asking what, so the meeting isn't
   run by whoever talks first.
2. Based on the requirements document and what came out of the customer meeting, identify user
   stories from the requirements spec and capture them as a product backlog.
3. Agree as a team how you'll manage that backlog for the rest of the programme, tool, format,
   who owns refining the backlog, and when you'll revisit it. Your analysts will be working in
   JIRA and Confluence throughout, which makes that the sensible default unless you have a reason
   not to. It's also natural for an analyst to own refining the backlog, with engineers sizing
   and challenging it, but decide it, don't assume it.
4. Agree how the team works across both roles: how analysis reaches the engineers during the
   week rather than only on Fridays, and how analysis work shows up on the board.

## Part 2: The data model

### The trap to avoid

A week of RDBMS modelling and ER diagrams makes "one normalised Postgres schema for everything"
feel like the obvious answer. It's the freshest tool in your hand, so it's the one you'll reach
for. Before committing to that, look again at what the spec is actually asking for:

- BR-09 needs an order's fill, the cash movement and the position change to succeed or fail
  together, that's a strong argument for one transactional store.
- BR-14/15 and section 9.4 need a permanent, unalterable record that survives a restart or a bad
  deployment, at any point a regulator can ask to see it. Is that the same thing as "the current
  state," or a different property this store has to have?
- BR-16, and Priya's persona in section 6, need trading activity analysed by instrument, period
  and client segment, without competing with Joanna placing a live order. That's the same
  question the engineering track's Module 12 asked you to reflect on, does this genuinely want
  the OnLine Transaction Processing (OLTP) database, or something else?

Your engineers did Module 11 this week: classify your own platform's capabilities the way you
classified PaySprint's scenarios, by actual access pattern, not by instinct. The answer might
genuinely be "one store, well designed, is enough", that's a legitimate outcome if you can defend
it against the requirements above. What isn't legitimate is not asking the question, and
documenting the decision.

The analyst-side version of the same trap is a data dictionary that's just a list of column
names. The value is in the meaning: what's the difference between the time an order was placed
and the time it was accepted, and which of those does David need to answer a dispute under
BR-15? A dictionary that can't answer that isn't doing its job.

This is also a good moment to hold your original candidate architecture up against what you now
know. If it said "a database" without saying which kind or how many, does it still hold up?

### Suggested session

- Before drawing any ER diagram, list the platform's capabilities that need data (order
  processing, positions and cash, the audit trail, reporting) and for each one, its access
  pattern: read-heavy or write-heavy, current-state or historical, who queries it and how often.
- Decide, capability by capability, whether it belongs in the same store as the others or not,
  and write down the requirement that drove each decision.
- Design and review the schema for whatever you've decided is your transactional store, as a
  full team, every member should be able to defend it, not just whoever drew it. Put the
  analysts' requirements-first model next to it and walk the differences.
- Check the schema against the data dictionary and the validation rules: is every rule either
  enforced by the database or written down as something a test will check?
- Profile whatever seed data you've loaded the way your analysts were taught this week, for
  missing, duplicate and inconsistent values. Seed data that can't break a rule doesn't test it.
- If you've decided any capability needs a different kind of store, don't build it this week,
  just capture the decision and what it implies for later weeks.
- If modelling this has left your team assuming something the spec doesn't actually say, how
  long history really needs to be kept, what "reporting" means to the business, anything like
  that, that's a fast question for your customer instructor rather than a guess baked into the
  schema. The engineering track's Module 10 taught how to frame exactly this kind of check.

## What to present to the class

- Reflections on how the customer meeting went, what was easy to get out of them, what wasn't.
- An initial overview of your current backlog, and how you're planning to manage it going
  forward.
- Who owns what across the team's engineers and analysts, and how the two will work together
  week to week.
- Your capabilities-to-storage breakdown, and the requirement behind each decision.
- A walkthrough of your current thinking around any potential schemas or NoSQL database
  structures.
- Your data dictionary, and one place where the analysts' model and the engineers' schema
  disagreed and what you decided.
- Anywhere your original architecture pitch has changed now that you've actually modelled the
  data, and why.
- An updated risk list.

The first assessment touchpoint (TP1) falls at the end of next week, and the data model and
data dictionary are part of it.
