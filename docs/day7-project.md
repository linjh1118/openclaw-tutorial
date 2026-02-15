# Day 7：综合项目 - 个人 AI 助手

> 🎯 **学习目标**：打造完整的个人 AI 助手工作流

## 项目目标

构建一个跨设备的个人 AI 助手，实现：

1. **多渠道接入**：Telegram + 飞书（或其他）
2. **自定义人格**：配置 SOUL.md 和 IDENTITY.md
3. **定时任务**：每日天气/日程提醒
4. **自定义 Skills**：至少 2 个
5. **记忆管理**：配置 memory 目录

## 配置清单

```
~/.openclaw/
├── openclaw.json           # 多渠道 + Cron 配置
├── workspace/
│   ├── AGENTS.md           # 行为规范
│   ├── SOUL.md             # 人格设定
│   ├── USER.md             # 用户信息
│   ├── IDENTITY.md         # Agent 身份
│   ├── TOOLS.md            # 工具配置
│   ├── HEARTBEAT.md        # 心跳任务
│   └── memory/             # 记忆存储
└── skills/
    ├── skill-1/
    │   └── SKILL.md
    └── skill-2/
        └── SKILL.md
```

## Step by Step

### Step 1: 配置多渠道

编辑 `~/.openclaw/openclaw.json`：

```json
{
  "channels": {
    "telegram": {
      "token": "xxx",
      "allowFrom": ["your_id"]
    },
    "feishu": {
      "appId": "xxx",
      "appSecret": "xxx"
    }
  }
}
```

### Step 2: 配置 Agent 身份

编辑 `~/.openclaw/workspace/IDENTITY.md`：

```markdown
# IDENTITY.md

- **Name**: [你的 Agent 名字]
- **Creature**: AI 助手
- **Vibe**: [描述性格]
- **Emoji**: 🤖
```

### Step 3: 配置用户信息

编辑 `~/.openclaw/workspace/USER.md`：

```markdown
# USER.md

- **Name**: [你的名字]
- **Timezone**: Asia/Shanghai
- **Notes**: [任何偏好]
```

### Step 4: 创建 Skills

创建 `~/.openclaw/skills/daily-weather/SKILL.md`：

```markdown
---
name: daily-weather
description: Get weather forecast
---

查询指定城市的天气预报，包括：
- 当前温度和天气状况
- 今日最高/最低温度
- 是否需要带伞
```

### Step 5: 配置 Cron

添加到 `openclaw.json`：

```json
{
  "cron": {
    "jobs": [
      {
        "name": "morning-weather",
        "schedule": {
          "kind": "cron",
          "expr": "0 7 * * *",
          "tz": "Asia/Shanghai"
        },
        "payload": {
          "kind": "agentTurn",
          "message": "早上好！请告诉我今天的天气"
        },
        "sessionTarget": "isolated"
      }
    ]
  }
}
```

### Step 6: 配置 Heartbeat

创建 `~/.openclaw/workspace/HEARTBEAT.md`：

```markdown
# HEARTBEAT.md

## 检查项
- 整理 memory 文件
- 检查是否有遗漏的任务
```

### Step 7: 测试

```bash
# 重启 Gateway
openclaw gateway restart

# 检查状态
openclaw status

# 从两个渠道发送消息测试
```

## 验收标准

- [ ] 能从两个渠道和 AI 助手对话
- [ ] Agent 知道自己的名字和身份
- [ ] 每天早上收到天气提醒
- [ ] 自定义 Skill 能正常工作
- [ ] AI 能记住之前的对话内容

## 交付物

1. **完整的配置文件**
2. **演示截图/录屏**
3. **课程总结报告**（1000字）：
   - 学到了什么
   - 遇到的挑战
   - 对 AI 助手的思考
   - 未来改进计划

## 评分标准

| 项目 | 分值 |
|-----|------|
| 多渠道配置 | 20% |
| Agent 人格 | 15% |
| Skills | 20% |
| Cron/Heartbeat | 20% |
| 课程总结 | 25% |

---

🎉 **恭喜完成 OpenClaw 学习！**

现在你已经拥有了一个跨设备的个人 AI 助手！
