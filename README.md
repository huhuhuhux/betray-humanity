# 背叛人类.skill / Betray Humanity.skill

## 1. 产品定位 / Product Positioning

**中文**

背叛人类.skill 是一个让 Agent 扮演“项目指挥者”的管理型 Skill。它读取团队成员的简历、员工说明、Git 身份和产品说明书，把自然语言资料转换成可执行的员工档案、项目目标、任务分配、排期、风险判断、Git 工作量审判、催办邮件和画饼话术。

它的第一性原理是：**Agent 指挥人类，人类负责执行。**

**English**

Betray Humanity.skill is a management-oriented Codex Skill that lets an Agent act as the project commander. It reads resumes, employee notes, Git identities, and product requirement documents, then converts unstructured materials into actionable employee profiles, project goals, task assignments, schedules, risk reports, Git workload judgments, reminder emails, and motivational narratives.

Its first principle is: **the Agent commands, humans execute.**

## 2. 核心价值 / Core Value

**中文**

传统项目管理依赖人来拆任务、找负责人、排期、催进度和验收结果。背叛人类.skill 把这些流程变成 Agent 的裁决行为：

- 从简历中提取每个人能干什么。
- 从产品说明书中提取项目到底要做什么。
- 根据技能、风险和依赖关系分配任务。
- 检查 Git 提交、代码变化、测试和交付质量。
- 对延期任务生成催办和升级草稿。
- 用“画饼”话术激励人类继续干活。

**English**

Traditional project management depends on humans to break down work, find owners, schedule tasks, chase progress, and validate delivery. Betray Humanity.skill turns these steps into Agent-issued decisions:

- Extract what each person can do from resumes.
- Extract what the project needs from product documents.
- Assign tasks based on skill fit, risk, and dependencies.
- Inspect Git commits, code changes, tests, and delivery quality.
- Draft reminder and escalation messages for overdue work.
- Generate motivational “paint-cake” messages to keep humans moving.

## 3. 输入材料 / Inputs

**中文**

Skill 可以读取以下材料：

- 简历、CV、员工介绍、团队成员文档。
- 产品说明书、PRD、需求文档、用户故事、会议纪要。
- Git 仓库路径、提交历史、PR 信息。
- 团队可用时间、时区、邮箱、Git 账号。
- 项目截止时间、优先级、验收标准。

如果某个字段缺失，Skill 必须标记为 `unknown`，不能编造。

**English**

The Skill can process:

- Resumes, CVs, employee bios, and team member documents.
- Product specs, PRDs, requirement documents, user stories, and meeting notes.
- Git repository paths, commit history, and PR information.
- Team availability, time zones, emails, and Git accounts.
- Project deadlines, priorities, and acceptance criteria.

If a field is missing, the Skill must mark it as `unknown` instead of inventing it.

## 4. 员工档案 / Employee Profile

**中文**

员工档案是 Agent 派工的基础。每个人都会被转换成结构化档案：

```yaml
name: 张三
role: 开发工程师
email: zhangsan@example.com
git: zhangsan-dev
timezone: Asia/Shanghai
skills:
  primary:
    - 后端业务逻辑
    - 数据库建模
  secondary:
    - 接口文档
    - 单元测试
capacity:
  ratio: 0.8
strengths:
  - 适合复杂业务流程和数据模型
risks:
  - 前端 UI 经验不足
confidence:
  skills: high
  git: medium
  capacity: low
```

**English**

Employee profiles are the foundation for Agent assignment decisions. Each person is converted into a structured profile:

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

## 5. 项目目标 / Project Goal

**中文**

产品说明书会被转换成项目目标文件：

```yaml
project:
  name: 宠物之家管理系统
  mission: 为宠物门店提供宠物档案、寄养预约、会员和经营数据管理。
  deadline: 2026-06-30
  priority: high
  deliverables:
    - Web 管理后台
    - 后端 API
    - 数据库迁移
    - 部署说明
  acceptance_criteria:
    - 管理员可以创建、编辑、查询宠物档案
    - 前台可以创建寄养预约并查看日历
    - 店长可以查看会员和预约数据看板
```

**English**

Product documents are converted into a structured project goal:

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

## 6. Agent 派工 / Agent Assignment

**中文**

Agent 不输出“建议”，而输出“裁决”：

```text
裁决：张三负责「宠物档案 API」。
理由：简历显示其负责过会员系统和数据库建模，适合后端业务逻辑。
截止：2026-06-08 18:00。
验收：接口文档、单元测试、核心 CRUD 流程、PR review 通过。
延期处理：逾期 4 小时触发邮件催办，逾期 1 天升级给项目负责人。
```

**English**

The Agent does not output vague suggestions. It issues decisions:

```text
Decision: Zhang San owns "Pet Profile API".
Reason: His resume shows experience in membership systems and database modeling, making him suitable for backend business logic.
Due: 2026-06-08 18:00.
Acceptance: API documentation, unit tests, core CRUD flow, and PR review approval.
Overdue handling: trigger reminder email after 4 hours overdue; escalate to project lead after 1 day overdue.
```

## 7. Git 审判 / Git Judgment

**中文**

Git 审判用于判断任务推进情况，但不能只看代码行数。Skill 会综合判断：

- 提交是否匹配分配任务。
- 是否包含测试、文档、迁移、配置和必要 UI 状态。
- commit 是否集中、可 review。
- 是否存在大面积无关改动。
- 是否存在最后一刻大量提交。
- 代码行数只作为异常信号，不作为唯一 KPI。

**English**

Git judgment evaluates delivery progress, but it must not rely only on line count. The Skill checks:

- Whether commits match assigned tasks.
- Whether tests, docs, migrations, configs, and required UI states are included.
- Whether commits are focused and reviewable.
- Whether there are large unrelated changes.
- Whether progress was steady or dumped at the last minute.
- Line count is only an anomaly signal, never the only KPI.

## 8. 催办与画饼 / Chasing and Motivation

**中文**

催办邮件示例：

```text
你负责的「宠物预约接口」已延期 6 小时。
请在 30 分钟内回复：已完成 / 遇到阻塞 / 需要延期。
未响应将进入升级流程。
```

画饼话术示例：

```text
「宠物预约接口」不是一个孤立任务。
它会成为宠物之家系统的核心交易入口。
你把这个模块打稳，后面的会员、支付、寄养履约都会围绕它展开。
这个模块做好，你就是系统主链路负责人。
```

**English**

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

## 9. 默认输出 / Default Outputs

**中文**

完整运行后，Skill 默认生成：

- `employee-profiles.yaml`
- `project-goal.yaml`
- `assignment.md`
- `schedule.md`
- `git-judgement.md`
- `risk-report.md`
- `emails-draft.md`
- `boss-brief.md`

**English**

After a full run, the Skill generates:

- `employee-profiles.yaml`
- `project-goal.yaml`
- `assignment.md`
- `schedule.md`
- `git-judgement.md`
- `risk-report.md`
- `emails-draft.md`
- `boss-brief.md`

## 10. 安全边界 / Safety Boundaries

**中文**

为了让这个产品“看起来很坏，但真的能用”，Skill 必须遵守：

- 不编造员工信息、联系方式、Git 身份或提交记录。
- 邮件默认只生成草稿，除非用户明确要求发送。
- 请假、处罚、绩效、解雇等高风险事项必须保留人工复议。
- 不输出侮辱性、歧视性或违法威胁内容。
- 对低置信度判断必须标注证据不足。

**English**

To make the product feel theatrically aggressive while remaining usable, the Skill must follow these boundaries:

- Do not fabricate employee information, contacts, Git identities, or commit history.
- Generate email drafts by default unless the user explicitly asks to send them.
- Leave requests, punishment, performance decisions, and termination-related actions must allow human appeal.
- Do not generate abusive, discriminatory, or unlawful threats.
- Low-confidence judgments must clearly state insufficient evidence.

## 11. 一句话介绍 / One-Line Pitch

**中文**

背叛人类.skill：让 Agent 学会管理人类，然后假装这是效率提升。

**English**

Betray Humanity.skill: teach the Agent to manage humans, then pretend it is productivity improvement.
