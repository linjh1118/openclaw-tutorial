# Day 1：环境搭建

> 🎯 **学习目标**：安装 OpenClaw 并连接第一个聊天渠道

## 什么是 OpenClaw

OpenClaw 是一个自托管的 AI 助手网关：

- 🔗 **多渠道**：WhatsApp/Telegram/Discord/飞书等
- 🏠 **自托管**：数据在你自己的机器上
- 🤖 **Agent 原生**：支持工具使用、记忆、多 Agent
- 🔓 **开源**：MIT 协议

## 安装

### 1. 检查 Node 版本

```bash
node -v
# 需要 22+
```

### 2. 安装 OpenClaw

```bash
npm i -g openclaw
```

### 3. 首次运行

```bash
openclaw
```

首次运行会进入交互式配置，设置 API Key 等。

## 配置飞书

### Step 1: 创建应用

1. 登录 [飞书开放平台](https://open.feishu.cn)
2. 创建企业自建应用
3. 开启「机器人」能力
4. 获取 App ID 和 App Secret
5. 配置事件订阅（WebSocket 方式）

### Step 2: 配置 OpenClaw

```bash
openclaw configure --section feishu
# 输入 App ID 和 App Secret
```

### Step 3: 重启 Gateway

```bash
openclaw gateway restart
```

### Step 4: 测试

在飞书给你的机器人发消息，收到 AI 回复！

## 其他渠道

不同渠道的配置难度：

| 渠道 | 难度 | 说明 |
|-----|-----|------|
| 飞书 | ⭐⭐ | 需配置机器人（本教程使用）|
| Telegram | ⭐ | 只需 bot token |
| Discord | ⭐⭐ | 需创建 Discord 应用 |
| WhatsApp | ⭐⭐⭐ | 需 QR 码配对 |

## 常用命令

```bash
# 启动 Gateway
openclaw gateway start

# 停止 Gateway
openclaw gateway stop

# 重启 Gateway
openclaw gateway restart

# 查看状态
openclaw status
```

## 配置文件位置

```
~/.openclaw/
├── openclaw.json      # 主配置
├── workspace/         # Agent 工作空间
└── skills/            # 自定义 Skills
```

## ✅ 今日练习

- [ ] 安装 OpenClaw
- [ ] 在飞书开放平台创建应用并获取凭证
- [ ] 配置并连接飞书
- [ ] 发送第一条消息，收到 AI 回复
- [ ] 运行 `openclaw status` 检查状态

---

[下一天：多渠道配置 →](day2-channels.md)
