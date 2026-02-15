# Day 5：Cron 定时任务

> 🎯 **学习目标**：配置定时任务实现自动化

## Cron 任务类型

| 类型 | 说明 | 示例 |
|-----|------|-----|
| `at` | 一次性任务 | 20分钟后提醒我 |
| `every` | 间隔执行 | 每小时检查一次 |
| `cron` | Cron 表达式 | 每天早上 9 点 |

## 通过对话创建

最简单的方式是直接告诉 Agent：

```
帮我创建一个提醒：20分钟后提醒我喝水

每天早上 9 点告诉我今天的天气

每周一早上 10 点提醒我写周报
```

## 配置文件方式

在 `openclaw.json` 中配置：

### 一次性任务 (at)

```json
{
  "cron": {
    "jobs": [
      {
        "name": "reminder",
        "schedule": {
          "kind": "at",
          "at": "2024-01-01T10:00:00+08:00"
        },
        "payload": {
          "kind": "agentTurn",
          "message": "提醒：该喝水了！"
        },
        "sessionTarget": "isolated"
      }
    ]
  }
}
```

### 间隔执行 (every)

```json
{
  "schedule": {
    "kind": "every",
    "everyMs": 3600000  // 每小时
  }
}
```

### Cron 表达式

```json
{
  "schedule": {
    "kind": "cron",
    "expr": "0 9 * * 1-5",  // 工作日早上 9 点
    "tz": "Asia/Shanghai"
  }
}
```

## Payload 类型

### systemEvent

注入系统事件到主会话：

```json
{
  "payload": {
    "kind": "systemEvent",
    "text": "该检查邮件了"
  },
  "sessionTarget": "main"
}
```

### agentTurn

在独立会话运行 Agent：

```json
{
  "payload": {
    "kind": "agentTurn",
    "message": "检查天气并告诉用户"
  },
  "sessionTarget": "isolated"
}
```

## 管理 Cron 任务

```bash
# 列出所有任务
openclaw cron list

# 运行指定任务
openclaw cron run --job <job-id>

# 查看任务历史
openclaw cron runs --job <job-id>
```

## 常用示例

### 每日天气提醒

```json
{
  "name": "daily-weather",
  "schedule": {
    "kind": "cron",
    "expr": "0 7 * * *",
    "tz": "Asia/Shanghai"
  },
  "payload": {
    "kind": "agentTurn",
    "message": "查询今天的天气，并发送给我"
  },
  "sessionTarget": "isolated"
}
```

### 工作日站会提醒

```json
{
  "name": "standup-reminder",
  "schedule": {
    "kind": "cron",
    "expr": "50 9 * * 1-5",
    "tz": "Asia/Shanghai"
  },
  "payload": {
    "kind": "agentTurn",
    "message": "提醒：10分钟后站会"
  },
  "sessionTarget": "isolated"
}
```

## ✅ 今日练习

- [ ] 通过对话创建一个简单的一次性提醒
- [ ] 在配置文件中创建一个每日任务
- [ ] 使用 `openclaw cron list` 查看任务
- [ ] 手动触发一个任务测试

---

[← 上一天](day4-skills.md) | [下一天：Heartbeat →](day6-heartbeat.md)
