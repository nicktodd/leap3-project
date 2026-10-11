# Leap Project


A group project run alongside the Leap training programme. Teams design and build a
trading platform themselves, using whatever technology each week has just taught them, and
manage it as a real agile project: their own architecture, their own backlog, their own customer.

The technical brief is the business requirements spec issued at kickoff, in
[`kickoff/`](kickoff). It describes what the platform must do and says nothing about how to
build it, the architecture, the technology, the division of work into services, all of that is
for each team to propose and defend themselves.

This folder is week-by-week guidance for your team: what you might usefully do with your
project time given what both tracks have just been taught, and what to present back to the
class. It's a sensible default, not a plan to follow: your team manages its own project, decides
what goes into each sprint and in what order, and can spend its time however it judges best.

## A mixed team: engineers and analysts

Each team is mostly engineers from the Software Engineering track, with one or two systems
analysts from the sister Systems Analyst track. The two tracks are taught different things in
the same weeks, and in most weeks what the analysts have just been taught produces exactly the
artefact the engineers need to build against, or the check that tells the team whether what
they built is right. The guidance in each week's file is written with that in mind.

The working split is:

- **Analysts own the what, the why, and whether it was done.** The customer relationship, the
  backlog and its acceptance criteria, the data dictionary, process and state models, the screen
  specification and permission matrix, the test pack, UAT, and the final go/no-go
  recommendation.
- **Engineers own the how.** The code, the services, the pipelines and the deployment.
- **The design belongs to the team.** The architecture, the data model, the domain model and the
  API contract are decided together, and both sides sign them off.

"Own" means leads and is accountable for, not does alone. A few things worth watching for:

- Analysts aren't the team's scribe or project manager by default. Facilitating, note-taking and
  running the board rotate like any other job. An analyst who spends the programme minuting
  stand-ups hasn't done the analyst job.
- Analysts aren't a wall between the engineers and the customer. Engineers still go to customer
  meetings, and every engineer should still be able to walk the backlog and explain an acceptance
  criterion.
- Engineers shouldn't write the requirements and hand them to the analysts to tidy up. Equally,
  analysts shouldn't be writing production code to stay busy. Writing SQL, building test data and
  calling the team's APIs from Postman to investigate something is squarely analyst work.
- With only one or two analysts on a team, analysis can't all wait for Friday. Agree early how
  analysis work reaches the engineers during the week, and put it on the board as stories like
  anything else.

Each week's file opens with what both tracks have been learning, then has an **Analyst focus**
section and a **Handoffs** list: what goes in from the analysts, what comes back from the
engineers, and what gets checked or signed off together. Like everything else here, the cadence
is a suggestion that matches what each track has just been taught. Teams can and do move work
earlier or later, wireframes started ahead of week 5, test cases written alongside the stories,
and that's fine as long as it's a choice.

## Structure

Each `weekNN-readme.md` file corresponds to one week of the programme. Files are named by week
number rather than by what either track teaches, because the two tracks teach different things in
the same week. Each file opens with a summary of what both tracks have just been learning, then
the project guidance for that week. The kickoff slides and the spec are in
[`kickoff/`](kickoff), and the guidance for the kickoff day itself is in
[`week01-readme.md`](week01-readme.md).

| Week | File | Engineering track | Systems Analyst track | Team deliverable | Assessed |
|---|---|---|---|---|---|
| 1 | [`week01-readme.md`](week01-readme.md), [`kickoff/`](kickoff) | Foundations: Git, ways of working & GenAI | Foundations: the SA role, ways of working, JIRA/Confluence, Git | Kickoff day: candidate architecture, project plan, risk list | |
| 2 | [`week02-readme.md`](week02-readme.md) | Pipelines (CI/CD, Docker, IaC, OWASP, Secure Code Warrior) and Data Systems (Postgres, SQL, modelling, NoSQL), in parallel | The trading domain & data systems | First backlog, customer engagement, trade database schema, data dictionary | |
| 3 | [`week03-readme.md`](week03-readme.md) | Java, OOAD, UML, SOLID, TDD | Business analysis: elicitation, BRDs, process modelling, user stories & acceptance criteria | Domain engine, refined backlog with acceptance criteria | **TP1** |
| 4 | [`week04-readme.md`](week04-readme.md) | Spring Boot, REST, OpenAPI, MyBatis, JWT | OOAD, UML & domain modelling | Trade REST API, analysis and design pack | |
| 5 | [`week05-readme.md`](week05-readme.md) | HTML/CSS, Angular | UI/UX literacy & stakeholder demos | Trading UI, screen specification, role & permission matrix | |
| 6 | [`week06-readme.md`](week06-readme.md) | IAM/zero trust, JS/TypeScript, Node, NestJS | APIs, cloud & systems literacy | Auth service, UI validated against the screen specification | **TP2** |
| 7 | [`week07-readme.md`](week07-readme.md) | Python, pandas, EDA, APIs, ETL (Mon-Tue; Wed-Fri off) | Product & design thinking (Mon-Tue; Wed-Fri off) | No project time this week - analytics and ETL picked up in weeks 8-9 | |
| 8 | [`week08-readme.md`](week08-readme.md) | Kafka, event-driven architecture, refactoring, DevSecOps | Testing, UAT & quality | Event backbone, test pack, defect log, UAT plan | **TP3** |
| 9 | [`week09-readme.md`](week09-readme.md) | none, applied project week | none, applied project week | Close the gap against the spec, traceability audit, optional BR-18 extension | |
| 10 | [`week10-readme.md`](week10-readme.md) | AWS, deployment automation | Capstone: validation, UAT, go/no-go | Cloud deployment, go/no-go recommendation, final showcase | **TP4** |

Weeks 1 and 10 are presentation-heavy in a different way to the rest: Week 1's kickoff is
presented to a stakeholder panel, and Week 10's is the final programme showcase. The weeks in
between are internal weekly check-ins to the rest of the class. The four assessment touchpoints
are described in [`assessment/assessment.md`](assessment/assessment.md); each falls on a Friday
where both tracks have just finished something coherent to look at.
