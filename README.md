# NovelForge — AI网文创作工作台 🚀

从一句话创意到百万字长篇，AI 辅助你完成设定、大纲、写作全流程。

## 核心功能

| 功能 | 说明 |
|------|------|
| 🧠 **AI创作中心** | 题材建议、大纲生成、角色设计、世界观构建、一键全书 |
| 🗣️ **对话式创作向导** | 点击按钮即可完成小说设定，无需动脑 |
| 📝 **AI章节编辑器** | 续写、润色、扩写、去AI味，9种AI操作 |
| 📕 **Book Bible 设定锁定** | 核心设定永不跑偏，AI生成自动读取 |
| 🎭 **伏笔管理** | 自动追踪伏笔埋设与回收 |
| 💡 **AI实时建议** | 写作时自动分析节奏、AI腔、爽点 |

## 部署到云端（让朋友点链接就能用）

### 第1步：上传到 GitHub

```bash
cd D:/Hermes/novelforge
git remote set-url origin https://github.com/smf211/test001novel.git
git push -u origin main
```

或者在网页 https://github.com/smf211/test001novel 点 **Add file → Upload files**，把整个 `novelforge` 文件夹拖进去（排除 node_modules、.next、dev.db）

### 第2步：创建 Turso 数据库

1. 打开 https://turso.tech 注册
2. 点 **Create Database** → 名称 `novelforge` → 区域选 **Singapore**
3. 点 **Generate Token** → 复制 URL 和 Token

### 第3步：部署到 Vercel

1. 打开 https://vercel.com/new
2. 导入 `smf211/test001novel` 仓库
3. 添加环境变量：

| 变量名 | 值 |
|-------|-----|
| `TURSO_DATABASE_URL` | `libsql://novelforge-xxx.turso.io` |
| `TURSO_AUTH_TOKEN` | `eyJ...` |

4. 点 **Deploy**，等2分钟

### 第4步：初始化数据

部署成功后访问：
```
https://你的域名/api/seed
```
会自动创建一本示例小说和样例数据。

## 本地开发

```bash
npm install
npx prisma generate
npx prisma db push
node seed.js
npm run dev
```

## 技术栈

- **前端:** Next.js 16 + React 19 + Tailwind CSS 4
- **数据库:** Prisma 7 + SQLite (本地) / Turso (云端)
- **AI引擎:** DeepSeek / OpenAI / Claude 多Provider
