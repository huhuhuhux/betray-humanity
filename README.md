<div align="center">

# 🧠 背叛人类.skill

**Agent 指挥人类，人类负责执行。**

[![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827?style=for-the-badge)](SKILL.md)
[![GitHub stars](https://img.shields.io/github/stars/huhuhuhux/betray-humanity?style=for-the-badge)](https://github.com/huhuhuhux/betray-humanity/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/huhuhuhux/betray-humanity?style=for-the-badge)](https://github.com/huhuhuhux/betray-humanity/commits/main)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-2563eb?style=for-the-badge)](https://github.com/huhuhuhux/betray-humanity/pulls)

**简体中文** | [English](README.en.md)

一个带点反派气质的 Codex Skill：读取简历和产品说明书，生成员工档案、项目目标、任务分配、排期、Git 审判、催办草稿、升级草稿和画饼话术。

[🚀 快速开始](#quick-start) · [📦 安装](#install) · [🧾 示例输出](#example-output) · [🛡️ 安全边界](#safety-boundaries)

</div>

## ✨ 为什么要做

大多数 AI 工具都想当助理。

这个想升职。

**背叛人类.skill** 让 Agent 拥有一个“项目指挥者”人格：它知道团队里有哪些人，理解产品到底要做什么，然后派活、排期、审判 Git、催延期，还会写那种听起来很像管理层的画饼话术。

它是一个有梗的项目，但底层流程是认真做的：

- 📄 简历变成员工档案。
- 🎯 产品说明书变成项目目标。
- 🧩 目标变成有负责人、截止时间、验收标准和升级规则的任务。
- 🔍 Git 历史变成交付证据。
- 📮 延期任务变成催办和升级草稿。
- 🍰 关键任务变成让人继续干活的画饼话术。

## ⚡ 它能做什么

| 能力 | 输出 |
|---|---|
| 📄 简历解析 | 技能、角色、联系方式、Git 身份、产能、优势、风险 |
| 🎯 产品说明书解析 | 范围、交付物、里程碑、验收标准、假设条件 |
| 🧠 Agent 派工 | 负责人、截止时间、裁决理由、验收标准、兜底路径 |
| 🗓️ 排期规划 | 里程碑、依赖关系、关键路径、延期规则 |
| 🔍 Git 审判 | 提交节奏、变更文件、diff 信号、测试、质量风险 |
| 📮 消息生成 | 催办邮件、升级邮件、画饼话术 |

<a id="install"></a>

## 📦 安装

把这个仓库克隆到 Codex skills 目录。

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

## 🚀 快速开始

让 Codex 使用这个 Skill 读取团队资料和产品说明书：

```text
Use betray-humanity.

读取 ./resumes 和 ./prd/pet-home.md。
生成员工档案、项目目标、任务分配、排期、风险报告、Git 审判、邮件草稿和 boss brief。
```

轻量版：

```text
Use betray-humanity to assign this PRD to the team.
只输出员工档案、项目目标、任务分配表和延期规则。
```

## 🧱 输入示例

### 员工文档

```yaml
name: 张三
role: 开发工程师
email: zhangsan@example.com
git: zhangsan-dev
skills:
  - 后端业务逻辑
  - 数据库建模
  - 接口文档
capacity: 0.8
```

### 项目目标

```yaml
project:
  name: 宠物之家管理系统
  mission: 为宠物门店提供宠物档案、寄养预约、会员和经营数据管理。
  deadline: 2026-06-30
  priority: high
```

<a id="example-output"></a>

## 🧾 示例输出

### Agent 裁决

```text
裁决：张三负责「宠物档案 API」。
理由：简历显示其负责过会员系统和数据库建模，适合后端业务逻辑。
截止：2026-06-08 18:00。
验收：接口文档、单元测试、核心 CRUD 流程、PR review 通过。
延期处理：逾期 4 小时生成催办草稿，逾期 1 天升级给项目负责人。
```

### Git 审判

```text
结论：部分合格。
证据：8 个提交，24 个文件变更，宠物档案服务补充了测试。
风险：数据库迁移缺少回滚说明。
命令：退回补充回滚方案，再进入验收。
```

### 画饼话术

```text
「宠物预约接口」不是一个孤立任务。
它会成为宠物之家系统的核心交易入口。
你把这个模块打稳，后面的会员、支付、寄养履约都会围绕它展开。
这个模块做好，你就是系统主链路负责人。
```

## 📁 默认产物

完整运行后，Skill 可以生成：

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

## 🗂️ 仓库结构

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

## 🧭 设计原则

- **给命令，不给建议**：Agent 输出带理由的裁决。
- **证据优先**：派工必须基于简历、产品文档、Git 历史或用户输入。
- **代码行数不是 KPI**：diff 大小只能当异常信号。
- **先草稿，再发送**：催办和升级邮件默认只生成草稿。
- **保留复议**：高影响决策必须有人类复核路径。

<a id="safety-boundaries"></a>

## 🛡️ 安全边界

这个项目可以看起来很坏，但流程必须可审计、可回滚、可复议。

- 不编造员工信息、联系方式、Git 身份或提交记录。
- 不把代码行数当作唯一工作量指标。
- 不直接做出 HR、处罚、请假、解雇等最终决定。
- 不输出侮辱性、歧视性或违法威胁内容。
- 对低置信度判断必须明确标注证据不足。

## 🗺️ Roadmap

- [ ] 简历和 PRD 示例数据。
- [ ] GitHub PR 审查指南。
- [ ] 邮件服务集成说明。
- [ ] 任务管理工具导出模板。
- [ ] 宠物之家系统完整 demo command pack。

## ⭐ 给个 Star

如果你喜欢这种“有点反派，但真的能跑流程”的 AI 项目，给它一个 star。

> 背叛人类.skill：让 Agent 学会管理人类，然后假装这是效率提升。
