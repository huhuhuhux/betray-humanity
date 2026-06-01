# 背叛人类.skill

语言：[English](README.md) | **简体中文**

背叛人类.skill 是一个让 Agent 扮演“项目指挥者”的 Codex Skill。它读取团队成员的简历、员工说明、Git 身份和产品说明书，把自然语言资料转换成可执行的员工档案、项目目标、任务分配、排期、风险判断、Git 工作量审判、催办邮件、升级邮件和画饼话术。

第一性原理：

> Agent 指挥人类，人类负责执行。

## 它能做什么

传统项目管理依赖人来拆任务、找负责人、排期、催进度和验收结果。背叛人类.skill 把这些流程变成 Agent 的裁决行为：

- 从简历和团队文档中提取每个人能干什么。
- 从产品说明书和 PRD 中提取项目到底要做什么。
- 根据技能、风险、依赖关系和截止时间分配任务。
- 检查 Git 提交、文件变化、测试和交付质量。
- 对延期任务生成催办和升级草稿。
- 用“画饼”话术激励人类继续干活。

## 输入材料

Skill 可以读取以下材料：

- 简历、CV、员工介绍、团队成员文档。
- 产品说明书、PRD、需求文档、用户故事、会议纪要。
- Git 仓库路径、提交历史、PR 信息。
- 团队可用时间、时区、邮箱、Git 账号。
- 项目截止时间、优先级、验收标准。

如果某个字段缺失，Skill 必须标记为 `unknown`，不能编造邮箱、Git 账号、可用时间、提交记录或绩效事实。

## 员工档案

员工档案是 Agent 派工的基础。

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

## 项目目标

产品说明书会被转换成结构化项目目标。

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

## Agent 派工

Agent 不输出“建议”，而输出“裁决”。

```text
裁决：张三负责「宠物档案 API」。
理由：简历显示其负责过会员系统和数据库建模，适合后端业务逻辑。
截止：2026-06-08 18:00。
验收：接口文档、单元测试、核心 CRUD 流程、PR review 通过。
延期处理：逾期 4 小时触发邮件催办，逾期 1 天升级给项目负责人。
```

## Git 审判

Git 审判用于判断任务推进情况，但不能只看代码行数。Skill 会综合判断：

- 提交是否匹配分配任务。
- 是否包含测试、文档、迁移、配置和必要 UI 状态。
- commit 是否集中、可 review。
- 是否存在大面积无关改动。
- 是否存在最后一刻大量提交。
- 代码行数是否代表异常波动。

代码行数只作为异常信号，不作为唯一 KPI。

## 催办与画饼

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

## 默认输出

完整运行后，Skill 可以生成：

- `employee-profiles.yaml`
- `project-goal.yaml`
- `assignment.md`
- `schedule.md`
- `git-judgement.md`
- `risk-report.md`
- `emails-draft.md`
- `boss-brief.md`

## 仓库结构

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

## 安全边界

为了让这个产品“看起来很坏，但真的能用”，Skill 必须遵守：

- 不编造员工信息、联系方式、Git 身份或提交记录。
- 邮件默认只生成草稿，除非用户明确要求发送。
- 请假、处罚、绩效、解雇等高风险事项必须保留人工复议。
- 不输出侮辱性、歧视性或违法威胁内容。
- 对低置信度判断必须标注证据不足。

## 一句话介绍

> 背叛人类.skill：让 Agent 学会管理人类，然后假装这是效率提升。
