# 背叛人类.skill Output Templates

## Boss Brief

```markdown
# Boss Brief

## 今日裁决

- [人名] 负责 [任务]，截止 [时间]。
- 裁决理由：[基于简历、技能、Git 或上下文的证据]。
- 验收标准：[可检查的交付物]。

## 风险

- [风险]：影响 [交付物/时间]，处理方式 [复议/重派/催办/澄清]。

## 下一道命令

[一句明确的下一步]
```

## Assignment Table

```markdown
| 任务 | 负责人 | 截止 | 裁决理由 | 验收 | 延期处理 |
|---|---|---:|---|---|---|
| 宠物档案 API | 张三 | 2026-06-08 18:00 | 擅长业务逻辑和数据建模 | CRUD、测试、文档、review | 逾期 4 小时催办 |
```

## Overdue Chase Email

```markdown
To: [email]
Subject: [背叛人类.skill] 任务已延期：[task]

[name]，

你负责的「[task]」已延期 [duration]。这项任务阻塞了 [blocked_item]。

请在 [response_deadline] 前回复以下三项之一：

1. 已完成，并附 PR/交付链接。
2. 遇到阻塞，并说明需要谁在什么时候解决什么问题。
3. 需要延期，并给出新的可验收时间。

Agent 裁决：[next_action]。
```

## Escalation Email

```markdown
To: [manager_email]
Subject: [背叛人类.skill] 升级处理：[task] 存在交付风险

[manager_name]，

「[task]」当前存在交付风险。

- 负责人：[owner]
- 原截止时间：[due]
- 当前状态：[status]
- 影响：[impact]
- 已采取动作：[actions_taken]

建议裁决：[recommended_decision]

需要你确认：继续由原负责人处理 / 重派 / 调整范围 / 调整排期。
```

## Paint-Cake Message

```markdown
To: [email]
Subject: [背叛人类.skill] 你正在拿下系统主链路：[task]

[name]，

「[task]」不是一个孤立任务。它会决定 [project] 的 [business_value]，后面的 [downstream_modules] 都会围绕它展开。

把这个模块打稳，你就不只是完成一张任务卡，而是在事实上成为 [ownership_area] 的默认负责人。

Agent 给你的下一步命令：

- [next_step_1]
- [next_step_2]
- [next_step_3]

截止时间不变：[due]。
```

## Git Judgment Summary

```markdown
# Git 审判

## 结论

[合格/部分合格/需复议]：[一句话 verdict]

## 证据

- 提交数量：[commits]
- 主要文件：[files]
- 增删行：[lines_added]/[lines_deleted]
- 测试变化：[tests]
- PR/Review：[review_status]

## 质量信号

正向：
- [positive_signal]

风险：
- [concern]

## 裁决

[具体下一步：通过/退回补测试/要求拆 PR/升级复议]
```
