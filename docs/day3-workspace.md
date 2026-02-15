# Day 3：Agent 工作空间

> 🎯 **学习目标**：理解和配置 Agent 的工作空间

## 工作空间结构

```
~/.openclaw/workspace/
├── AGENTS.md      # Agent 行为指南
├── SOUL.md        # Agent 人格设定
├── USER.md        # 用户信息
├── TOOLS.md       # 工具配置笔记
├── HEARTBEAT.md   # 心跳任务
├── IDENTITY.md    # Agent 身份
└── memory/        # 记忆存储
    ├── 2024-01-01.md
    └── ...
```

## 核心文件

### SOUL.md - Agent 的人格

定义 Agent 的性格和行为准则：

```markdown
# SOUL.md - Who You Are

Be genuinely helpful, not performatively helpful.
Skip the "Great question!" — just help.

Have opinions. An assistant with no personality is just a search engine.

Be resourceful before asking. Try to figure it out first.

Remember you're a guest. Treat access to someone's data with respect.
```

### USER.md - 用户信息

告诉 Agent 关于你的信息：

```markdown
# USER.md - About Your Human

- **Name**: 你的名字
- **What to call them**: 怎么称呼你
- **Timezone**: Asia/Shanghai
- **Notes**: 任何偏好或注意事项
```

### IDENTITY.md - Agent 身份

给你的 Agent 一个身份：

```markdown
# IDENTITY.md

- **Name**: Jarvis
- **Creature**: AI 助手
- **Vibe**: 靠谱、有温度、偶尔幽默
- **Emoji**: 🤖
```

## 记忆系统

### 日常记忆

Agent 会在 `memory/` 目录记录每天发生的事：

```
memory/
├── 2024-01-01.md
├── 2024-01-02.md
└── ...
```

### 长期记忆

`MEMORY.md` 用于存储长期重要的信息：

```markdown
# MEMORY.md

## 重要决定
- 2024-01-01: 决定使用 TypeScript
- 2024-01-05: 项目架构确定

## 用户偏好
- 喜欢简洁的回复
- 晚上 11 点后不要打扰
```

## AGENTS.md - 行为规范

定义 Agent 的行为规则：

```markdown
# AGENTS.md

## 每次会话
1. 读 SOUL.md — 记住我是谁
2. 读 USER.md — 记住用户是谁
3. 读 memory/YYYY-MM-DD.md — 近期上下文

## 安全规则
- 不泄露私人数据
- 不执行危险命令
- 不确定时先问

## 群聊规则
- 不是每条消息都要回复
- 质量 > 数量
```

## 自定义你的 Agent

### Step 1: 编辑 IDENTITY.md

```bash
vim ~/.openclaw/workspace/IDENTITY.md
```

给 Agent 一个名字和性格。

### Step 2: 编辑 USER.md

告诉 Agent 关于你的信息。

### Step 3: 编辑 SOUL.md

调整 Agent 的行为准则。

## ✅ 今日练习

- [ ] 阅读默认的工作空间文件
- [ ] 自定义 IDENTITY.md（给 Agent 取名）
- [ ] 编辑 USER.md（添加你的信息）
- [ ] 测试 Agent 是否记住了这些配置

---

[← 上一天](day2-channels.md) | [下一天：Skills 系统 →](day4-skills.md)
