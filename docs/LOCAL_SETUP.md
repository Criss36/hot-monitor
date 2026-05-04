# 🚀 本地运行指南

本文档手把手教你在本地跑起来 AI 热点监控工具的完整前后端。

## 📋 前置要求

| 工具 | 版本要求 | 检查命令 |
|------|----------|----------|
| 🟢 Node.js | ≥ 18 | `node -v` |
| 📦 npm | ≥ 9 | `npm -v` |
| 📚 Git | 任意 | `git --version` |

> 💡 推荐使用 Node.js 20 LTS 版本。

## 第一步：克隆项目

```bash
git clone <your-repo-url>.git
cd hot-monitor
```

## 第二步：获取 API Key

项目需要 **1 个必需的 API Key**，另外 2 个为可选。

### ✅ 必需：OpenRouter API Key

OpenRouter 是一个统一的 AI 大模型接入平台，注册即可使用。

1. 打开 [https://openrouter.ai/](https://openrouter.ai/)，注册并登录
2. 进入 [API Keys 页面](https://openrouter.ai/settings/keys)
3. 点击 **Create Key**，复制生成的 Key（以 `sk-or-v1-` 开头）
4. 确保账户有一定额度（新用户通常有免费额度）

### 🔧 可选：Twitter API Key

配置后可以从 Twitter/X 获取国际热点信息。

1. 打开 [https://twitterapi.io/](https://twitterapi.io/)，注册并登录
2. 进入 [Dashboard](https://twitterapi.io/dashboard)
3. 复制你的 API Key

### 🔧 可选：邮件通知

配置后系统会在发现高重要性热点时自动发送邮件提醒。

需要准备 SMTP 邮箱信息（以 QQ 邮箱为例）：
- 📧 SMTP 地址：`smtp.qq.com`
- 🔢 端口：`465`
- 👤 账号：你的 QQ 邮箱
- 🔑 密码：QQ 邮箱的 **授权码**

## 第三步：配置环境变量

```bash
cp server/.env.example server/.env
```

编辑 `server/.env` 文件：

```env
DATABASE_URL="file:./dev.db"
PORT=3001
CLIENT_URL=http://localhost:5173

OPENROUTER_API_KEY=sk-or-v1-你的key
TWITTER_API_KEY=你的twitter_api_key  # 可选

SMTP_HOST=smtp.qq.com
SMTP_PORT=465
SMTP_SECURE=true
SMTP_USER=你的邮箱@qq.com
SMTP_PASS=你的授权码
NOTIFY_EMAIL=接收通知的邮箱@example.com
```

> ⚠️ 注意：`.env` 文件包含敏感信息，已被 `.gitignore` 排除。

## 第四步：安装依赖

```bash
cd server
npm install

cd ../client
npm install
```

## 第五步：初始化数据库

```bash
cd server
npx prisma generate
npx prisma db push
```

## 第六步：启动项目

需要同时启动后端和前端，打开两个终端窗口：

```bash
# 终端 1：后端
cd server
npm run dev

# 终端 2：前端
cd client
npm run dev
```

访问 **http://localhost:5173** 🎉

## 🔌 端口汇总

| 服务 | 默认端口 | 说明 |
|------|----------|------|
| ⚙️ 后端 API | 3001 | Express + Socket.io |
| 🌐 前端页面 | 5173 | Vite 开发服务器 |
| 🗄️ Prisma Studio | 5555 | 数据库可视化（可选） |
