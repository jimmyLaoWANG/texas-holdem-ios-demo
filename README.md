# Texas Hold'em · iOS Demo

一款面向 iOS 移动端的德州扑克可交互 Demo，单文件 HTML 零依赖，可直接双击在浏览器打开，亦可通过 GitHub Pages 在线访问。

> ⚠️ 本仓库为**前端交互原型 / 立项验证 Demo**，不是上架的 iOS App 本体。
> 用途：在 iOS 原生开发立项前，先用网页形式跑通完整德州扑克玩法和游戏化大厅交互，供产品/设计/技术评审。

## ✨ 功能一览

### 🏠 游戏化大厅
- 中央椭圆牌桌 + 💁‍♀️ 荷官形象（浮动扑克 + 循环欢迎语）
- 4 个圆形入口按钮沿弧线排布，毛玻璃球面感视觉
- 4 个全屏页面：个人中心 / 充值 / 创建牌局 / 加入牌局
- 个人资产 / VIP 等级 / 头像通过 localStorage 持久化

### 🃏 完整德州扑克玩法
- 支持 **4 / 6 / 8 人桌**（座位极坐标动态布局）
- 完整四轮下注：Preflop / Flop / Turn / River
- 操作：Fold / Check / Call / Raise（带滑块 + 2x/3x/½池/底池/All-in 快捷键）/ All-in
- **真实牌型评估**：7 选 5 全枚举，9 类手牌（含 A-2-3-4-5 轮子）
- AI 决策模型：Preflop 用 Chen 公式简化版，Postflop 按 category + pot odds

### ⏱️ 开局确认机制（防挂机踢人）
- 每手开始前 15s 圆环倒计时
- 超时自动踢回大厅
- 所有玩家头像 / 资产 / 准备状态可见

### 🎲 房间系统
- 6 个预置房间（含创建者头像 + 昵称 + VIP 徽章）
- 自建房自动以当前 profile 作为 creator
- 牌桌内顶部胶囊显示 "由 XXX 创建 · 50/100 盲注"

## 🚀 在线体验

**Live Demo**：<https://jimmylaowang.github.io/texas-holdem-ios-demo/>

或本地体验：
```bash
git clone https://github.com/jimmyLaoWANG/texas-holdem-ios-demo.git
cd texas-holdem-ios-demo
# 双击 index.html，或：
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 📱 推荐使用方式

- **设备**：iPhone Safari（375×812 竖屏基准设计）
- **桌面**：Chrome / Safari DevTools 开启移动端模拟（iPhone 13 / 14）
- 当前 Demo 仅支持单机 vs AI，未做联机

## 🏗️ 技术架构

| 项 | 说明 |
|---|---|
| 框架 | 无（纯原生 HTML/CSS/JS） |
| 依赖 | 零（无 CDN、无 npm） |
| 文件 | 单文件 `index.html`，约 2900 行 |
| 视觉风格 | iOS Human Interface Guidelines（SF Pro 字体回退、毛玻璃、iOS 配色） |
| 数据持久化 | localStorage（`poker_profile`） |
| 算法核心 | 自实现 7 选 5 牌型评估 + Chen 公式 AI |

## 📦 迭代历史

| 版本 | 行数 | 关键变化 |
|---|---|---|
| v1 | 1450 | 基础 4 人桌德州扑克核心玩法 |
| v2 | 2383 | 大厅 + 开局确认 + 桌内头像/资产 |
| v3 | 2855 | 游戏化大厅 + 全屏页 + 房间创建者 + 4/6/8 人桌 |
| v3.1 | 2866 | 圆形按钮去白底 + 加间距 + 去倾斜 |
| v3.2 | 2918 | 修复牌桌穿透大厅按钮的路由 bug |

## ⚠️ 已知局限

1. 未实现 side-pot（多人不同筹码 All-in 时按主池均分）
2. Postflop AI 用 category/8 粗估，未做蒙特卡洛胜率
3. 房间列表 `joined/max` 为静态 mock，加入后未回写
4. 邀请好友 / 战绩 / 设置 / 退出登录均为占位
5. 仅支持单机 vs AI，未实现联机

## 📄 License

MIT
