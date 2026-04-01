<div align="center">

# AIStore 资讯

**专业 AI 资讯，一站直达**

</div>

---

## 简介

AIStore 是一个 AI 资讯聚合平台
帮助用户快速获取 AI 行业动态、技能教程、模型评测和安全资讯。

**核心功能：**
- 📰 **AI 快讯** - 实时行业动态
- 📚 **深度好文** - 精选长文解读
- 🎓 **精选教程** - 实战技能教程
- 📖 **术语百科** - AI 术语速查
- 🎬 **优质视频** - 视频内容聚合
- 🎙️ **AI 播客** - 音频节目收听
- 🛡️ **安全实验室** - AI 安全与合规
- 🔧 **Skill / MCP / 大模型** - 分类内容入口

---

## 在线访问

- **生产环境**: https://aistore-copywriting.vercel.app
- **GitHub 仓库**: https://github.com/brucey0017-cloud/AIStore

---

## 本地开发

### 环境要求

- Node.js >= 18.0.0
- npm >= 9.0.0

### 快速开始

```bash
# 克隆仓库
git clone https://github.com/brucey0017-cloud/AIStore.git
cd AIStore

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

访问 http://localhost:3000

### 构建生产版本

```bash
npm run build
npm run preview
```

---

## 项目结构

```
AIStore/
├── src/
│   ├── App.tsx          # 主应用（路由 + 页面渲染）
│   ├── data.ts          # 数据源
│   ├── types.ts         # TypeScript 类型定义
│   ├── main.tsx         # 入口文件
│   ├── index.css        # 全局样式
│   ├── lib/             # 工具函数
│   └── components/      # UI 组件
│       ├── Common.tsx   # 通用组件
│       ├── Effects.tsx  # 动效组件
│       └── NewsCards.tsx # 新闻卡片组件
├── public/              # 静态资源
├── index.html           # HTML 模板
├── package.json         # 项目配置
├── tailwind.config.js   # Tailwind 配置
└── vite.config.ts       # Vite 配置
```

---

## 技术栈

| 技术 | 版本 | 用途 |
|------|------|------|
| React | 19.0.0 | UI 框架 |
| Vite | 6.2.0 | 构建工具 |
| Tailwind CSS | 4.1.14 | 样式框架 |
| Motion | 12.38.0 | 动画库 |
| Lucide React | 0.546.0 | 图标库 |

---

## 页面路由

| 路由 | 页面 | 说明 |
|------|------|------|
| `#/` | 首页 | Hero + 5 入口卡片 |
| `#/portal` | AI 百科 | 资讯聚合页 |
| `#/list?tab=xxx` | 列表页 | 6 个 tab（快讯/好文/教程/百科/视频/播客） |
| `#/detail/:slug` | 文章详情 | 深度阅读页 |
| `#/term/:id` | 术语详情 | 术语百科页 |
| `#/video/:slug` | 视频详情 | 视频播放页 |
| `#/podcast/:slug` | 播客详情 | 音频播放页 |
| `#/learning-path` | 学习路径 | 7 天学习计划 |
| `#/section/:key` | 分类页 | skill/mcp/model/security |

---

## 部署

### Vercel 部署（推荐）

```bash
# 安装 Vercel CLI
npm install -g vercel

# 登录
vercel login

# 部署到生产环境
vercel --prod
```

### 自动部署

仓库已连接 Vercel
推送到 `main` 分支会自动触发部署。

---

## 文案优化记录

本项目使用 [copywriting-rewriter skill](https://github.com/brucey0017-cloud/copywriting-rewriter) 进行文案优化。

详见 [COPYWRITING_CHANGES.md](./COPYWRITING_CHANGES.md)

---

## License

MIT

---

## 贡献

欢迎提交 Issue 和 Pull Request！

---

© 2026 AIStore 传媒集团。保留所有权利。
