<div align="center">

# 🧠 Betray Humanity.skill

**The Agent commands. Humans execute.**

[![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827?style=for-the-badge)](SKILL.md)
[![GitHub stars](https://img.shields.io/github/stars/huhuhuhux/betray-humanity?style=for-the-badge)](https://github.com/huhuhuhux/betray-humanity/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/huhuhuhux/betray-humanity?style=for-the-badge)](https://github.com/huhuhuhux/betray-humanity/commits/main)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-2563eb?style=for-the-badge)](https://github.com/huhuhuhux/betray-humanity/pulls)

[简体中文](README.md) | **English**

A theatrical Codex Skill that turns resumes and product specs into employee profiles, project goals, task assignments, schedules, Git judgments, reminder drafts, escalation drafts, and motivational "paint-cake" messages.

[🚀 Quick Start](#quick-start) · [📦 Install](#install) · [🧾 Example](#example-output) · [🛡️ Safety](#safety-boundaries)

</div>

## ✨ Why This Exists

Most AI tools want to be assistants.

This one wants a promotion.

**Betray Humanity.skill** gives the Agent a project management persona: it reads who your humans are, understands what the product needs, assigns work, judges progress, chases delays, and writes the kind of motivational message that sounds suspiciously like leadership.

It is a joke with an operational core:

- 📄 Resumes become structured employee profiles.
- 🎯 Product specs become executable project goals.
- 🧩 Goals become assignments with owners, deadlines, acceptance checks, and escalation rules.
- 🔍 Git history becomes delivery evidence.
- 📮 Overdue tasks become reminder and escalation drafts.
- 🍰 Critical tasks become motivational "paint-cake" messages.

## ⚡ What It Can Do

| Capability | Output |
|---|---|
| 📄 Resume parsing | Skills, role, contact, Git identity, capacity, strengths, risks |
| 🎯 Product spec parsing | Scope, deliverables, milestones, acceptance criteria, assumptions |
| 🧠 Agent assignment | Owner, due date, task reason, acceptance checks, fallback path |
| 🗓️ Schedule planning | Milestones, dependencies, critical path, overdue rules |
| 🔍 Git judgment | Commit cadence, touched files, diff signals, tests, quality concerns |
| 📮 Message drafting | Reminder email, escalation email, motivational "paint-cake" message |

<a id="install"></a>

## 📦 Install

Clone this repository into your Codex skills directory.

### macOS / Linux

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/huhuhuhux/betray-humanity.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/betray-humanity"
```

### Windows PowerShell

```powershell
$codexHome = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME ".codex" }
New-Item -ItemType Directory -Force -Path (Join-Path $codexHome "skills") | Out-Null
git clone https://github.com/huhuhuhux/betray-humanity.git `
  (Join-Path $codexHome "skills\betray-humanity")
```

<a id="quick-start"></a>

## 🚀 Quick Start

Ask Codex to use the skill with your team documents and product spec:

```text
Use betray-humanity.

Read ./resumes and ./prd/pet-home.md.
Create employee profiles, project goal, assignments, schedule, risk report,
Git judgment, reminder drafts, and a boss brief.
```

For a lighter run:

```text
Use betray-humanity to assign this PRD to the team.
Only output employee profiles, project goal, assignment table, and overdue rules.
```

## 🧱 Input Examples

### Employee Document

```yaml
name: Zhang San
role: Software Engineer
email: zhangsan@example.com
git: zhangsan-dev
skills:
  - backend business logic
  - database modeling
  - API documentation
capacity: 0.8
```

### Product Goal

```yaml
project:
  name: Pet Home Management System
  mission: Provide pet profile, boarding reservation, membership, and business data management for pet stores.
  deadline: 2026-06-30
  priority: high
```

<a id="example-output"></a>

## 🧾 Example Output

### Agent Decision

```text
Decision: Zhang San owns "Pet Profile API".
Reason: His resume shows membership system and database modeling experience.
Due: 2026-06-08 18:00.
Acceptance: API documentation, unit tests, CRUD flow, and PR review approval.
Overdue handling: send reminder draft after 4 hours overdue; escalate after 1 day.
```

### Git Judgment

```text
Verdict: Partially qualified.
Evidence: 8 commits, 24 files changed, tests added for pet profile service.
Concern: no rollback note for the migration.
Command: return the task for a rollback plan before approval.
```

### Motivational Draft

```text
"Pet Reservation API" is not an isolated task.
It will become the core transaction entry point of the Pet Home system.
Own this well, and you become the default owner of the system's main business flow.
```

## 📁 Default Artifacts

A full run can produce:

```text
employee-profiles.yaml
project-goal.yaml
assignment.md
schedule.md
git-judgement.md
risk-report.md
emails-draft.md
boss-brief.md
```

## 🗂️ Repository Layout

```text
.
├── SKILL.md
├── README.md
├── README.en.md
├── agents/
│   └── openai.yaml
└── references/
    ├── output-templates.md
    └── schemas.md
```

## 🧭 Design Principles

- **Command, not suggestion**: the Agent outputs decisions with reasons.
- **Evidence first**: assignments must be grounded in resumes, specs, Git history, or explicit user input.
- **Line count is not a KPI**: diff size is only an anomaly signal.
- **Draft before send**: reminder and escalation emails are drafts unless explicitly sent by the user.
- **Human appeal remains**: high-impact decisions must keep a review path.

<a id="safety-boundaries"></a>

## 🛡️ Safety Boundaries

The product is theatrically aggressive, but the workflow should stay usable and auditable.

- Do not fabricate employee information, contact details, Git identities, or commit history.
- Do not treat line count as the only measure of work.
- Do not make final HR, punishment, leave, or termination decisions without human review.
- Do not generate abusive, discriminatory, or unlawful threats.
- Mark low-confidence judgments clearly.

## 🗺️ Roadmap

- [ ] Example resume and PRD fixtures.
- [ ] GitHub PR inspection guide.
- [ ] Email provider integration notes.
- [ ] Task tracker export templates.
- [ ] Demo command pack for the Pet Home system.

## ⭐ Star Pitch

If you enjoy AI tools with a little product villain energy and a real workflow underneath, star the repo.

> Betray Humanity.skill: teach the Agent to manage humans, then pretend it is productivity improvement.
