# Progress Reviews and Scoring

Your team's project work is reviewed and scored as a team, at four points across the
programme, for a single running score out of 100. There is no pass mark. The
score is a measure of how far the platform and the way you are building it have
come, and it exists so that the feedback at each review is concrete rather than
an impression.

Each team is mostly engineers with one or two systems analysts, and there is one review per team covering both the engineering and the analysis. The analysis
is not a separate strand bolted on: most areas below include work that analysts
lead, and area 2 is the analysis itself.

This document is the whole rubric. Nothing is scored that is not described here, and the points against each item tell you where we think the value is.

## How it works

Reviews happen at four touchpoints, each on a Friday where both tracks have
just finished something coherent to look at, rather than work in flight.

| Touchpoint | When | What comes into scope | Points | Running total |
|---|---|---|---:|---:|
| **TP1** | End of week 3 | Backlog, stories and acceptance criteria, the requirements pack and process models, the data model and data dictionary, the customer engagement, how the team is running itself | 20 | 20 |
| **TP2** | End of week 6 | The domain engine, the REST API, the trading UI and authentication, and the analysis behind them: the state model, NFRs, screen specification, permission matrix and the review of the UI against it | 43 | 63 |
| **TP3** | End of week 8 | The event backbone, atomic execution and duplicate handling, the reporting and ETL work, the test pack, defect log and UAT plan | 23 | 86 |
| **TP4** | End of week 10 | Deployment, UAT and the go/no-go recommendation, the traceability audit and gap-closing, any BR-18 capability, the showcase | 14 | 100 |

Week 7 has no project time, so the reporting and ETL work is first
looked for at TP3.

### The score is additive, and the touchpoints are not deadlines

Each touchpoint releases its own points. It does not re-score everything from the
start: TP1 is scored out of 20, TP2 adds up to 43 more, and so on, up to 100.

Points you do not earn at their touchpoint are not lost. If an area is still thin
at TP2 but solid by TP3, those points are picked up at TP3, at full value. The
touchpoint is when the work is first looked for, and when feedback on it is most
useful to you, not a gate that closes. Points already earned are not taken back
either; the continuity checks below are their own small line items, not a
re-scoring of what came before.

We will still encourage you to meet each touchpoint on time. Scoping work to
land by a fixed review date is a large part of what this project is teaching,
and a team that consistently turns up ready is building a real delivery skill.
Treat the dates as an external constraint the way you would on a real
engagement. But arriving late costs nothing in the score itself.

Every touchpoint after the first also carries a small **continuity check** on
the areas already reviewed. By TP2 the schema has more weeks
built on it, and the question is whether the design still hangs together as a
whole, whether the changes made along the way were deliberate and recorded, and
whether anything regressed in correctness. Adjusting the earlier design is
expected. Leaving the design record behind, or breaking something that used to
work, is not. Those points are noted in each area below.

### You are reviewed against your own design, and it is expected to change

There is no central set of contracts, no prescribed architecture, and no
reference schema. What you are held to is the design record you maintain: your
own architecture, API contracts, event definitions, schema, decision log and
risk list, and your own requirements record, the backlog, acceptance criteria,
models and specifications, read against the business requirements
specification.

That design is expected to change, and changing it is not a cost here. The
candidate architecture pitched at kickoff is made with the least knowledge the
team will ever have of the problem, so large parts of it turning out wrong is
the normal outcome, not a failure. The same is true of the first schema, the
first API shape, the first backlog and the first screen spec.

What is scored is not whether the design held still, but whether it evolved
well: each significant change was a decision the team made on purpose, recorded
with its reason, and reconciled with the rest of the design and the
documentation. A team that spotted a modelling mistake early on, changed it
deliberately later and can explain why scores better here than a team
whose schema never changed because it was never tested. The faults are
unrecorded drift, where the running system, the design record and the
requirements have quietly diverged and nobody chose it, and a correctness
regression that later work introduced and no one caught.

### The contribution record

The score is a team score. It is not split between members, or between the
engineers and the analysts.

Alongside it, keep a `contributions.md` in your repository with one short block
per week: for each member, their role, what they led, what they paired on, and
what they reviewed, plus a line on anything that slipped and where it went. At
each touchpoint the instructor checks it against your commit history and your
board.

Its purpose is to make sure the work rotated within each role and crossed
between them, which the reviews test directly by asking any member to walk a
part of the platform they did not build. If a member cannot speak to any of the
work, that is a conversation with your instructor, not a deduction from the
team's score.

### Walking work you did not build, across roles

"Every member can walk it" means something slightly different for each role,
and the reviews ask for both:

- An **engineer** should be able to walk the requirements behind what they
  built: the story, its acceptance criteria, and what the customer said.
- An **analyst** is not expected to explain code line by line. They should be
  able to trace a business rule from the requirement to where it is enforced,
  explain the design decisions behind it in business terms, and say how it is
  tested.

### The customer's input

The instructor who acted as your customer sends your reviewing instructor a
short note after each interview and demo: whether you prepared, whether you led
the meeting, whether you confirmed what you heard, and whether you followed up
on the answers that were left vague. That note is evidence that feeds the
Delivery and Requirements points. It is not a separate score.

### Score bands

The number is reported with a band, so it means something without a pass line.

| Band | Range | Reads as |
|---|---|---|
| Developing | 0–39 | The pieces exist in part; the platform does not yet hold together, or the team is not yet running as one |
| Functional | 40–59 | The core works and is being built deliberately; known gaps in correctness, rigour or process |
| Solid | 60–74 | The platform does what the requirements ask, the design decisions are defensible, the design has been adjusted deliberately as the team learned more, and the team can explain its own work |
| Strong | 75–89 | Correct where it is hard to be correct, tested where it matters, honest about its own limits, and evolving on purpose rather than by accident |
| Exceptional | 90–100 | The platform and the process would stand up outside the programme, with the difficult properties designed in rather than hoped for |

---

# The scored areas

Eleven areas, 100 points. Each table shows the points available at each touchpoint.
An `R` in the notes means the points at that touchpoint are a regression check on
work first reviewed earlier.

## 1. Delivery and agile process - 12 points

How the team runs itself as a delivery team, reviewed a little at every touchpoint rather than in one block.

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| The board reflects the real state of the work, analysis and engineering alike, and the backlog is refined as the team learns rather than set once | 1 | 1 | 1 | – |
| Decision log and risk list are current and record real decisions and real risks, not a template filled in once; significant changes were impact-assessed before they were made | 1 | 1 | 1 | 1 |
| The weekly class check-in is honest: it surfaces problems, shows the backlog and risks moving, and a member who did not present can answer for the team | 1 | 1 | 1 | 1 |
| The contribution record is maintained per week, records each member's role, and matches the history and the board | 1 | – | – | – |
| **Subtotal** | **4** | **3** | **3** | **2** |

## 2. Requirements and analysis - 14 points

The work the team's analysts lead: turning the spec and the customer into
something engineers can build against and the team can check against.

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| Customer engagement is prepared and led, what was heard is confirmed back in writing, vague answers are followed up, and the customer demo is structured for its audience | 1 | 1 | – | – |
| Stories trace to a requirement or to something the customer said, meet INVEST, and carry Given/When/Then acceptance criteria precise enough to write a test from, rather than restated requirement titles | 3 | – | – | – |
| The data dictionary defines what each field means to the business, and data validation rules are stated as testable criteria | 2 | – | – | – |
| The as-is and to-be process for placing an order is modelled; the trade's state model agrees with the order states in code, or the difference is recorded | 1 | 1 | – | – |
| The screen specification covers every required view and its states (empty, loading, error, permission-denied, accepted-but-not-filled) with WCAG expectations, and the role and permission matrix backs BR-02 and section 9.3 | – | 2 | – | – |
| The section 9 service expectations are written as measurable NFRs | – | 1 | – | – |
| The built UI has been reviewed against the screen specification, and the gaps raised as tracked defects rather than left in conversation | – | 1 | – | – |
| Every requirement from BR-01 to BR-18 and every section 9 expectation traces to its stories, its tests and an honest current status | – | – | – | 1 |
| **Subtotal** | **7** | **6** | **–** | **1** |

## 3. Data, storage and analytics - 12 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| The data model covers the domain the platform needs (accounts, instruments, orders, positions, cash, the permanent record), is normalised, any deliberate denormalisation is recorded with its reason, and it has been reconciled with the data dictionary | 3 | – | – | – |
| Access patterns are worked out capability by capability (order processing, positions and cash, the audit trail, reporting), and each storage decision is tied to the requirement that drove it | 2 | – | – | – |
| Integrity is enforced by the database rather than hoped for in code: keys, constraints, and a way to reject a duplicated order | 2 | – | – | – |
| The historical and reporting design for BR-16 is described: how it is populated, how it is queried, how it behaves as it grows | 1 | – | – | – |
| The data model still hangs together as the domain, the API and then the executor are built on it; changes were deliberate and are recorded, and the design record matches what is running (`R`) | – | 1 | 1 | – |
| The ETL pipeline is separated into extract, transform and load, is repeatable, and handles a malformed input rather than wrapping the run in a bare `try` | – | – | 1 | – |
| Three business insights are each framed as a success measure a non-technical reader can act on before the pipeline is built, the numbers reconcile with the source rows, and the reporting path does not compete with live trading | – | – | 1 | – |
| **Subtotal** | **8** | **1** | **3** | **–** |

## 4. Domain and business rules - 11 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| Entities, enumerations and the order lifecycle match the team's own model, and the terminal states are chosen on purpose rather than falling out of the first code written | – | 2 | – | – |
| The BR-05 checks and the BR-06 "recorded as a commitment before execution" rule are implemented as an explicit, ordered sequence, in the domain and not in a caller | – | 3 | – | – |
| The domain has no database, HTTP or framework dependency, and can answer "is this order allowed?" in isolation | – | 1 | – | – |
| Money is represented with a type that survives many small operations, and the choice is defended | – | 1 | – | – |
| Tests were written before the implementation, evidenced in the commit history, derived from the acceptance criteria, and they assert behaviour rather than only running green | – | 2 | – | – |
| The domain still serves its callers cleanly now that the executor uses it from the execution side; any changes made to accommodate that were deliberate and recorded (`R`) | – | – | 1 | – |
| The domain is coherent across the finished platform, its evolution since TP2 is recorded, and every member can walk it as it stands now (`R`) | – | – | – | 1 |
| **Subtotal** | **–** | **9** | **1** | **1** |

## 5. API and services - 11 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| A running service exposes the team's own published contract, signed off by both roles, and the contract is coherent: a consistent response shape and a consistent error shape across every operation | – | 2 | – | – |
| Layering holds: no persistence in a controller, no HTTP or framework type in the domain, and no business rule that belongs in the domain living in a service | – | 2 | – | – |
| Persistence uses parameterised statements throughout | – | 1 | – | – |
| Order placement is atomic per BR-09: the order record, the cash movement and the holding change commit together or not at all, and something concrete enforces that rather than a hope that it is so | – | 3 | – | – |
| Concurrent orders against one account cannot both spend the same cash, demonstrated, with the losing one failing cleanly and the cash reconciled against the order history afterwards | – | 1 | – | – |
| The service builds and runs as a container in the team's own environment, reproducibly | – | 1 | – | – |
| The API serves the event backbone cleanly; where the contract changed to meet it, the contract and its consumers were updated together (`R`) | – | – | 1 | – |
| **Subtotal** | **–** | **10** | **1** | **–** |

## 6. Events and asynchronous execution - 7 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| Accepting an order and executing it are genuinely separate, connected by messages, and the record of intent does not depend on execution succeeding | – | – | 1 | – |
| The consumer is idempotent: replaying the same message does not double-debit an account, demonstrated on demand rather than described, and confirmed by reconciling the data afterwards | – | – | 3 | – |
| The execution side keeps BR-09 true: order status, cash and position update in one transaction | – | – | 2 | – |
| The market-data source and its request limits are understood, the design stays inside them, and the key never reaches the browser | – | – | 1 | – |
| **Subtotal** | **–** | **–** | **7** | **–** |

## 7. Authentication and security - 7 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| Registration and secure sign-in work end to end (BR-01), and whatever stood in for authentication earlier has been replaced or revisited deliberately, with the impact of the change reviewed first | – | 2 | – | – |
| A client can reach only their own positions, cash and history (BR-02, section 9.3), the check lives somewhere a caller cannot bypass, and what is enforced matches the team's permission matrix | – | 2 | – | – |
| The session is time-limited and revocable (BR-03); if it is only time-limited, that gap is recorded as a risk rather than left silent | – | 1 | – | – |
| Passwords are hashed with argon2 or bcrypt at a deliberate cost, never logged, and no secret is in the repository | – | 1 | – | – |
| Adopting the auth service elsewhere in the platform is a configuration change, not a code change | – | 1 | – | – |
| **Subtotal** | **–** | **7** | **–** | **–** |

## 8. Trading UI and the end-to-end experience - 8 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| The required views exist (sign-in, holdings and cash, order ticket, blotter, per BR-10, BR-11, BR-13), are built to the team's screen specification, and work for the Joanna persona without a guide, evidenced by a usability test | – | 2 | – | – |
| Sign-in runs against the real auth service, route guards block unauthenticated access, and the token is attached to the platform's own services and to nothing else | – | 1 | – | – |
| Every error the back end can return reaches the screen as something a non-technical client can act on | – | 1 | – | – |
| No API key or secret is present in the built bundle | – | 1 | – | – |
| An order that is accepted but not yet filled reads as still working, not as broken, once execution is genuinely asynchronous (section 9.2) | – | – | 2 | – |
| The UI works correctly served from the deployed origin; any changes needed for that (origin configuration, base href) are deliberate and recorded (`R`) | – | – | – | 1 |
| **Subtotal** | **–** | **5** | **2** | **1** |

## 9. Quality, testing and acceptance - 8 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| Tests exist at the level that matches the risk (unit for rules, integration for wiring) | – | 1 | – | – |
| A test pack traced to the acceptance criteria covers negative, boundary and failure cases, including the event flow's, and has been run against the platform with evidence recorded; test data was built deliberately and verified with SQL | – | – | 2 | – |
| Defects are logged so they can be acted on, triaged for severity and priority by the team, and tracked to resolution | – | – | 1 | – |
| Automated tests reach the full path (sign-in and placing an order end to end, each journey standing on its own), characterisation tests were put around older code before it was changed, and a CI pipeline runs the tests and a quality gate on every change | – | – | 1 | – |
| UAT is planned with entry and exit criteria (TP3), then run with the customer against the deployed platform with the evidence captured (TP4) | – | – | 1 | 1 |
| The go/no-go recommendation is supported by evidence, open defects are stated honestly, and the quality gate is green without findings waved through | – | – | – | 1 |
| **Subtotal** | **–** | **1** | **5** | **2** |

## 10. Deployment and operations - 5 points

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| The front end is reachable at a real URL over HTTPS, from a private origin that only the CDN reads; a public bucket does not satisfy this | – | – | – | 2 |
| Deployment is one repeatable command covering build, upload and invalidation, and running it twice leaves the same result as running it once | – | – | – | 1 |
| The deploying credential is scoped to only what it needs, no long-lived key is in the repository, and teardown responsibilities are confirmed and recorded | – | – | – | 1 |
| The back end accepts requests from the deployed origin by a considered rule, not "allow everything" | – | – | – | 1 |
| **Subtotal** | **–** | **–** | **–** | **5** |

## 11. Defence and showcase - 5 points

The part no artefact can show: whether the team owns what it built. See
"Walking work you did not build, across roles" above for what this asks of each
role.

| What is scored | TP1 | TP2 | TP3 | TP4 |
|---|---:|---:|---:|---:|
| Every member can walk the backlog, its acceptance criteria and the data model unaided, and the team can say what the customer did not tell them that they still need | 1 | – | – | – |
| Every member can walk any part of the domain, the API, the UI and authentication, including parts they did not build, and the team can show an order placed live through the UI against real services | – | 1 | – | – |
| The team can trace one order from the request through the topic to the committed rows and the published event, defend the order in which the rules are evaluated, and show the test that proves it | – | – | 1 | – |
| The showcase leads with the business outcome and covers the platform end to end, what the kickoff architecture got wrong and how the design responded, two or three decisions the team would defend and what it rejected, the go/no-go recommendation and its evidence, the BR-18 capability if built, and where AI helped and where it did not; both roles present a real part of it | – | – | – | 2 |
| **Subtotal** | **1** | **1** | **1** | **2** |

---

# The reviews

Each touchpoint is a conversation with your instructor against a running system
and a live requirements record, not a submission read in isolation. Satisfying
the countable items is necessary and it is not sufficient: whether a rule has
quietly moved into the wrong layer, whether an index is justified or merely
present, whether an acceptance criterion could actually be tested, whether an
error message is one a trader could act on, whether your team can explain any of
it, are read rather than searched for. A green test suite is the floor.

Where your design has moved since the last touchpoint, come ready to walk that
change: what you learned, what you decided, and where it is recorded. That is a
normal part of the conversation, not something to explain away.

## Bring to TP1 (end of week 3)

The backlog walked against the spec, with three stories traced back to either a
business requirement or a sentence the customer said, and their acceptance
criteria. One of those criteria alongside the test written from it. The
requirements pack and the as-is and to-be process for placing an order. The
notes from both customer meetings, and what you confirmed back. The risk list.
The data dictionary. The ER diagram and your migrations applied against an empty
database, and where the analysts' model and the engineers' schema differed. Your
six most important queries and why each index earns its place. The design note
on the historical and reporting data. A statement that inserts the same order
twice under one idempotency key and is refused by the database.
`contributions.md`. Your answer to "why is the model this way and not the other
way" for the decision you argued about longest.

## Bring to TP2 (end of week 6)

The domain, the trade API, the auth service and the UI all running together.
The trade's state model next to the order states in code. Your NFRs. Every
operation in your contract answering with the shape your contract states. Each
failure your domain defines produced on demand in your error shape, and rendered
on screen as a sentence a trader can act on. Several concurrent orders against
one account, with the cash reconciled against the order history afterwards by
query. Your `git log` showing tests arriving before implementation. Sign-in from
a clean browser against the real auth service. A guarded route hit without a
session so the redirect can be watched. A missing and a tampered token on a
protected route, and one client asking for another's data. A recording of the
requests one signed-in page makes, showing where the bearer token went and where
it did not. The built bundle searched in front of the panel for a key and a
secret. The screen specification and permission matrix, and the defects raised
when the UI was reviewed against them. What the usability test and the customer
demo told you. Your answer to how a compromised session would actually be shut
down before it expires.

## Bring to TP3 (end of week 8)

The running stack. One order traced from the HTTP request, through your domain,
onto your topic, consumed by your executor, to the committed rows and the
published event. The duplicate message replayed live, moving no money the second
time, and the reconciliation query that shows it. An order placed through the UI
and left sitting unfilled, and the screen bringing it up to date. The test pack
and the acceptance criteria it traces to, the test data and how it was checked,
the defect log and how it was triaged, and the UAT plan. The three business
insights, the success measure behind each, and the numbers behind one of them
traced to the rows they came from, if you have picked the analytics work up.
Your answer to what happens when two customers spend the same money at the same
moment.

## Bring to TP4 (end of week 10)

The deployed application reached over HTTPS at its real URL. Both of the
origin bucket's own endpoints refusing a direct request. The deploy script run
twice. The JavaScript the deployed page serves, searched for secrets. The
scoped deployment policy. Your decision log for the deployment. The
traceability matrix from the project week, brought up to date. The UAT evidence
and the go/no-go recommendation. The risk list from every earlier week with an
honest status on each open item. And the showcase itself: the business outcome,
the platform end to end, the architecture's journey from the kickoff pitch, the
decisions you would defend, the BR-18 capability if you built it, and where AI
earned its place across the programme and where it did not.
