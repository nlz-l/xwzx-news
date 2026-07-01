# 新闻中心移动端

![Vue](https://img.shields.io/badge/Vue-3.x-4FC08D)
![Vite](https://img.shields.io/badge/Vite-7.x-646CFF)
![Vant](https://img.shields.io/badge/Vant-4.x-07C160)
![Pinia](https://img.shields.io/badge/Pinia-2.x-F7D336)
![Status](https://img.shields.io/badge/status-active-brightgreen)

基于 Vue 3 + Vite 的移动端新闻应用，支持新闻浏览、用户登录、收藏历史、多语言切换和 AI 对话。与 [`toutiao_backend`](../toutiao_backend/) 后端配合使用。

## 技术栈

| 技术 | 用途 |
|---|---|
| **Vue 3** (Composition API) | 前端框架 |
| **Vite 7** | 构建工具 |
| **Pinia** + `pinia-plugin-persistedstate` | 状态管理 + 持久化 |
| **Vue Router** | 路由管理 |
| **Vant 4** | 移动端 UI 组件库 |
| **Axios** | HTTP 请求 |
| **vue-i18n** | 国际化（中/英） |
| **marked** + **DOMPurify** | Markdown 渲染 + XSS 防护 |

## 项目结构

```text
xwzx-news/
├── index.html                # HTML 入口
├── vite.config.js            # Vite 配置
├── package.json              # 项目依赖
├── src/
│   ├── main.js               # 应用入口
│   ├── App.vue               # 根组件
│   ├── components/           # 公共组件
│   │   ├── NewsItem.vue      # 新闻卡片
│   │   └── TabBar.vue        # 底部导航栏
│   ├── views/                # 页面组件
│   │   ├── Home.vue          # 首页新闻流
│   │   ├── Category.vue      # 分类浏览
│   │   ├── NewsDetail.vue    # 新闻详情
│   │   ├── Login.vue         # 登录页
│   │   ├── Register.vue      # 注册页
│   │   ├── Favorite.vue      # 收藏列表
│   │   ├── History.vue       # 浏览历史
│   │   ├── My.vue            # 个人中心
│   │   ├── Profile.vue       # 个人资料
│   │   ├── Settings.vue      # 设置页
│   │   └── AIChat.vue        # AI 对话
│   ├── router/               # Vue Router 路由
│   ├── store/                # Pinia 状态模块
│   │   ├── user.js           # 用户状态
│   │   ├── news.js           # 新闻状态
│   │   ├── favorites.js      # 收藏状态
│   │   ├── history.js        # 历史状态
│   │   ├── language.js       # 语言偏好
│   │   └── theme.js          # 主题设置
│   ├── i18n/                 # 国际化
│   │   ├── index.js          # i18n 初始化
│   │   ├── zh-CN.js          # 中文语言包
│   │   └── en-US.js          # 英文语言包
│   └── config/
│       └── api.js            # API 地址配置
└── README.md
```

## 快速开始

### 环境要求

- Node.js 18+
- npm

### 安装与运行

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

### 配置后端地址

在 `src/config/api.js` 或 `.env` 中配置 API 基础地址：

```js
// src/config/api.js
export const API_BASE_URL = 'http://localhost:8000'
```

## 页面路由

| 路由 | 页面 | 说明 |
|---|---|---|
| `/` | Home | 首页新闻流 |
| `/category/:id` | Category | 按分类浏览新闻 |
| `/news/:id` | NewsDetail | 新闻详情页 |
| `/login` | Login | 用户登录 |
| `/register` | Register | 用户注册 |
| `/favorites` | Favorite | 我的收藏 |
| `/history` | History | 浏览历史 |
| `/my` | My | 个人中心 |
| `/profile` | Profile | 编辑资料 |
| `/settings` | Settings | 应用设置 |
| `/ai-chat` | AIChat | AI 对话助手 |

## 状态管理

使用 Pinia 模块化管理应用状态，并通过 `pinia-plugin-persistedstate` 实现本地持久化：

```text
user store     ──→ 登录态、Token、用户信息（持久化）
news store     ──→ 新闻列表、分类、加载状态
favorites store ──→ 收藏列表（持久化）
history store  ──→ 浏览历史（持久化）
language store ──→ 中/英文切换（持久化）
theme store    ──→ 主题偏好（持久化）
```

## 国际化

支持中文（zh-CN）和英文（en-US）双语言切换：

```text
src/i18n/
├── zh-CN.js    # 导航、按钮、提示等中文文本
└── en-US.js    # 英文对应翻译
```

语言偏好自动持久化到本地存储，刷新页面后保持选择。

## 功能特性

| 功能 | 说明 |
|---|---|
| 📰 新闻流 | 首页推荐 + 分类浏览 |
| 🔍 新闻详情 | Markdown 渲染 + XSS 防护 |
| 👤 用户系统 | 注册、登录、个人资料编辑 |
| ⭐ 收藏功能 | 收藏/取消收藏新闻 |
| 🕐 浏览历史 | 自动记录阅读历史 |
| 🌐 多语言 | 中文 / 英文切换 |
| 🎨 主题 | 支持明暗主题切换 |
| 🤖 AI 对话 | 智能问答/新闻助手 |
| 📱 移动适配 | Vant UI 组件 + 响应式布局 |

## 与后端联调

1. 确保 [`toutiao_backend`](../toutiao_backend/) 已启动
2. 将 `src/config/api.js` 中的 API 地址指向后端
3. 如遇 CORS 跨域，检查后端 `main.py` 中 `allow_origins` 配置

## 相关链接

- 后端项目：[toutiao_backend](../toutiao_backend/)
- Dify AI 工具：[Dify](../Dify/)
