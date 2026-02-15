# Day 4：Skills 系统

> 🎯 **学习目标**：安装和创建 OpenClaw Skills

## Skills 概念

Skills 教 Agent 使用特定工具和完成特定任务：

- 遵循 [AgentSkills](https://agentskills.io) 标准
- 可以从 ClawHub 安装
- 可以自定义创建

## Skills 位置

```
~/.openclaw/skills/          # 全局 Skills
~/.openclaw/workspace/skills/ # 工作空间 Skills
```

## ClawHub 安装

浏览并安装社区 Skills：

```bash
# 浏览 Skills
open https://clawhub.com

# 安装 Skill
clawhub install <skill-name>

# 更新所有 Skills
clawhub update --all
```

## 内置 Skills

OpenClaw 自带一些常用 Skills：

| Skill | 用途 |
|-------|-----|
| `weather` | 天气查询 |
| `github` | GitHub 操作 |
| `tmux` | 远程会话控制 |
| `coding-agent` | 代码助手 |

## 创建自定义 Skill

### 目录结构

```
~/.openclaw/skills/my-skill/
└── SKILL.md
```

### SKILL.md 格式

```markdown
---
name: daily-report
description: Generate daily work report
---

# Daily Report

Generate a daily work report including:

1. **Tasks Completed Today**
   - List all completed tasks
   - Note any blockers resolved

2. **In Progress**
   - Tasks currently being worked on
   - Expected completion

3. **Tomorrow's Plan**
   - Priority tasks
   - Meetings scheduled
```

## 高级配置

### 环境要求

```yaml
---
name: my-skill
description: My custom skill
metadata:
  {
    "openclaw":
      {
        "requires": { "bins": ["uv"], "env": ["API_KEY"] },
      },
  }
---
```

### API Key 注入

在 `openclaw.json` 中配置：

```json
{
  "skills": {
    "entries": {
      "my-skill": {
        "enabled": true,
        "apiKey": "xxx"
      }
    }
  }
}
```

## 禁用 Skills

```json
{
  "skills": {
    "entries": {
      "some-skill": { "enabled": false }
    }
  }
}
```

## ✅ 今日练习

- [ ] 浏览 ClawHub 上的 Skills
- [ ] 安装一个感兴趣的 Skill
- [ ] 创建一个简单的自定义 Skill
- [ ] 测试 Skill 是否正常工作

---

[← 上一天](day3-workspace.md) | [下一天：Cron 定时任务 →](day5-cron.md)
