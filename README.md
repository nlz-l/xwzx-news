# 新闻中心移动端

[![Vue](https://img.shields.io/badge/Vue-3.x-4FC08D)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-7.x-646CFF)](https://vite.dev/)
[![Vant](https://img.shields.io/badge/Vant-4.x-07C160)](https://vant-ui.github.io/)
[![Pinia](https://img.shields.io/badge/Pinia-2.x-F7D336)](https://pinia.vuejs.org/)
[![i18n](https://img.shields.io/badge/i18n-zh_CN_|_en_US-green)]()

基于 Vue 3 + Vite 的移动端新闻应用，支持新闻浏览、用户登录、收藏、历史、多语言切换和 AI 对话。与 [toutiao_backend](../toutiao_backend/) 后端配合使用。

---

## 📂 项目结构

```text
xwzx-news/
├── index.html                # HTML 入口
├── vite.config.js            # Vite 配置
├── package.json              # 依赖配置
├── src/
│   ├── main.js               # 应用入口
│   ├── App.vue               # 根组件
│   ├── components/           # 公共组件
│   │   ├── NewsItem.vue      #   新闻卡片
│   │   └── TabBar.vue        #   底部导航
│   ├── views/                # 页面组件
│   │   ├── Home.vue          #   首页新闻流
│   │   ├── Category.vue      #   分类浏览
│   │   ├── NewsDetail.vue    #   新闻详情
│   │   ├── Login.vue         #   登录
│   │   ├── Register.vue      #   注册
│   │   ├── Favorite.vue      #   收藏列表
│   │   ├── History.vue       #   浏览历史
│   │   ├── My.vue            #   个人中心
│   │   ├── Profile.vue       #   个人资料
│   │   ├── Settings.vue      #   设置
│   │   └── AIChat.vue        #   AI 对话
│   ├── router/               # Vue Router 路由
│   ├── store/                # Pinia 状态管理
│   │   ├── user.js           #   用户状态
│   │   ├── news.js           #   新闻状态
│   │   ├── favorites.js      #   收藏状态
│   │   ├── history.js        #   历史状态
│   │   ├── language.js       #   语言偏好
│   │   └── theme.js          #   主题设置
│   ├── i18n/                 # 国际化
│   │   ├── index.js          #   i18n 初始化
│   │   ├── zh-CN.js          #   中文语言包
│   │   └── en-US.js          #   英文语言包
│   └── config/api.js         # API 地址配置
└── README.md
```

---

## 🚀 快速开始

环境要求：Node.js 18+

```bash
npm install
npm run dev                  # 开发服务器 → http://localhost:5173
npm run build                # 生产构建
npm run preview              # 预览构建结果
```

---

## 🗺️ 页面路由

| 路由 | 页面 | 说明 |
|---|---|---|
| `/` | Home | 首页新闻流 |
| `/category/:id` | Category | 分类新闻 |
| `/news/:id` | NewsDetail | 新闻详情 |
| `/login` | Login | 用户登录 |
| `/register` | Register | 用户注册 |
| `/favorites` | Favorite | 我的收藏 |
| `/history` | History | 浏览历史 |
| `/my` | My | 个人中心 |
| `/profile` | Profile | 编辑资料 |
| `/settings` | Settings | 应用设置 |
| `/ai-chat` | AIChat | AI 对话助手 |

---

## 🗃️ 状态管理

使用 Pinia 管理状态并通过 `pinia-plugin-persistedstate` 持久化到本地存储：

```text
user store       → 登录态、Token、用户信息（持久化）
news store       → 新闻列表、分类、加载状态
favorites store  → 收藏列表（持久化）
history store    → 浏览历史（持久化）
language store   → 中/英文切换（持久化）
theme store      → 明暗主题（持久化）
```

---

## ✨ 功能特性

| 功能 | 说明 |
|---|---|
| 📰 新闻流 | 首页推荐 + 分类浏览 |
| 🔍 详情 | Markdown 渲染 + XSS 防护 |
| 👤 用户系统 | 注册、登录、个人资料编辑 |
| ⭐ 收藏 | 收藏/取消收藏新闻 |
| 🕐 历史 | 自动记录浏览历史 |
| 🌐 多语言 | 中文 / 英文切换 |
| 🎨 主题 | 明暗主题切换 |
| 🤖 AI 对话 | 智能问答助手 |
| 📱 移动适配 | Vant UI 组件 + 响应式布局 |

---

## 🛠️ 技术栈

| 技术 | 用途 |
|---|---|
| Vue 3（Composition API） | 前端框架 |
| Vite 7 | 构建工具 |
| Pinia | 状态管理 |
| Vue Router | 路由 |
| Vant 4 | 移动端 UI 组件库 |
| Axios | HTTP 请求 |
| vue-i18n | 国际化 |
| marked + DOMPurify | Markdown 渲染 + XSS 防护 |

---

## 🔗 相关项目

- **后端**：[toutiao_backend](../toutiao_backend/) — FastAPI 新闻 API
- **AI 工具**：[Dify](../Dify/) — Dify 天气工具
