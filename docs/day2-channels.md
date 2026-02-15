# Day 2：多渠道配置

> 🎯 **学习目标**：配置多个聊天渠道

## 支持的渠道

| 渠道 | 特点 |
|-----|------|
| Telegram | 最简单，Bot API |
| Discord | 服务器/频道/DM |
| 飞书 | 企业常用，WebSocket |
| WhatsApp | 需要 QR 配对 |
| Signal | 隐私优先 |
| iMessage | 仅 macOS |
| Slack | 工作空间应用 |

## 飞书配置

### Step 1: 创建应用

1. 登录 [飞书开放平台](https://open.feishu.cn)
2. 创建企业自建应用
3. 开启机器人能力
4. 获取 App ID 和 App Secret

### Step 2: 配置 OpenClaw

```bash
openclaw configure --section feishu
```

或直接编辑配置：

```json
{
  "channels": {
    "feishu": {
      "appId": "cli_xxx",
      "appSecret": "xxx"
    }
  }
}
```

### Step 3: 配置事件订阅

在飞书开放平台配置：
- 消息接收事件
- WebSocket 方式（推荐）

## Discord 配置

### Step 1: 创建应用

1. 登录 [Discord Developer Portal](https://discord.com/developers)
2. 创建 Application
3. 在 Bot 页面创建 Bot
4. 获取 Token
5. 生成邀请链接，添加到服务器

### Step 2: 配置 OpenClaw

```bash
openclaw configure --section discord
```

```json
{
  "channels": {
    "discord": {
      "token": "xxx"
    }
  }
}
```

## 同时运行多渠道

配置文件中可以同时配置多个渠道：

```json
{
  "channels": {
    "telegram": {
      "token": "xxx"
    },
    "discord": {
      "token": "xxx"
    },
    "feishu": {
      "appId": "xxx",
      "appSecret": "xxx"
    }
  }
}
```

OpenClaw 会同时连接所有配置的渠道。

## 安全配置

### 限制允许的用户

```json
{
  "channels": {
    "telegram": {
      "token": "xxx",
      "allowFrom": ["your_telegram_id"]
    }
  }
}
```

### 群聊需要 @ 提及

```json
{
  "channels": {
    "telegram": {
      "token": "xxx",
      "groups": {
        "*": { "requireMention": true }
      }
    }
  }
}
```

## 检查渠道状态

```bash
openclaw status
```

## ✅ 今日练习

- [ ] 选择并配置第二个聊天渠道
- [ ] 测试两个渠道都能正常工作
- [ ] 配置安全限制（allowFrom）
- [ ] 使用 `openclaw status` 检查所有渠道

---

[← 上一天](day1-setup.md) | [下一天：Agent 工作空间 →](day3-workspace.md)
