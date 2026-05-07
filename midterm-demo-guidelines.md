# Midterm Demo Guidelines - CSC 394

## Overview

The midterm check-in demo is a working-software milestone. It is due during **Week 6** and counts as **10% of the team project milestone grade**.

By this point, the vertical slice demo should already have proven that the team can connect one narrow feature through the front end, API, and data layer. The midterm demo raises the bar: the team should now show that the application is becoming a coherent product, not just a single connected feature.

This is not expected to be the final product. It is expected to show meaningful progress across the stack, credible project execution, and a realistic path to the preview and final demos.

The central expectation is simple: **the project must function on demo day in a way the team can explain.**

---

## How This Differs from the Vertical Slice Demo

The vertical slice demo asked: **Can your team make one feature work end-to-end?**

The midterm demo asks: **Can your team turn that working foundation into a usable application?**

At the midterm, a single isolated slice is no longer enough unless it has grown into a more complete and reliable application path. Teams should demonstrate broader functionality, stronger integration, clearer engineering practices, and a concrete plan for finishing.

| Earlier Vertical Slice | Midterm Check-In |
| --- | --- |
| One narrow user story | One primary workflow plus supporting features or a second workflow |
| Mock or hardcoded data acceptable | Persistent data expected for the main demo path |
| Integration proof | Integrated application progress |
| Minimal error handling | Clear validation, error handling, and known quality gaps |
| Architecture exists in concept | Architecture matches what is running and can be explained |
| Setup should be possible | Setup, deployment path, and environment needs are documented |

---

## What the Midterm Demo Should Prove

Your demo should answer six questions:

1. **What problem are you solving, and for whom?**
2. **What can a user do in the application today?**
3. **What has been completed since the vertical slice demo?**
4. **What parts of the system are actually connected and backed by persistent data?**
5. **How do you know the current build is reliable enough to continue from?**
6. **What remains to be built before the preview and final demos?**

A strong midterm demo shows working software, visible progress, technical understanding, and honest planning. It does not need to show every planned feature, but it should make clear that the team has moved beyond a single proof-of-concept slice.

---

## Required Demo Format

Each team should plan for an **8-10 minute demo** followed by **2-4 minutes of questions**.

Every team member should speak. Speaking time does not need to be perfectly equal, but each person should be able to explain their contribution and how it fits into the overall system.

Recommended structure:

| Section | Time | What to Cover |
| --- | ---: | --- |
| Project refresher | 1 min | Problem, target users, and core value proposition |
| Progress since vertical slice | 1 min | What was working before and what is new now |
| Live application demo | 4-5 min | Walk through the primary user workflow and at least one supporting capability |
| Technical walkthrough | 1-2 min | Front end, back end, data model, API, deployment, and integration points |
| Quality and project status | 1 min | Tests, CI/CD status, known bugs, risks, and next sprint priorities |
| Q&A | 2-4 min | Instructor and peer questions |

---

## Minimum Functional Expectations

The midterm demo should include more than the original vertical slice. At minimum, the team should demonstrate a working application path with real integration and persistent state.

That means the team should be able to show:

- A running user interface, not only wireframes, static screens, or slide mockups.
- A primary user workflow that a real user would recognize as useful.
- At least one supporting feature, alternate role, or second workflow that shows the product is expanding beyond the original slice.
- A back-end API or server-side layer that supports the demonstrated workflows.
- Persistent data using a database or equivalent durable store for the main demo path.
- Front-end and back-end integration for all features shown as working.
- At least one validation, error, empty-state, or unhappy-path behavior handled gracefully.
- Clear evidence that the project is in version control and team members are contributing through branches, pull requests, commits, or comparable workflow evidence.
- A realistic plan for what will be completed next.

Examples of midterm-ready progress:

| Project Type | Midterm-Ready Example |
| --- | --- |
| Task or project manager | User creates an account, creates tasks, updates status, sees persisted board state, and receives validation on invalid input |
| Marketplace or listing app | User creates a listing, another user can browse or search it, listing data persists, and invalid listing data is rejected |
| Scheduling app | User creates an event or appointment, sees it in a list or calendar, updates/cancels it, and the app handles unavailable or invalid times |
| Review or recommendation app | User submits a review, it appears in the UI, aggregate data updates, and duplicate/invalid input is handled |
| Social or collaboration app | User creates shared content, another role or user can view/respond, data persists, and access or validation rules are explained |

Mock data is acceptable only for secondary or unfinished areas. The main demo path should not be mock-only. If a team cannot persist data for the main path, the team must explain the blocker and show substantial progress elsewhere, but that will be treated as a risk for the milestone.

---

## Technical Expectations

Your team should be prepared to discuss the technical state of the application with specific evidence.

### Front End

Be ready to explain:

- Main user flows implemented so far.
- Components, pages, or views that are complete.
- How the UI communicates with the back end.
- Loading, error, empty, and success states for the demonstrated workflow.
- Which areas are still placeholder, mock, or incomplete.

### Back End and API

Be ready to explain:

- Major API endpoints or server-side operations currently implemented.
- Request/response behavior for the demo path.
- How the API validates input and returns errors.
- Authentication and authorization status if applicable.
- Which endpoints are production-like, which are temporary, and which are planned but not yet built.

### Data Storage

Be ready to explain:

- What data is stored persistently.
- Basic data model or schema.
- How records are created, read, updated, or deleted.
- How the application proves persistence during the demo, such as refresh, logout/login, or a second browser session.
- How you seed, reset, migrate, or clean demo data if needed.

### Deployment and Environments

By the midterm, deployment may still be in progress, but the team must know the deployment path.

Be ready to explain:

- Whether the application is deployed, locally runnable, or partially deployed.
- Where the front end, back end, and database run.
- Required environment variables or configuration categories, without exposing secret values.
- Whether `.env.example`, setup instructions, and local run commands are current.
- Current deployment blockers and the plan to resolve them.

### Testing and CI/CD

Be ready to explain:

- What automated tests exist today.
- What parts of the system are manually tested before demos.
- Whether a GitHub Actions workflow or other CI process runs on pull requests or main branch changes.
- Whether linting, formatting, or test scripts are documented and run by the team.
- What quality gates will be added before the preview demo.

---

## Project Management Expectations

The midterm demo should show that the team is managing the project, not just writing code.

Teams should be ready to show or discuss:

- Current sprint board, issue tracker, or task list.
- Which user stories are done, in progress, blocked, or deferred.
- Which requirements from the original pitch have changed and why.
- Evidence of code review, branching, or pull request workflow.
- How work is divided across team members.
- Key risks and mitigation plans.
- Updated scope if the original plan was too large.

Cutting scope is acceptable. Hiding scope problems is not.

---

## What to Submit

To submit the midterm demo milestone, commit all project code, documentation, configuration, and required assets, then merge the completed work into the repository's `main` branch before the deadline.

The `main` branch should include:

- All source code needed for the demonstrated application.
- All required assets, seed files, migrations, scripts, and configuration examples.
- Link to the deployed application in the README, if available.
- Instructions for running the app locally if deployment is incomplete.
- Short demo outline or slide deck used in the presentation (If Applicable).
- Current project status summary: completed, in progress, blocked, deferred.
- Requirements/status summary that maps major planned features to current implementation status.
- Testing summary: automated tests, manual checks, known gaps.
- API or architecture documentation, if updated since the vertical slice demo.
- AI disclosure statement describing how AI tools were used for this milestone.

The repository should be clear enough that someone who missed the live demo could understand the current state of the project and run it from the committed instructions.

---

## Evaluation Criteria

The midterm check-in will be evaluated on the quality of the working software, the clarity of the demo, and the team's understanding of the system.

| Category | Weight | Strong Evidence |
| --- | ---: | --- |
| Live functionality | 25% | A meaningful user workflow runs successfully during the demo |
| Progress beyond vertical slice | 15% | The app shows new integrated functionality beyond the earlier single slice |
| Integration and persistence | 20% | Front end, back end, and durable data storage are connected for the main path |
| Technical understanding | 15% | Team can explain architecture, API, data model, deployment, and tradeoffs |
| Testing and reliability | 10% | Team has automated or repeatable manual checks and knows current quality gaps |
| Project management and scope control | 10% | Sprint board, priorities, ownership, blockers, and adjusted scope are clear |
| Presentation and team participation | 5% | Demo is rehearsed, organized, and includes all team members |

A demo that does not run at all cannot earn higher than 50% of the milestone grade and receives no credit for the live-functionality portion.

---

## Demo Readiness Checklist

Before class, confirm:

- [ ] The app runs on the machine or environment you will use for the demo.
- [ ] The primary workflow works without live debugging.
- [ ] At least one supporting feature, alternate role, or second workflow is ready to show.
- [ ] The database has usable demo data.
- [ ] Data persistence can be proven during the demo.
- [ ] Login credentials or test accounts are ready, if needed.
- [ ] Environment variables are configured and secret values will not be displayed.
- [ ] Local setup instructions and `.env.example` are current.
- [ ] The team has rehearsed the exact demo path.
- [ ] The team has a fallback plan if deployment fails.
- [ ] The repo is up to date and the demo branch is stable.
- [ ] Known bugs are documented honestly.
- [ ] Every team member knows what they will say.
- [ ] The team can explain what is real, what is mocked, and what is still unfinished.

---

## Common Pitfalls to Avoid

- Repeating the vertical slice demo without showing meaningful new progress.
- Showing only slides with no running software.
- Showing only disconnected front-end mockups.
- Claiming features are complete when they are not connected to the real system.
- Relying on mock data for the main demo path without explaining why.
- Spending the whole demo on setup, login problems, or debugging.
- Letting only one person explain the entire project.
- Hiding blockers until demo day.
- Presenting a large feature list without showing working core flows.
- Exposing API keys, passwords, database URLs, or secret values during the demo.

---

## Final Reminder

The midterm demo is a checkpoint, not the finish line. The goal is to prove that the project has moved beyond a single vertical slice into a working product foundation.

Show working software. Show what changed since the earlier demo. Explain it clearly. Be honest about what is incomplete. Leave the audience confident that the team can reach the preview and final demos.
