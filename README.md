# 新闻中心 · 移动端

[![Vue](https://img.shields.io/badge/Vue-3.x-4FC08D)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-7.x-646CFF)](https://vite.dev/)
[![Vant](https://img.shields.io/badge/Vant-4.x-07C160)](https://vant-ui.github.io/)
[![Pinia](https://img.shields.io/badge/Pinia-2.x-F7D336)](https://pinia.vuejs.org/)
[![i18n](https://img.shields.io/badge/i18n-zh_CN_|_en_US-green)]()

> Vue 3 移动端新闻应用，与 [toutiao_backend](https://github.com/your/toutiao_backend) 配套使用。
> 完整的前后端分离实战项目，覆盖登录态管理、数据持久化、国际化。

---

## 🏗️ 前端架构

```text
┌─────────────────────────────────────────────────┐
│                   Vue 3 应用                      │
│                                                   │
│  ┌─────────────────────────────────────────────┐ │
│  │              UI 层 (Vant 4)                  │ │
│  │   NavBar · TabBar · Card · Form · Dialog     │ │
│  └──────────────────┬──────────────────────────┘ │
│                     │                             │
│  ┌──────────────────▼──────────────────────────┐ │
│  │              页面层 (11 Views)               │ │
│  │  Home · Detail · Login · Favorite · AI Chat  │ │
│  └──────────────────┬──────────────────────────┘ │
│                     │                             │
│  ┌──────────────────▼──────────────────────────┐ │
│  │            状态管理层 (Pinia 6 Stores)        │ │
│  │  user ─┬─ news ─┬─ favorites ─┬─ history     │ │
│  │        │ language │    theme   │              │ │
│  │        └─── 持久化到 localStorage ───┘        │ │
│  └──────────────────┬──────────────────────────┘ │
│                     │                             │
│  ┌──────────────────▼──────────────────────────┐ │
│  │           网络层 (Axios)                      │ │
│  │  拦截器 · Token 注入 · 错误统一处理           │ │
│  └──────────────────┬──────────────────────────┘ │
└─────────────────────┼────────────────────────────┘
                      │ HTTP
┌─────────────────────▼────────────────────────────┐
│               toutiao_backend                     │
│              FastAPI + MySQL + Redis              │
└──────────────────────────────────────────────────┘
```

---

## 📂 项目结构

```text
xwzx-news/
├── index.html                # SPA 入口
├── vite.config.js            # Vite 构建配置
├── package.json
├── src/
│   ├── main.js               # 应用启动：挂载 Vue、注册 Pinia/Router/i18n
│   ├── App.vue               # 根组件：布局 + 路由出口
│   ├── components/           # 可复用组件
│   │   ├── NewsItem.vue      #   新闻卡片（标题、摘要、来源、时间）
│   │   └── TabBar.vue        #   底部导航（首页/分类/我的）
│   ├── views/                # 页面组件
│   │   ├── Home.vue          #   首页：新闻流 + 下拉刷新
│   │   ├── Category.vue      #   分类浏览
│   │   ├── NewsDetail.vue    #   详情：Markdown 渲染 + XSS 过滤
│   │   ├── Login.vue         #   登录表单 + 校验
│   │   ├── Register.vue      #   注册表单
│   │   ├── Favorite.vue      #   收藏列表 + 取消收藏
│   │   ├── History.vue       #   浏览历史 + 清空
│   │   ├── My.vue            #   个人中心入口
│   │   ├── Profile.vue       #   编辑资料
│   │   ├── Settings.vue      #   语言/主题设置
│   │   └── AIChat.vue        #   AI 对话界面
│   ├── router/index.js       # 路由表 + 导航守卫
│   ├── store/                # Pinia 模块
│   │   ├── user.js           #   登录态、Token、用户信息
│   │   ├── news.js           #   新闻列表、分类
│   │   ├── favorites.js      #   收藏
│   │   ├── history.js        #   浏览历史
│   │   ├── language.js       #   语言偏好
│   │   └── theme.js          #   主题偏好
│   ├── i18n/                 # 国际化
│   │   ├── zh-CN.js          #   中文语言包
│   │   └── en-US.js          #   英文语言包
│   └── config/api.js         # API 基础地址
└── README.md
```

---

## 🔧 技术选型

| 决策点 | 选择 | 理由 |
|---|---|---|
| **框架** | Vue 3 Composition API | 逻辑复用方便、TypeScript 友好、生态成熟 |
| **构建** | Vite 7 | 秒级冷启动、HMR 极快、原生 ESM |
| **UI 库** | Vant 4 | 国内最成熟的移动端组件库，文档完善 |
| **状态管理** | Pinia | 官方推荐，比 Vuex 更轻量、更好的 TS 支持 |
| **持久化** | pinia-plugin-persistedstate | 登录态/偏好刷新不丢失 |
| **路由** | Vue Router 4 | 导航守卫做登录拦截 |
| **国际化** | vue-i18n | 中英文切换，语言偏好持久化 |
| **安全** | DOMPurify | 新闻内容渲染前过滤 XSS，防止注入攻击 |
| **Markdown** | marked | 新闻正文 Markdown → HTML 渲染 |

---

## 🚀 快速开始

```bash
git clone https://github.com/your/xwzx-news.git
cd xwzx-news
npm install
npm run dev          # → http://localhost:5173
```

配置后端地址：编辑 `src/config/api.js`，将 `API_BASE_URL` 指向后端服务。

---

## 🗺️ 路由设计

| 路由 | 页面 | 认证 | 说明 |
|---|---|---|---|
| `/` | Home | 否 | 首页新闻流 |
| `/category/:id` | Category | 否 | 按分类浏览 |
| `/news/:id` | NewsDetail | 否 | 文章详情 |
| `/login` | Login | 否 | 登录（已登录自动跳转） |
| `/register` | Register | 否 | 注册 |
| `/favorites` | Favorite | 是 | 我的收藏 |
| `/history` | History | 是 | 浏览历史 |
| `/my` | My | 是 | 个人中心 |
| `/profile` | Profile | 是 | 编辑资料 |
| `/settings` | Settings | 否 | 语言/主题 |
| `/ai-chat` | AIChat | 否 | AI 助手 |

**导航守卫**：未登录访问需认证的页面 → 自动跳转 `/login`

---

