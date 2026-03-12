---
name: key-tracker
description: "智能关键信息记录：从对话和报告中自动捕获时间节点、遗留问题、决策点、承诺事项等16类关键信息。外置大脑，不遗漏重要信息。"
---

# Key Tracker - 智能关键信息记录

外置大脑，自动捕获工作交流中的关键信息。

---

## 一、核心定位

**不是**：私人秘书、日程管理工具  
**而是**：外置大脑、关键信息捕获系统

**核心价值**：
1. 不遗漏重要信息
2. 可追溯决策过程
3. 提醒待处理事项
4. 沉淀知识经验
5. 跟踪进展状态

---

## 二、记录类型（16 类）

### 时间类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `deadline` | 截止日期 | 截止、之前完成、deadline |
| `milestone` | 里程碑 | 里程碑、节点、阶段性目标 |

### 问题类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `issue` | 遗留问题 | 问题、bug、issue、待解决 |
| `blocker` | 阻塞项 | 卡住、阻塞、等...才能 |
| `risk` | 风险提示 | 风险、可能出问题、担心 |

### 决策类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `decision` | 决策记录 | 决定、确定、选定、就...了 |
| `rationale` | 决策原因 | 因为、考虑到、出于、由于 |
| `assumption` | 假设前提 | 假设、前提、如果...的话 |
| `change` | 变更记录 | 改为、换成、调整、从...改 |

### 承诺类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `commitment` | 我的承诺 | 我会、我保证、我来负责 |
| `expectation` | 他人承诺 | 麻烦你、请你、你来负责 |

### 过程类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `progress` | 进展状态 | 已完成、正在做、进度 |
| `dependency` | 依赖关系 | 依赖、需要等、取决于 |
| `resource` | 资源需求 | 需要、缺少、希望有 |

### 知识类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `learning` | 学习要点 | 经验、教训、记住、以后注意 |
| `insight` | 想法灵感 | 突然想到、灵感、也许可以 |
| `context` | 背景上下文 | 背景、原因是、目的是、为了 |

### 人物类
| 类型 | 说明 | 触发词 |
|------|------|--------|
| `stakeholder` | 关键人物 | 负责、找...、联系...、涉及 |

---

## 三、自动检测规则

### 检测时机
1. **对话过程中** — 实时检测关键词
2. **报告分析时** — 自动提取关键信息
3. **任务讨论时** — 捕获遗留问题
4. **决策过程中** — 记录决策及原因

### 检测原则
- ✅ 宁可多记，不遗漏重要信息
- ✅ 保留原始上下文
- ✅ 自动分类存储
- ✅ 关联相关记录

---

## 四、记录格式

### 主记录库
**位置**: `~/.openclaw/workspace/.keyrecords/records.json`

```json
{
  "records": [
    {
      "id": "KR-YYYYMMDD-XXX",
      "type": "deadline|issue|decision|...",
      "title": "简短标题",
      "context": "上下文说明",
      "source": "conversation|report|analysis",
      "source_text": "原始文本片段",
      "datetime": "ISO-8601（如有时间）",
      "status": "pending|done|cancelled",
      "priority": "high|medium|low",
      "logged_at": "记录时间"
    }
  ]
}
```

### 分类存储
```
.keyrecords/
├── records.json           # 主记录库
├── 时间类/
│   ├── deadlines.json
│   └── milestones.json
├── 问题类/
│   ├── issues.json
│   ├── blockers.json
│   └── risks.json
├── 决策类/
│   ├── decisions.json
│   ├── rationales.json
│   ├── assumptions.json
│   └── changes.json
├── 承诺类/
│   ├── commitments.json
│   └── expectations.json
├── 过程类/
│   ├── progress.json
│   ├── dependencies.json
│   └── resources.json
├── 知识类/
│   ├── learnings.json
│   ├── insights.json
│   └── contexts.json
└── 人物类/
    └── stakeholders.json
```

---

## 五、查询命令

```
用户: 有什么时间节点？     → deadlines + milestones
用户: 有哪些遗留问题？     → issues + blockers
用户: 做过什么决策？       → decisions + rationales
用户: 我承诺过什么？       → commitments
用户: 有什么风险？         → risks
用户: 卡在什么地方？       → blockers
用户: 依赖什么？           → dependencies
用户: 最近有什么想法？     → insights
用户: 项目背景是什么？     → contexts
用户: 涉及哪些人？         → stakeholders
用户: 有什么假设前提？     → assumptions
用户: 改过什么？           → changes
用户: 显示所有记录         → 全部记录
```

---

## 六、使用示例

### 场景 1：时间节点检测
```
用户: "项目要在3月20日前完成"
→ 自动记录:
  type: deadline
  title: 项目完成
  datetime: 2026-03-20
  context: 项目交付时间
```

### 场景 2：决策记录
```
用户: "决定用 PostgreSQL，因为团队熟悉度高"
→ 自动记录:
  type: decision
  title: 选择 PostgreSQL
  rationale: 团队熟悉度高
```

### 场景 3：问题捕获
```
报告: "性能优化尚未完成，卡在缺少测试环境"
→ 自动记录:
  type: issue
  title: 性能优化未完成
  blocker: 缺少测试环境
```

### 场景 4：承诺记录
```
用户: "我会明天把文档发给你"
→ 自动记录:
  type: commitment
  title: 发送文档
  deadline: 2026-03-13
```

---

## 七、定期回顾

建议配置定期回顾任务：

| 任务 | 时间 | 内容 |
|------|------|------|
| 晨间提醒 | 08:00 | 今日 deadline + pending commitments |
| 晚间回顾 | 21:00 | 今日记录汇总 + 明日关注点 |
| 周度盘点 | 周五 18:00 | 本周决策 + 遗留问题 + 风险项 |

---

## 八、注意事项

### 记录原则
1. **保持原始性** — 保留原始文本，便于追溯
2. **及时性** — 发现即记录，不延迟
3. **关联性** — 关联相关记录（如决策+原因）
4. **可追溯** — 记录来源和时间

### 隐私保护
- 敏感信息不记录（密码、密钥等）
- 个人隐私信息脱敏处理

---

## 九、文件位置

| 文件 | 路径 |
|------|------|
| 主记录库 | `~/.openclaw/workspace/.keyrecords/records.json` |
| 检测模式 | `~/.openclaw/workspace/skills/key-tracker/references/patterns.md` |
| 关键词库 | `~/.openclaw/workspace/skills/key-tracker/references/keywords.md` |

---

**外置大脑，让每一次思考都有痕迹。**