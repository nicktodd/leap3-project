# Week 10 - Project Time Guidance

## What each track has been learning

**Software Engineering track:** Cloud engineering foundations, AWS account setup and IAM,
networking (VPC, subnets, security groups), S3, CloudFront, containerising for the cloud and ECR,
ECS, managed data and secrets (RDS, Secrets Manager), observability and cost awareness, and
deployment automation.

**Systems Analyst track:** The capstone from the analyst's side: deployment readiness from an
analysis perspective, a requirements walkthrough, validating the deployed platform against
acceptance criteria, exploratory testing, logging, triaging and resolving defects with the
engineers, UAT execution and evidence, the go/no-go recommendation, finalising the analysis pack,
structuring the showcase, and a review of how AI was used across the analysis work.

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

This week's deliverable is getting your Angular front end somewhere a real URL reaches it,
deployed by a command your whole team could run, not just the one person who remembers the
steps. It's also the final week of the programme, and this Friday's presentation is the full
programme showcase, not an internal update.

## Analyst focus

The engineers deploy it; the analysts decide, with evidence, whether it's ready. That
recommendation belongs in the showcase.

## Handoffs

- **Engineers to analysts:** the deployed platform, as early in the week as possible. Every day
  it's only running locally is a day it can't be validated.
- **Analysts own:** validating the deployed build against the acceptance criteria, exploratory
  testing, and running UAT with your customer instructor against the plan written in week 8.
- **Joint:** the defect resolution cycle. Analysts triage, engineers fix, analysts re-test.
- **Analysts own:** the go/no-go recommendation, and the evidence behind it.

## What to keep in mind

- This week's S3 and CloudFront teaching covers the standard pattern for this: a private bucket,
  never addressed directly, sitting behind a CDN that's the only reader it trusts. Apply that.
  A public bucket is the faster route to something on screen, and it costs you real things:
  plain-HTTP access to your own login page, anything you upload being world-readable, and no
  way to control caching or error handling in front of it.
- Deployment should be one repeatable command, not a sequence of steps in somebody's shell
  history. Running it twice should leave things exactly as running it once did, test that
  rather than assume it.
- Whatever credential runs your deployment should be scoped to only what it needs. If those
  credentials leaked tomorrow, what's the actual blast radius, and does your setup genuinely
  limit it or just assume it does? No long-lived key belongs in your repository, ever, in any
  branch, in any file.
- Once it's deployed, test a route other than the root, not just the homepage. If it breaks,
  that's telling you something real about how a static file store differs from a server that
  understands your application's own routes, and it's worth working out what your CDN needs to
  do about it.
- Your API is still running locally, not deployed. Once your UI is served from somewhere else,
  what actually has to change for your backend to accept a request from that origin at all, and
  is "allow everything" an acceptable answer for a service holding customer positions?
- Real cloud resources cost money and keep running until somebody tells them to stop. Confirm
  with your instructor what your team is responsible for tearing down, and when, before the
  showcase, not after.
- A go/no-go that's always "go" isn't a recommendation. If there are open defects or unmet
  exit criteria, the honest answer might be "go, with these known issues", and that's a
  stronger thing to say in front of stakeholders than pretending there are none.

## Suggested project session

- Apply this week's S3/CloudFront teaching to your own build. Agree who owns the deployment
  script, and actually rehearse running it twice.
- Walk through what changes once your API is called from a different origin than it's used to,
  and decide what you're doing about it.
- Finish UAT and the defect cycle, and agree the go/no-go recommendation as a team, with the
  analysts presenting the evidence.
- Do a final pass on the risk list from every earlier week, anything still open needs an
  honest answer in the showcase, not a hope that nobody asks.
- Rehearse the showcase itself: walk the whole platform end to end, and know who's presenting
  which part, so nobody is caught explaining something they didn't build. Engineers and analysts
  should both have a real part, not the analysts introducing and the engineers doing the rest.
- Confirm cost and teardown responsibilities with your instructor.

## What to present: the final showcase

This week's presentation is the programme showcase to stakeholders, the same audience and
stakes as the original kickoff day. Cover:

- The business outcome first: what a client can now do, and how you know, traced back to the
  requirements.
- The platform end to end: architecture, the decisions that shaped it, and how it's changed
  since the candidate architecture you pitched at kickoff.
- A live demo, deployed, not running on someone's laptop.
- Your go/no-go recommendation, the UAT evidence behind it, and any known issues you'd ship with.
- If your team built the additional capability from BR-18 in week 9, what it is, why that
  one, and what you deliberately left out.
- Two or three design decisions you'd genuinely defend, and what you rejected along the way.
- Where AI tools helped you across the programme, where they didn't, and how you knew the
  difference, on both the engineering and the analysis side.
- What you'd do next if this were a real six-month programme rather than a ten-week one.
