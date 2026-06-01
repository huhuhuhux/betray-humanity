# 背叛人类.skill Schemas

Use these schemas as output targets. Keep unknown facts explicit instead of inventing them.

## Employee Profiles

```yaml
employees:
  - id: zhang-san
    name: 张三
    role: 开发工程师
    seniority: mid
    contacts:
      email: zhangsan@example.com
      phone: unknown
      chat: unknown
    git:
      username: zhangsan-dev
      emails:
        - zhangsan@example.com
    timezone: Asia/Shanghai
    capacity:
      ratio: 0.8
      notes: 每周约 4 天可投入
    skills:
      primary:
        - 后端业务逻辑
        - 数据库建模
      secondary:
        - 接口文档
        - 单元测试
    evidence:
      - source: 张三简历.pdf
        text: 负责会员系统订单和权限模块
    strengths:
      - 适合复杂业务流程和数据模型
    risks:
      - 前端 UI 经验不足
    assignment_preferences:
      owns:
        - 后端 API
        - 数据模型
      assists:
        - 权限设计
      avoid:
        - 高保真 UI
    confidence:
      role: high
      email: high
      git: medium
      skills: high
      capacity: low
```

## Project Goal

```yaml
project:
  name: 宠物之家管理系统
  mission: 为宠物门店提供宠物档案、寄养预约、会员和经营数据管理。
  deadline: 2026-06-30
  priority: high
  users:
    - 门店管理员
    - 前台运营
    - 店长
  scope:
    in:
      - 宠物档案管理
      - 预约寄养
      - 会员管理
      - 数据看板
      - 管理后台登录和权限
    out:
      - 原生移动 App
      - 在线支付
  deliverables:
    - Web 管理后台
    - 后端 API
    - 数据库迁移
    - 部署说明
  acceptance_criteria:
    - 管理员可以创建、编辑、查询宠物档案
    - 前台可以创建寄养预约并查看日历
    - 店长可以查看会员和预约数据看板
    - 核心接口有测试并通过 CI
  milestones:
    - name: 需求冻结
      due: 2026-06-03
    - name: 后端主流程完成
      due: 2026-06-12
    - name: 前端管理后台完成
      due: 2026-06-18
    - name: 联调和验收
      due: 2026-06-25
  assumptions:
    - 使用现有用户体系
  risks:
    - 预约日历和寄养状态流转可能需要产品确认
```

## Assignment

```yaml
assignments:
  - task_id: backend-pet-profile
    title: 宠物档案 API
    owner: 张三
    backup_owner: unknown
    reason: 张三简历显示其擅长后端业务逻辑和数据库建模。
    due: 2026-06-08T18:00:00+08:00
    dependencies:
      - 数据模型确认
    deliverables:
      - API routes
      - database migration
      - tests
      - API documentation
    acceptance:
      - CRUD 流程通过测试
      - PR review 通过
    escalation:
      overdue_after_hours: 4
      action: draft_chase_email
    status: assigned
```

## Git Judgment

```yaml
git_judgment:
  person: 张三
  git_identity:
    username: zhangsan-dev
    emails:
      - zhangsan@example.com
  period: 2026-06-01..2026-06-07
  commits: 8
  files_changed: 24
  lines_added: 830
  lines_deleted: 210
  task_alignment: high
  quality_signals:
    positive:
      - includes tests for pet profile service
      - commits are focused by module
    concerns:
      - no migration rollback found
  verdict: 基本合格，需补迁移回滚说明。
  confidence: medium
```
