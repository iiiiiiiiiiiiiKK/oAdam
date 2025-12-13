```markdown
# V56 Terminal - 加密货币交易终端仪表板

## 概述

V56 Terminal 是一个功能齐全的加密货币交易终端仪表板，专为交易者和投资者设计。它集成了实时市场数据、持仓管理、技术分析、巨鲸追踪和多种实用工具于一体，提供专业级的交易监控体验。

## ✨ 核心功能

### 📊 实时市场数据
- **多交易所支持**：Binance、OKX、CoinGecko 数据源
- **实时价格更新**：WebSocket 连接实现毫秒级价格更新
- **市场指标**：资金费率、恐惧贪婪指数、多空比、持仓量等
- **宏观经济**：DXY美元指数、黄金价格、USDT汇率

### 🎯 持仓管理
- **多空持仓监控**：实时计算未实现盈亏
- **风险控制**：自动计算清算价格和风险等级
- **杠杆调节**：自定义杠杆倍数（1-100x）
- **钱包管理**：实时净值追踪

### 🤖 智能分析系统
- **技术指标**：RSI、BOLL、ATR、移动平均线
- **AI分析**：每小时/4小时/日线级别深度扫描
- **策略矩阵**：自动生成支撑阻力位和交易建议
- **净资金流**：10日资金流向可视化

### 🐋 巨鲸追踪
- **Hyperliquid 监控**：实时追踪巨鲸持仓
- **批量导入**：支持单地址或批量导入监控列表
- **Telegram 集成**：支持通过TG Bot添加监控地址
- **持仓详情**：方向、杠杆、盈亏、清算价等

### 📈 图表与可视化
- **TradingView 集成**：专业级K线图表
- **周期回报热力图**：季度/月度/周度/日度回报可视化
- **净资金流图表**：资金流向柱状图

### 🔧 实用工具
- **OCR识别**：截图识别交易订单（价格、数量）
- **截图功能**：全屏/模块截图
- **云同步**：Firebase 数据同步
- **主题切换**：深色/浅色/像素风格

## 🛠 技术栈

### 前端框架
- **React 18**：函数组件 + Hooks
- **状态管理**：useState, useEffect, useMemo, useRef

### 数据服务
- **WebSocket**：实时价格数据
- **Firebase**：身份验证 + Firestore 数据库
- **REST APIs**：Binance、OKX、CoinGecko、Hyperliquid

### 第三方库
- **TradingView**：专业图表
- **Tesseract.js**：OCR识别
- **html2canvas**：网页截图
- **Firebase SDK**：云服务

### 样式与UI
- **CSS-in-JS**：动态主题系统
- **响应式设计**：移动端优先
- **自定义字体**：TechMono 字体族

## 🚀 快速开始

### 环境要求
- Node.js 16+
- npm 或 yarn
- 现代浏览器（Chrome 90+, Firefox 88+）

### 安装步骤

1. **克隆项目**
   ```bash
   git clone <repository-url>
   cd v56-terminal
```

1. 安装依赖
   ```bash
   npm install
   # 或
   yarn install
   ```
2. 配置环境变量
   在 public/index.html 中添加全局配置：
   ```html
   <script>
     window.__app_id = 'your-app-id';
     window.__firebase_config = JSON.stringify({
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_AUTH_DOMAIN",
       projectId: "YOUR_PROJECT_ID",
       storageBucket: "YOUR_STORAGE_BUCKET",
       messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
       appId: "YOUR_APP_ID"
     });
     window.__initial_auth_token = "OPTIONAL_AUTH_TOKEN";
   </script>
   ```
3. 运行开发服务器
   ```bash
   npm start
   # 或
   yarn start
   ```
4. 构建生产版本
   ```bash
   npm run build
   # 或
   yarn build
   ```

⚙️ 配置说明

Firebase 配置

项目使用 Firebase 实现：

· 匿名/自定义令牌认证
· Firestore 数据同步
· 用户设置云存储

API 密钥配置

· Telegram Bot：用于推送通知和地址监控
· CORS Proxy：可选的代理设置（默认启用）
· 自定义数据源：支持添加外部API源

主题配置

三种预设主题：

1. 深色主题：默认，适合夜间交易
2. 浅色主题：适合日间使用
3. 像素主题：复古风格

📱 模块详解

1. 核心监控面板 (CORE MONITOR)

· 实时盈亏计算
· 净值监控
· 风险等级指示器
· 清算价格预警

2. 策略矩阵 (STRATEGY MATRIX)

· 基于当前价格的支撑阻力位
· 自动生成交易建议
· 点击即可加载到模拟器

3. AI技术分析

· 多时间框架分析（1H/4H/1D）
· 技术指标综合评估
· 交易信号生成
· 入场/止损/目标价建议

4. 巨鲸追踪器

· Hyperliquid 平台巨鲸实时监控
· 持仓变化警报
· 批量地址管理
· Telegram 集成添加

5. 周期回报热力图

· 季度/月度/周度/日度回报可视化
· 颜色编码（绿色盈利/红色亏损）
· 多币种对比（BTC/ETH/SOL）

🔐 安全特性

数据安全

· 本地存储加密：敏感数据本地加密存储
· 云同步可选：用户可选择启用/禁用云同步
· 匿名认证：默认使用Firebase匿名认证

隐私保护

· 无用户数据分析：不收集用户交易数据
· 自托管选项：所有代码可自托管
· API密钥本地存储：不发送到第三方服务器

📱 移动端优化

响应式设计

· 自适应屏幕尺寸
· 移动端触摸优化
· 底部导航栏

性能优化

· 图片懒加载
· WebSocket 连接复用
· 数据缓存机制

🔄 数据流

```
用户界面 ↔ React组件 ↔ 状态管理
      ↓
WebSocket/REST API ↔ 外部数据源
      ↓
Firebase ↔ 云同步
      ↓
LocalStorage ↔ 本地缓存
```

🧪 测试与开发

开发模式

```bash
# 启动开发服务器
npm start

# 运行测试
npm test

# 构建分析
npm run build -- --analyze
```

代码质量

· ESLint 代码检查
· Prettier 代码格式化
· React Hooks 规则检查

📄 许可证

本项目采用 MIT 许可证。详见 LICENSE 文件。

🤝 贡献指南

1. Fork 项目仓库
2. 创建功能分支 (git checkout -b feature/AmazingFeature)
3. 提交更改 (git commit -m 'Add some AmazingFeature')
4. 推送到分支 (git push origin feature/AmazingFeature)
5. 开启 Pull Request

📞 支持与反馈

· 问题报告：使用 GitHub Issues
· 功能请求：提交 Issue 并标记为 enhancement
· 安全漏洞：请勿公开报告，通过安全渠道联系

📚 相关资源

· React 官方文档
· Firebase 文档
· Binance API 文档
· TradingView 图表库

---

版本: v56.0
最后更新: 2024年
维护者: @oAdam
兼容性: Chrome, Firefox, Safari, Edge (最新版本)

```
```