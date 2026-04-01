# AIStore 使用与部署手册

---

## 目录

1. [快速开始](#快速开始)
2. [环境配置](#环境配置)
3. [开发指南](#开发指南)
4. [部署指南](#部署指南)
5. [内容管理](#内容管理)
6. [自定义配置](#自定义配置)
7. [故障排查](#故障排查)

---

## 快速开始

### 前置要求

- Node.js 18+ 
- npm 或 pnpm
- Vercel CLI（可选，用于部署）

### 本地运行

```bash
# 克隆仓库
git clone https://github.com/brucey0017-cloud/AIStore.git
cd AIStore

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

访问 http://localhost:3000 查看应用。

---

## 环境配置

### 必需的环境变量

创建 `.env.local` 文件：

```env
# Gemini API Key（用于 AI 功能）
GEMINI_API_KEY=your_gemini_api_key
```

### 可选的环境变量

```env
# 分析工具（可选）
NEXT_PUBLIC_ANALYTICS_ID=your_analytics_id
```

---

## 开发指南

### 项目结构详解

```
src/
├── App.tsx              # 主应用组件（路由 + 页面渲染）
├── main.tsx             # 入口文件
├── data.ts              # 静态数据（新闻/工具/术语）
├── types.ts             # TypeScript 类型定义
├── index.css            # 全局样式
├── lib/
│   └── utils.ts         # 工具函数（cn 等）
└── components/
    ├── Common.tsx       # Card, Badge 等通用组件
    ├── Effects.tsx      # 滚动进度、鼠标光效
    └── NewsCards.tsx    # ArticleCard, TimelineItem 等新闻卡片
```

### 添加新页面

1. 在 `App.tsx` 的 `View` 类型中添加新视图
2. 在 `view` useMemo 中添加路由判断
3. 创建对应的 `renderXXX()` 函数
4. 在导航中添加链接

### 修改数据

数据存储在 `src/data.ts` 中：

```typescript
// 添加新闻
export const NEWS_DATA: NewsItem[] = [
  {
    id: 'news-xxx',
    slug: 'news-slug',
    type: 'article', // 'flash' | 'article' | 'tutorial'
    title: '标题',
    summary: '摘要',
    categoryTag: '分类标签',
    cover: '封面图URL',
    date: '2026-04-01',
    readCount: 10000,
    importance: 5,
    sourceName: '来源名称',
    sourceUrl: 'https://...'
  }
]
```

---

## 部署指南

### Vercel 部署（推荐）

#### 方式一：通过 Vercel Dashboard

1. 访问 https://vercel.com
2. 点击 "New Project"
3. 导入 GitHub 仓库 `brucey0017-cloud/AIStore`
4. 配置环境变量
5. 点击 "Deploy"

#### 方式二：通过 CLI

```bash
# 安装 Vercel CLI
npm install -g vercel

# 登录
vercel login

# 部署到预览环境
vercel

# 部署到生产环境
vercel --prod
```

### 自动部署配置

Vercel 会自动检测 `main` 分支的推送并触发部署。

### 自定义域名

1. 在 Vercel Dashboard 中进入项目设置
2. 点击 "Domains"
3. 添加自定义域名
4. 配置 DNS 记录

---

## 内容管理

### 更新新闻数据

编辑 `src/data.ts`：

```typescript
export const NEWS_DATA: NewsItem[] = [
  // 添加或修改新闻条目
]
```

### 更新术语百科

```typescript
export const GLOSSARY_DATA: GlossaryItem[] = [
  {
    id: 'term-xxx',
    term: '术语名称',
    definition: '术语定义'
  }
]
```

### 更新工具推荐

```typescript
export const TOOLS_DATA: Record<string, Tool> = {
  'tool-id': {
    id: 'tool-id',
    name: '工具名称',
    tagline: '一句话介绍',
    description: '详细描述',
    logo: 'Logo URL',
    features: ['特性1', '特性2'],
    officialUrl: 'https://...'
  }
}
```

---

## 自定义配置

### 修改主题色

编辑 `src/index.css`：

```css
:root {
  --brand-primary: #1ed661;  /* 主色 */
  --brand-accent: #4aa3ff;   /* 强调色 */
}
```

### 修改导航

编辑 `src/App.tsx` 中的 `<nav>` 部分：

```tsx
<a href="#/your-page">新页面</a>
```

### 添加分析工具

在 `index.html` 中添加脚本：

```html
<script async src="https://your-analytics.com/script.js"></script>
```

---

## 故障排查

### 构建失败

**问题**：`npm run build` 报错

**解决**：
```bash
# 清理缓存
rm -rf node_modules dist
npm install
npm run build
```

### Vercel 部署失败

**问题**：部署超时或失败

**解决**：
1. 检查 `vercel.json` 配置
2. 确保环境变量已设置
3. 查看 Vercel Dashboard 的构建日志

### 样式不生效

**问题**：Tailwind 样式未生效

**解决**：
```bash
# 重新生成 Tailwind 样式
npm run build
```

### 路由不工作

**问题**：页面刷新后 404

**解决**：
确保 `vercel.json` 中有重写规则：

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

---

## 联系与支持

- **GitHub Issues**: https://github.com/brucey0017-cloud/AIStore/issues
- **文档**: [README.md](./README.md)

---

© 2026 AIStore 传媒集团
