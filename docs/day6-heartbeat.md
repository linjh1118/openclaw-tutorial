# Day 6：Heartbeat

> 🎯 **学习目标**：配置心跳检查，让 Agent 主动工作

## Heartbeat vs Cron

| 特性 | Heartbeat | Cron |
|-----|-----------|------|
| 精确时间 | ❌ 大致间隔 | ✅ 精确 |
| 批量任务 | ✅ 多个检查合并 | ❌ 单任务 |
| 上下文 | ✅ 有会话历史 | ❌ 独立 |
| Token 消耗 | 较少（批量） | 较多 |

**经验法则**：
- 需要精确时间 → Cron
- 多个检查可以合并 → Heartbeat
- 需要会话上下文 → Heartbeat

## 配置 HEARTBEAT.md

在工作空间创建 `HEARTBEAT.md`：

```markdown
# HEARTBEAT.md

## 每次检查
- [ ] 有没有新邮件需要回复？
- [ ] 今天有什么日程安排？
- [ ] GitHub 有没有需要处理的 PR？

## 触发条件
- 有重要邮件 → 通知用户
- 2小时内有日程 → 提醒用户
- 其他情况 → HEARTBEAT_OK
```

## 跳过心跳

如果 HEARTBEAT.md 为空或只有注释，Agent 会跳过心跳：

```markdown
# HEARTBEAT.md
# 保持为空以跳过心跳检查
```

## 心跳行为设计

### 主动检查项

轮流检查以下内容（不要每次都检查全部）：

- **邮件** - 重要的未读邮件
- **日历** - 接下来 24-48 小时的事件
- **社交媒体** - Twitter/Slack 提及
- **天气** - 如果用户可能外出

### 何时主动联系

- 有重要邮件
- 即将有日程（<2小时）
- 发现有趣的信息
- 超过 8 小时没有交流

### 何时保持安静

- 深夜（23:00-08:00）除非紧急
- 用户明显在忙
- 距离上次检查不到 30 分钟
- 没有新内容

## 心跳状态跟踪

使用 JSON 文件跟踪检查状态：

```json
// memory/heartbeat-state.json
{
  "lastChecks": {
    "email": 1703275200,
    "calendar": 1703260800,
    "weather": null
  }
}
```

## 后台工作

心跳期间可以做的事（无需询问）：

- 整理 memory 文件
- 检查项目状态（git status）
- 更新文档
- 提交自己的改动

## 记忆维护

定期（每几天）在心跳期间：

1. 阅读最近的 `memory/YYYY-MM-DD.md`
2. 提取重要信息到 `MEMORY.md`
3. 清理过时内容

## ✅ 今日练习

- [ ] 创建 HEARTBEAT.md
- [ ] 添加 2-3 个检查项
- [ ] 观察 Agent 的心跳行为
- [ ] 对比 Heartbeat 和 Cron 的使用场景

---

[← 上一天](day5-cron.md) | [下一天：综合项目 →](day7-project.md)
