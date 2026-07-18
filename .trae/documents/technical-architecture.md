# 龚艳艳·老江津酸菜鱼餐厅宣传网站 技术架构

## 1. 架构设计
纯静态单页网站，无需后端服务，直接部署到Cloudflare Pages。

```mermaid
flowchart TD
    "用户浏览器" --> "Cloudflare Pages CDN"
    "Cloudflare Pages CDN" --> "静态HTML/CSS/JS文件"
    "静态HTML/CSS/JS文件" --> "图片资源(CDN图片)"
```

## 2. 技术说明
- **前端方案**：纯 HTML5 + CSS3 + 原生 JavaScript（单页静态网站）
- **CSS方案**：使用Tailwind CSS v3 CDN版本，快速构建美观界面
- **图标方案**：Lucide Icons CDN
- **部署方案**：GitHub + Cloudflare Pages 自动部署
- **数据方案**：硬编码模拟数据（餐厅信息、团购套餐、评价等）

选择纯静态HTML方案原因：
1. 无需构建步骤，直接部署到Cloudflare Pages
2. 加载速度快，SEO友好
3. 维护简单，适合小型宣传网站
4. 无需Node.js环境，文件结构简洁

## 3. 文件结构
```
/
├── index.html          # 主页面（包含所有HTML结构）
├── assets/             # 资源目录（如需要本地图片）
└── README.md           # 部署说明（可选）
```

## 4. 核心模块实现

### 4.1 颜色系统
```css
--primary: #12a17d;      /* 主色调翠绿 */
--primary-dark: #0f8a6a; /* 深绿hover状态 */
--gold: #d4a853;         /* 金色强调 */
--bg: #fefcf8;           /* 米白背景 */
--text: #1a1a1a;         /* 深灰正文 */
--text-light: #666;      /* 辅助文字 */
```

### 4.2 技术支持悬浮按钮
- 固定定位：position: fixed; bottom: 24px; right: 24px
- 尺寸：56x56px圆形按钮
- 颜色：主色调#12a17d背景，白色图标
- 交互：hover时scale(1.05)，阴影加深
- 功能：点击新窗口打开 https://ai-tools-guide-ar8.pages.dev/
- z-index: 9999 确保始终在最上层

### 4.3 动画效果
- 页面加载时元素渐入动画
- 按钮hover轻微放大效果
- 平滑滚动导航
- 卡片hover轻微上浮效果
- 避免过于花哨的动画，保持高端餐饮的精致感
