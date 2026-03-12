# 🧠 Key Tracker - 智能关键信息记录技能

> 外置大脑，自动捕获工作交流中的关键信息

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)]()
[![ClawHub](https://img.shields.io/badge/ClawHub-Ready-orange.svg)]()

---

## ✨ 核心定位

**不是**：私人秘书、日程管理工具  
**而是**：外置大脑、关键信息捕获系统

**核心价值**：
1. 不遗漏重要信息
2. 可追溯决策过程
3. 提醒待处理事项
4. 沉淀知识经验
5. 跟踪进展状态

---

## 📋 16 类记录类型

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

## 🚀 快速开始

### 安装

```bash
# 克隆到 skills 目录
git clone https://github.com/vincentlau2046-sudo/key-tracker.git ~/.openclaw/workspace/skills/key-tracker

# 创建记录目录
mkdir -p ~/.openclaw/workspace/.keyrecords/{时间类,问题类,决策类,承诺类,过程类,知识类,人物类}
```

### 使用

在 OpenClaw 对话中自动触发：

```
用户: "项目要在3月20日前完成"
→ 自动记录 deadline

用户: "决定用 PostgreSQL，因为团队熟悉"
→ 自动记录 decision + rationale

用户: "我会明天发给你"
→ 自动记录 commitment
```

### 查询

```
用户: 有什么时间节点？
用户: 有哪些遗留问题？
用户: 做过什么决策？
用户: 我承诺过什么？
用户: 显示所有记录
```

---

## 📁 目录结构

```
~/.openclaw/workspace/
├── .keyrecords/                    # 关键记录目录
│   ├── records.json                # 主记录库
│   ├── 时间类/
│   ├── 问题类/
│   ├── 决策类/
│   ├── 承诺类/
│   ├── 过程类/
│   ├── 知识类/
│   └── 人物类/
│
└── skills/
    └── key-tracker/
        ├── SKILL.md                # 主技能文档
        ├── _meta.json              # 元数据
        └── references/
            └── patterns.md         # 检测模式库
```

---

## 📖 记录格式

```json
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
```

---

## 🎯 使用场景

### 场景 1：时间节点检测
```
用户: "项目要在3月20日前完成"
→ 自动记录:
  type: deadline
  title: 项目完成
  datetime: 2026-03-20
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

---

## 📄 许可证

MIT License

---

## 📞 联系方式

- GitHub: https://github.com/vincentlau2046-sudo/key-tracker

---

**外置大脑，让每一次思考都有痕迹。**