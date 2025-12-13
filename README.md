这里为您准备了一份专业、详尽的 README 文档，涵盖了项目介绍、核心功能、技术栈、安装配置及部署指南。您可以直接复制用于 GitHub 仓库。
# 🌌 Crypto Tactical Terminal V60 (@oAdam Edition)

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![React](https://img.shields.io/badge/React-18.x-61DAFB.svg)
![Vite](https://img.shields.io/badge/Vite-5.x-646CFF.svg)
![Firebase](https://img.shields.io/badge/Firebase-Firestore-FFCA28.svg)
![Style](https://img.shields.io/badge/Style-Cyberpunk%2FPixel-ff003c.svg)

**Crypto Tactical Terminal** 是一个基于 React 构建的极客风格加密货币战术终端。它集成了实时行情、链上巨鲸追踪、持仓模拟计算、AI 技术分析以及多端云同步功能。专为移动端优化的响应式设计，提供类似原生 App 的沉浸式体验。

---

## ✨ 核心功能 (Key Features)

### 📊 市场监控与分析
* **实时行情**: 支持 Binance (WebSocket), OKX (WebSocket), CoinGecko (Polling) 多源切换。
* **K线图表**: 集成 TradingView Widget，支持暗黑/明亮模式切换。
* **AI 深度扫描**: 自动计算 RSI, BOLL, MA 趋势，提供买卖信号与止盈止损位建议。
* **资金流向**: 可视化展示最近 10 天的 Net Taker Buy (主动买入) 资金流。

### 🐋 Hyperliquid 巨鲸追踪 (Whale Tracker)
* **实时监控**: 追踪指定钱包在 Hyperliquid 上的持仓、未结盈亏 (uPnL)、杠杆和爆仓价。
* **批量导入**: 支持文本批量导入钱包地址（格式：`地址 备注`）。
* **智能交互**: 
    * 点击地址跳转 Hyperliquid 详情页。
    * 列表支持横向/纵向滑动，表头 (Sticky Header) 吸附。
    * 移动端优化的删除操作（独立操作列）。

### ☁️ 云端同步与多设备协同 (Cloud Sync)
* **Firebase 集成**: 基于 Firestore 实现毫秒级数据同步。
* **无缝漫游**: 在桌面端录入持仓，手机端即时可见。只需输入相同的 `Cloud Key`。
* **数据持久化**: 防止浏览器缓存清除导致的数据丢失。

### 🧮 战术模拟 (Tactical Sim)
* **持仓推演**: 输入模拟价格和仓位，自动计算新的均价 (Avg Price) 和 强平价 (Liq Price)。
* **网格策略**: 自动生成基于当日开盘价的支撑/阻力网格。
* **OCR 识别**: 支持上传持仓截图，自动识别价格和数量（基于 Tesseract.js）。

### 📱 移动端极致体验
* **原生级交互**: 禁止双指缩放 (`user-scalable=no`)，防止误触。
* **自适应布局**: 完美适配各种尺寸的手机屏幕。

---

## 🛠️ 技术栈 (Tech Stack)

* **前端框架**: React 18, Vite
* **样式**: CSS Variables (支持 Pixel/Dark/Light 三种主题切换)
* **后端服务**: Firebase (Auth & Firestore)
* **工具库**: 
    * `html2canvas`: 界面截图生成
    * `tesseract.js`: 光学字符识别 (OCR)
    * TradingView Lightweight Charts

---

## 🚀 快速开始 (Quick Start)

### 1. 环境准备
确保您的环境已安装 [Node.js](https://nodejs.org/) (推荐 v18+)。

### 2. 克隆项目
```bash
git clone [https://github.com/your-username/crypto-terminal-v60.git](https://github.com/your-username/crypto-terminal-v60.git)
cd crypto-terminal-v60

3. 安装依赖
npm install
# 确保安装 firebase
npm install firebase

4. 配置 Firebase
在 src/App.jsx (或 src/firebaseConfig.js) 中填入您的 Firebase 配置信息。
 * 前往 Firebase Console 创建项目。
 * 启用 Authentication (选择匿名登录 Anonymous)。
 * 启用 Firestore Database (选择测试模式 Test Mode 以允许读写)。
 * 在项目设置中获取 firebaseConfig 对象。
<!-- end list -->
// src/App.jsx 顶部
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "your-app.firebaseapp.com",
  projectId: "your-app-id",
  storageBucket: "your-app.appspot.com",
  messagingSenderId: "...",
  appId: "..."
};

5. 启动开发服务器
npm run dev

访问终端显示的本地地址 (通常为 http://localhost:5173)。
📦 部署指南 (Deployment)
本项目完全静态化，推荐使用 Vercel 进行一键部署。
 * 将代码推送到 GitHub 仓库。
 * 登录 Vercel，点击 Add New Project。
 * 导入你的 GitHub 仓库。
 * Framework Preset 选择 Vite。
 * 点击 Deploy。
⚠️ 注意事项:
 * 部署后，请务必去 Firebase Console -> Authentication -> Settings -> Authorized domains 中添加 Vercel 分配的域名，否则云同步功能将无法登录。
📖 使用说明 (Usage Guide)
1. 开启云同步
点击底部 Dock 栏的 ⚙️ (设置) 图标，在 CLOUD SYNC 输入框中设置一个密钥（例如 my-secret-key-888）。在另一台设备输入相同密钥即可同步。
2. 添加巨鲸监控
点击 HYPERLIQUID WHALE TRACKER 标题栏右侧的 [+] 按钮。
 * Single: 单个添加，输入地址和备注。
 * Batch: 批量添加，每行一条，格式为 0x地址 备注。
3. 切换主题
点击顶部的 👾 / 🌙 / ☀️ 图标可在 像素风、暗黑模式、明亮模式 之间切换。
4. 截图分享
点击顶部的 📝 按钮可截取全屏；点击各面板标题栏右侧的小 📝 按钮可截取该独立模块。
📂 目录结构 (Structure)
crypto-terminal-v60/
├── public/              # 静态资源
├── src/
│   ├── App.jsx          # 主入口 (包含所有逻辑组件)
│   ├── main.jsx         # React 渲染入口
│   └── index.css        # 全局样式重置
├── index.html           # HTML 模板 (包含外部 Script 引用)
├── package.json         # 依赖配置
└── vite.config.js       # Vite 配置

🤝 贡献 (Contributing)
欢迎提交 Issue 或 Pull Request 来改进此终端。
 * Fork 本仓库
 * 创建特性分支 (git checkout -b feature/AmazingFeature)
 * 提交更改 (git commit -m 'Add some AmazingFeature')
 * 推送到分支 (git push origin feature/AmazingFeature)
 * 提交 Pull Request
📜 许可证 (License)
Distributed under the MIT License. See LICENSE for more information.
由 @oAdam 设计与构建 Not Financial Advice. DYOR.

