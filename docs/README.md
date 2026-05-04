# 🔥 热点监控工具

> ✨ 一款自动发现热点、智能识别真假内容、实时推送通知的 AI 工具

## 📋 项目概述

热点监控工具可以：
- 🔍 自动监控指定关键词的热点变化
- 🤖 利用 AI 识别假冒内容
- 📬 第一时间发送通知
- ⏰ 定期收集指定范围内的热点信息

## 🎯 核心功能

### 1️⃣ 关键词监控
- 用户输入要监控的关键词
- 当关键词相关内容出现时，AI 识别真假
- 第一时间发送通知

### 2️⃣ 热点收集
- 每 30 分钟自动收集指定范围内的热点
- 多数据源聚合，确保信息全面
- AI 分析热点价值和可信度

### 3️⃣ 通知系统
- 🌐 浏览器实时推送 (WebSocket)
- 📧 邮件通知 (SMTP)

## 🛠️ 技术栈

| 层级 | 技术 | 说明 |
|------|------|------|
| 前端 | React + Vite + TailwindCSS | 响应式、赛博朋克风格 UI |
| 后端 | Node.js + Express | 轻量级 API 服务 |
| 数据库 | SQLite + Prisma | 轻量存储、ORM |
| AI 服务 | OpenRouter API | 热点验证、内容分析 |
| 定时任务 | node-cron | 定时热点抓取 |
| 实时通信 | Socket.io | 浏览器推送 |
| 邮件 | Nodemailer | 邮件通知 |

## 📊 数据源

| 来源 | 方式 | 说明 |
|------|------|------|
| 🌐 网页搜索 | Bing/Google 爬虫 | 无需 API，控制频率 |
| 🐦 Twitter/X | twitterapi.io | 官方 API 接口 |
| 🔄 聚合处理 | 多源去重 + AI 分析 | 确保信息质量 |

## 📁 项目结构

```
hot-monitor/
├── client/                  # 📦 前端应用
│   ├── src/
│   │   ├── components/     # 🎨 UI 组件
│   │   ├── services/       # 🔗 API 调用
│   │   └── utils/          # 🔧 工具函数
│   └── package.json
├── server/                  # ⚙️ 后端服务
│   ├── src/
│   │   ├── routes/         # 🛤️ API 路由
│   │   ├── services/       # 💼 业务逻辑
│   │   ├── jobs/           # ⏰ 定时任务
│   │   └── utils/          # 🔧 工具函数
│   ├── prisma/             # 🗄️ Prisma ORM
│   └── package.json
├── skills/                  # 🎯 Agent Skills
│   └── hot-monitor/        # 🔥 热点监控技能
└── .env.example            # ⚙️ 环境变量模板
```

## ⚙️ 配置说明

```env
OPENROUTER_API_KEY=your_openrouter_key
TWITTER_API_KEY=your_twitter_api_key
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your_email
SMTP_PASS=your_password
NOTIFY_EMAIL=receive@example.com
MONITOR_INTERVAL=1800000  # 30分钟
```

## 🚀 快速开始

```bash
# 1️⃣ 安装依赖
cd server && npm install
cd client && npm install

# 2️⃣ 配置环境变量
cp .env.example .env
# 编辑 .env 文件填入你的 API Keys

# 3️⃣ 初始化数据库
cd server && npx prisma migrate dev

# 4️⃣ 启动服务
cd server && npm run dev
cd client && npm run dev
```
