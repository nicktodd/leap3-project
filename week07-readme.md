# Week 7 - Project Guidance

## What each track has been learning

**Software Engineering track:** Monday and Tuesday only: Python, pandas, data cleaning,
exploratory data analysis, statistical foundations, APIs, ETL validation and predictive analytics.

**Systems Analyst track:** Monday and Tuesday only: product and design thinking, covering problem
framing, design and product thinking, success measures (leading and lagging indicators), personas
and journey mapping from evidence, ideation, and prioritisation frameworks such as MoSCoW and
RICE, ending with a prioritised backlog of extension ideas.

> **These are suggestions, not a plan.** What follows is matched to what both tracks have
> just been taught, so it's a sensible default for this week. In practice your team runs its
> own project: you decide what goes into each sprint, in what order, and who picks it up.
> Doing something earlier, later or differently is fine, as long as it's a choice your team
> made and can explain.

## Context

**There is no project time this week.** Both tracks are taught Monday and Tuesday only, and are
off from Wednesday to Friday. The analytics and ETL work below doesn't disappear, it moves:
pick it up on the week 8 Friday or in the applied project week, whichever suits your team's
plan. It's looked for at TP3, and as with every area, marks not earned at their touchpoint can
be picked up later.

This week's deliverable is a Python "dashboard" surfacing three business insights, backed by a
tested extract-transform-load pipeline reading from whatever store(s) you designed earlier.
"Dashboard" here means what the week has actually taught: a plain Python script, run from the
command line, that prints a plain-text summary and saves its charts as image files with
matplotlib. Nothing this week teaches Jupyter, Streamlit, Dash or any other notebook or web UI
library, so don't let a team go looking for one, or burn Friday building one from scratch.
Notebooks are the more common tool for this kind of exploratory work in the real world, worth
a look in your own time, but not something to spend project time on this week.

## Analyst focus

Both halves of the analysts' two days feed the project directly. "Three business insights" is a
vague deliverable until someone frames them as outcomes Priya (section 6) can act on, which is
what success measures are for. And the ranked extension ideas are the obvious starting point for
BR-18 in the applied project week.

## Handoffs

- **Analysts to engineers:** the three insights, each written as a question Priya needs answered
  and the measure that answers it, before anyone builds a pipeline. Also a data requirement for
  each: which fields, over what period, at what volume.
- **Engineers to analysts:** the ETL design and the output, which analysts check against the
  numbers in the database with their own SQL.
- **Analysts, for week 9:** the prioritised list of BR-18 candidates, each with its
  justification.

## When you pick this up

- Agree as a team what the three business insights actually are before anyone writes a pipeline.
  Go back to the requirements spec and your earlier customer meeting notes, this is where a
  vague deliverable becomes a specific one. Start from the analysts' success measures.
- Sketch the ETL: what you're extracting from your existing schema, what shape it needs to be in
  for analysis, and where the two disagree.
- Check you actually have enough data to say anything meaningful. A trend by period or client
  segment needs real volume and variety across time, not the handful of rows you seeded earlier
  to test constraints. Generating a larger synthetic dataset is a good use of AI, just
  keep it consistent with your schema's constraints and realistic enough to support the insights
  you've chosen. If your analysts are building test data with SQL in week 8, one dataset can
  serve both.
- Decide how the pipeline will be tested, and who owns writing those tests, before the pipeline
  itself is built.
- If you're not confident the three insights you've picked are actually the ones that matter,
  don't just guess from your earlier customer notes, ask your customer instructor directly. Ten minutes
  now is cheaper than a dashboard built around the wrong three.
- Refine the backlog: are the insights you've chosen actually what the customer asked for?

## What to present to the class

- The three business insights you've chosen, and why they're the right three.
- Your ETL design, and how you're testing it.
- An updated backlog, and anything from your initial database designs that might need to be changed
