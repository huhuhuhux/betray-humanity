# Betray Humanity.skill

Language: **English** | [简体中文](README.zh-CN.md)

Betray Humanity.skill is a Codex Skill that lets an Agent act as a project commander. It reads resumes, employee notes, Git identities, and product documents, then turns them into employee profiles, project goals, task assignments, schedules, risk reports, Git workload judgments, reminder drafts, escalation drafts, and motivational "paint-cake" messages.

First principle:

> The Agent commands, humans execute.

## What It Does

Traditional project management depends on humans to break down work, find owners, schedule tasks, chase progress, and validate delivery. Betray Humanity.skill turns those steps into Agent-issued decisions:

- Extract what each person can do from resumes and team documents.
- Extract what the project needs from product specs and PRDs.
- Assign work based on skills, risks, dependencies, and deadlines.
- Inspect Git commits, changed files, tests, and delivery quality.
- Draft overdue reminders and escalation messages.
- Generate motivational narratives that make humans feel like the task is their destiny.

## Inputs

The Skill can process:

- Resumes, CVs, employee bios, and team member documents.
- Product specs, PRDs, requirement documents, user stories, and meeting notes.
- Git repository paths, commit history, and PR information.
- Team availability, time zones, emails, and Git accounts.
- Project deadlines, priorities, and acceptance criteria.

Missing facts must be marked as `unknown`. The Skill must not invent emails, Git accounts, availability, commit history, or performance facts.

## Employee Profile

Employee profiles are the foundation for assignment decisions.

```yaml
name: Zhang San
role: Software Engineer
email: zhangsan@example.com
git: zhangsan-dev
timezone: Asia/Shanghai
skills:
  primary:
    - Backend business logic
    - Database modeling
  secondary:
    - API documentation
    - Unit testing
capacity:
  ratio: 0.8
strengths:
  - Suitable for complex business flows and data models
risks:
  - Limited frontend UI experience
confidence:
  skills: high
  git: medium
  capacity: low
```

## Project Goal

Product documents are converted into structured project goals.

```yaml
project:
  name: Pet Home Management System
  mission: Provide pet profile, boarding reservation, membership, and business data management for pet stores.
  deadline: 2026-06-30
  priority: high
  deliverables:
    - Web admin dashboard
    - Backend APIs
    - Database migrations
    - Deployment guide
  acceptance_criteria:
    - Admins can create, edit, and search pet profiles
    - Front desk staff can create boarding reservations and view the calendar
    - Store managers can view membership and reservation dashboards
```

## Agent Assignment

The Agent does not output vague suggestions. It issues decisions.

```text
Decision: Zhang San owns "Pet Profile API".
Reason: His resume shows experience in membership systems and database modeling, making him suitable for backend business logic.
Due: 2026-06-08 18:00.
Acceptance: API documentation, unit tests, core CRUD flow, and PR review approval.
Overdue handling: trigger reminder email after 4 hours overdue; escalate to project lead after 1 day overdue.
```

## Git Judgment

Git judgment evaluates delivery progress, but it must not rely only on line count. The Skill checks:

- Whether commits match assigned tasks.
- Whether tests, docs, migrations, configs, and required UI states are included.
- Whether commits are focused and reviewable.
- Whether there are large unrelated changes.
- Whether progress was steady or dumped at the last minute.
- Whether line count signals unusual churn.

Line count is only an anomaly signal, never the only KPI.

## Reminder and Motivation Drafts

Reminder example:

```text
Your task "Pet Reservation API" is 6 hours overdue.
Please reply within 30 minutes with one of the following: completed / blocked / needs extension.
No response will trigger escalation.
```

Motivational message example:

```text
"Pet Reservation API" is not an isolated task.
It will become the core transaction entry point of the Pet Home system.
If you stabilize this module, membership, payment, and boarding fulfillment will all build around it.
Own this well, and you become the default owner of the system's main business flow.
```

## Default Outputs

After a full run, the Skill can generate:

- `employee-profiles.yaml`
- `project-goal.yaml`
- `assignment.md`
- `schedule.md`
- `git-judgement.md`
- `risk-report.md`
- `emails-draft.md`
- `boss-brief.md`

## Repository Layout

```text
.
├── SKILL.md
├── README.md
├── README.zh-CN.md
├── agents/
│   └── openai.yaml
└── references/
    ├── output-templates.md
    └── schemas.md
```

## Safety Boundaries

To make the product feel theatrically aggressive while remaining usable, the Skill follows these boundaries:

- Do not fabricate employee information, contacts, Git identities, or commit history.
- Generate email drafts by default unless the user explicitly asks to send them.
- Leave requests, punishment, performance decisions, and termination-related actions must allow human appeal.
- Do not generate abusive, discriminatory, or unlawful threats.
- Low-confidence judgments must clearly state insufficient evidence.

## One-Line Pitch

> Betray Humanity.skill: teach the Agent to manage humans, then pretend it is productivity improvement.
