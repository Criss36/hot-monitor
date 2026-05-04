# 🔥 AI 热点监控工具

> ✨ 自动发现热点、智能识别真假内容、实时推送通知的 AI 工具

## 📖 项目介绍

这是一套 **AI 热点监控工具**，基于 Express 5 + React 19 + OpenRouter + Socket.io 开发。输入要监控的关键词，系统自动从 Twitter、Bing、HackerNews、搜狗、B 站等 **8+** 个信息源聚合抓取内容，利用 AI 进行真假识别和相关性分析，并通过 WebSocket 实时推送和邮件通知用户。此外，还将热点监控能力封装为 **Agent Skills 技能包**，让 Cursor、VSCode Copilot、Claude Code 等 AI 编程工具也能直接使用。

### 🚀 核心能力

1. ⚙️ **配置监控关键词** - 支持激活/暂停
2. 🌐 **多源聚合抓取** - 从 8+ 数据源获取热点信息
3. 🤖 **AI 智能分析** - 真假识别、相关性分析、智能摘要
4. 🔍 **多维度筛选排序** - 按来源、重要性、时间范围筛选
5. 📬 **实时通知** - WebSocket 实时推送 + 邮件通知
6. 🛠️ **Agent Skills** - 可被 AI 编程工具直接调用

### 🏗️ 技术栈

| 层级 | 技术 |
|------|------|
| 前端 | React + Vite + TailwindCSS + Aceternity UI |
| 后端 | Node.js + Express 5 |
| 数据库 | SQLite + Prisma |
| AI 服务 | OpenRouter API |
| 实时通信 | Socket.io |

## 🚴 快速运行

### 📋 前置条件

- Node.js ≥ 18（推荐 20 LTS）
- 一个 [OpenRouter API Key](https://openrouter.ai/settings/keys)

### 1️⃣ 克隆并安装依赖

```bash
git clone <your-repo-url>.git
cd hot-monitor

# 后端
cd server
npm install
npx prisma generate
npx prisma db push

# 前端
cd ../client
npm install
```

### 2️⃣ 配置环境变量

```bash
cp server/.env.example server/.env
```

编辑 `server/.env`，填入 OpenRouter API Key：

```bash
OPENROUTER_API_KEY=sk-or-v1-你的key
TWITTER_API_KEY=你的key  # 可选
```

### 3️⃣ 启动服务

```bash
# 终端 1：后端（端口 3001）
cd server && npm run dev

# 终端 2：前端（端口 5173）
cd client && npm run dev
```

访问 **http://localhost:5173**

### 🔌 服务端口

| 服务 | 地址 |
|------|------|
| 前端页面 | http://localhost:5173 |
| 后端 API | http://localhost:3001 |
| 数据库管理 | `cd server && npx prisma studio` |

## 📁 项目结构

```
hot-monitor/
├── client/                  # 📦 前端应用
│   ├── src/
│   │   ├── components/     # 🎨 UI 组件
│   │   ├── services/       # 🔗 API 服务
│   │   └── utils/          # 🔧 工具函数
│   └── package.json
├── server/                  # ⚙️ 后端服务
│   ├── src/
│   │   ├── routes/         # 🛤️ API 路由
│   │   ├── services/       # 💼 业务逻辑
│   │   ├── jobs/           # ⏰ 定时任务
│   │   └── utils/          # 🔧 工具函数
│   ├── prisma/             # 🗄️ 数据库 schema
│   └── package.json
└── skills/                  # 🎯 Agent Skills
    └── hot-monitor/        # 🔥 热点监控技能包
```

## 📊 数据源

| 来源 | 方式 |
|------|------|
| 🌐 网页搜索 | Bing、Google、DuckDuckGo、HackerNews |
| 🇨🇳 中文搜索 | 搜狗、B 站、微博 |
| 🐦 Twitter/X | twitterapi.io |

## 📜 License

本项目采用 **MIT License** 开源协议。详见 [LICENSE](LICENSE) 文件。
