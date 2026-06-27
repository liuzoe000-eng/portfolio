# Portfolio Design System
> 基于 index.html + project-01 ~ project-04 提炼。**新增任何页面必须遵循本规范。**
> project-05.html 因风格偏差需对照本文档修正后方可上线。

---

## 1. 色彩 Color

### 核心 Palette（不可引入其他品牌色）

| Token | Hex | 用途 |
|---|---|---|
| `--accent` / `--lime` | `#beff00` | 主强调色：hover glow、选中圆点、selection highlight |
| `--lime-d` | `#9ed400` | 深版强调色：logo 标记色、标题 em、CTA hover 文字 |
| `--black` | `#0a0a0a` | 正文、标题、CTA 背景、黑色区块背景 |
| `--white` | `#ffffff` | 页面底色、卡片底色 |
| `--off-white` | `#f7f7f5` | 卡片背景、轻灰底 |
| `--gray` | `#f0f0ec` | 装饰文字（超大背景字） |
| `--gray-100` | `#f5f5f5` | 卡片填充 |
| `--gray-200` / `--gray2` | `#e4e4de` / `#e8e8e8` | 分割线、边框背景 |
| `--gray-400` / `--gray3` | `#c0c0b8` / `#999` | 辅助文字、滚动条 |
| `--gray-600` / `--text2` | `#666660` / `#555` | 次级文字、描述文字 |
| `--gray-800` | `#222` | 引用文字深色 |
| `--border` | `#e0e0d8` | 所有分割线、卡片描边 |

### 颜色使用规则
- **禁止**引入紫色系（`#4c1d95`、`#7c2d8a`、`#a78bfa` 等）作为品牌色或背景色
- **禁止**引入橙色系（`#fb923c`、`orange` 等）作为交互强调色
- 强调色**只有一个**：lime/accent `#beff00`
- 深色区块只用 `--black (#0a0a0a)`，不得引入其他深色
- 文字颜色三档：`--black`（主）→ `--text2/--gray-600`（次）→ `--gray-400`（辅）

---

## 2. 字体 Typography

### 字体族
```css
font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Noto Sans SC', Arial, sans-serif;
```
中英文统一使用此字体栈，**不引入其他字体**。

### 字重体系
| 用途 | Weight |
|---|---|
| 大标题 / Hero / 数字 | 800 |
| 卡片标题 / 章节标题 | 800 |
| 标签 / Kicker / CTA | 700 |
| 正文 / 描述 | 400–500 |

### 字号 Scale（响应式）
| 级别 | 值 |
|---|---|
| Hero 大标题 | `clamp(52px, 8vw, 120px)` |
| Section 标题 | `clamp(32px, 4vw, 52px)` |
| 项目详情 H1 | `clamp(36px, 5vw, 72px)` |
| 项目详情 H2 | `clamp(24px, 3vw, 36px)` |
| 卡片标题 | `clamp(16px, 1.8vw, 20px)` |
| 正文 | `16–18px`（详情页）/ `14px`（卡片）|
| 描述/次级 | `12–14px` |
| 标签/Kicker | `10–11px` |
| 最小辅助 | `9–10px` |

### 行高
- 大标题：`line-height: 0.95–1.1`
- 章节标题：`line-height: 1.1–1.15`
- 正文段落：`line-height: 1.7–1.85`
- 卡片描述：`line-height: 1.6–1.8`

### 字距
- 大标题：`letter-spacing: -0.03em ~ -0.05em`（负字距，紧凑感）
- 标签/Kicker：`letter-spacing: 0.08em ~ 0.2em`（正字距，全大写）
- 正文：`0`（不设字距）

---

## 3. 间距 Spacing

| 场景 | 值 |
|---|---|
| Section 上下 padding | `100px 0` |
| 容器最大宽 | `1200–1280px` |
| 容器左右 padding | `40–48px` |
| 卡片内边距 | `20–36px` |
| 卡片间距（grid gap） | `24–28px` |
| 元素间 margin-bottom | `8 / 12 / 20 / 24 / 28 / 40 / 80px` |
| Hero padding-top | `140px`（详情页）|

---

## 4. 圆角 Border Radius

| 场景 | 值 |
|---|---|
| 主卡片（work-card） | `16px`（`--r`）|
| 内容卡片 / Insight | `10–12px` |
| 标签 / Tag | `2–4px` |
| Pill 形（按钮/badge） | `999px` |
| 图片区块 | `12–20px` |
| 数字圆形 badge | `50%` |

---

## 5. 组件规范 Components

### 5-1 导航栏 Nav
- 固定顶部，高度 `58px`（index）/ `60px`（详情页）
- 滚动后：`background: rgba(255,255,255,.92)` + `backdrop-filter: blur(12~20px)`
- Logo：`liuux` 格式，`ux` 部分用 `--lime-d` 色，hover 触发旋转动画
- 右侧：详情页用 `← 返回作品集` 文字链接（`font-size:13px, color:--gray-600`）

### 5-2 标签 Tag / Hero-tag
```css
/* 详情页顶部分类标签 */
background: var(--accent);   /* #beff00 */
color: var(--black);
font-size: 11px; font-weight: 700;
letter-spacing: 0.1em; text-transform: uppercase;
padding: 5px 12px; border-radius: 2px;

/* 首页 work-card 标签 */
background: var(--gray2);    /* #e4e4de */
color: var(--text2);
border: 1px solid var(--border);
border-radius: 4px;
```

### 5-3 引用块 Highlight / Blockquote
```css
border-left: 3px solid var(--accent);   /* lime 左边框 */
background: var(--gray-100);            /* #f5f5f5 */
border-radius: 0 8px 8px 0;
padding: 20px 24px;
font-style: italic;
color: var(--gray-800);
```

### 5-4 数字徽章 Strategy-num / 序号圆
```css
background: var(--accent);
color: var(--black);
font-size: 12px; font-weight: 800;
width: 28px; height: 28px; border-radius: 50%;
```

### 5-5 深色卡片（黑底）
```css
background: var(--black);
/* 内部文字颜色 */
.title  { color: var(--white); }
.accent { color: var(--accent); }      /* lime，用于标注数字/kicker */
.body   { color: rgba(255,255,255,.55); }
.border { border: 1px solid rgba(255,255,255,.15); }
```

### 5-6 Metric 数字块
```css
/* 数字 */
font-size: clamp(32px,3.5vw,48px); font-weight:800; letter-spacing:-.04em;
/* 单位（yr / % 等） */
.unit { color: var(--accent); font-size: .55em; }
/* 标签 */
font-size:11px; color: rgba(255,255,255,.35); letter-spacing:.04em;
```

### 5-7 CTA 按钮
```css
/* 主 CTA（pill 形）*/
background: var(--black); color: var(--white);
border-radius: 999px; padding: 18px 40px;
font-size:15px; font-weight:700; letter-spacing:.04em;
/* hover */
background: var(--lime); color: var(--black);
box-shadow: 0 0 48px rgba(190,255,0,.35);
transform: scale(1.04);

/* 小圆形箭头按钮 */
background: var(--black); color: var(--white);
width:28px; height:28px; border-radius:50%;
/* hover */
background: var(--lime); color: var(--black);
transform: rotate(-45deg);
```

### 5-8 复盘卡片关键词高亮 `.card .kw`
```css
/* 默认状态：黑色加粗 + 细 accent 下划线 */
.card .kw {
  color: var(--black);
  font-weight: 700;
  border-bottom: 2px solid var(--accent);
  border-radius: 2px;
  padding: 0 1px;
  transition: background 0.2s, border-color 0.2s;
  cursor: default;
}

/* Hover 状态：下划线消失，背景高亮（类似文字选中效果） */
.card:hover .kw {
  color: var(--black);
  font-weight: 700;
  border-bottom-color: transparent;
  background: var(--accent);
}
```
- 用于 Reflections / 复盘模块中需要强调的关键词
- 默认态克制，仅用一条 `2px` accent 实线下划线暗示可交互
- Hover 态整体背景铺满 accent 黄，形成"文字被选中"的视觉反馈
- 所有项目页面保持一致

### 5-9 Work 卡片
- 背景：`var(--off-white)` / `var(--gray-100)`
- 悬停边框：`0 0 0 2px var(--lime)` + lime glow 光晕
- 图片区高度：`260px`，hover `scale(1.06)`
- hover 圆形 CTA：`76px`，`background: var(--lime)` + `rotate(-15deg→0deg)` 弹出动画
- 卡片序号徽章：白底黑字，`border: 1px solid var(--border)`

### 5-10 自定义光标
- 小圆点：`10–12px`，`background: var(--lime)` 或 `var(--black)`，`mix-blend-mode: multiply`
- 圆环：`36–38px`，`border: 1.5px solid var(--black)`
- hover 卡片时圆环放大至 `60px`，变为 lime 色

### 5-11 Marquee 跑马灯
- 深色版：`background: var(--black)`，文字 `rgba(255,255,255,.45)`
- 浅色版：`background: var(--off-white)`，文字 `var(--text2)`
- 星号分隔符：`color: var(--lime)` / `var(--lime-d)`

### 5-12 进度条
```css
height: 2px; background: var(--lime); transform-origin: left;
```

---

## 6. 动效 Motion

| 效果 | 参数 |
|---|---|
| 标准弹性曲线 | `cubic-bezier(.22,1,.36,1)` |
| 弹跳出现 | `cubic-bezier(.34,1.56,.64,1)` |
| 过渡时长（hover） | `0.2–0.35s` |
| 元素入场（fadeUp） | `opacity:0 + translateY(32px)` → `opacity:1 + translateY(0)`, `.9s` |
| 文字行入场（lineIn） | `translateY(110%)` → `0`, `.85s`, 每行 delay `0.1s` |
| Logo 旋转动画 | `0.75–0.8s` cubic-bezier(.4,0,.2,1) |

---

## 7. 布局 Layout

### 详情页结构模板（project-01 ~ 04 统一）
```
Nav（固定，logo + 返回按钮）
└─ Hero（padding-top:140px, max-width:1200px, padding:0 48px）
   ├─ Hero Tag（lime 背景标签）
   ├─ H1（clamp 大标题）
   ├─ Hero Meta（角色/时间/项目，flex gap:40px）
   └─ Hero Desc（18px, line-height:1.7, max-width:680px）
└─ Cover Image（max-width:1200px, border-radius:12px）
└─ Content（max-width:1200px, padding:0 48px 120px）
   ├─ Metrics Bar（3列 grid，黑底白字，lime 数字高亮）
   ├─ Section（margin-bottom:80px）
   │  ├─ Section Num（11px, uppercase, --gray-400）
   │  ├─ H2（clamp(24px,3vw,36px), weight:800）
   │  └─ 内容（正文/卡片/引用块/列表）
   └─ ...
└─ Footer Nav（border-top, flex space-between, 上/下一个项目）
```

### Grid 规范
- 首页 works-grid：`2列`，`gap:28px`，卡片错位排布（stagger offset）
- 服务卡片：`3列`，`gap:1px`（用背景色分割线）
- 洞察行：`3列`，`gap:24px`
- Metrics：`3–4列`，`gap:1px`

---

## 8. 禁止事项 Don'ts

❌ 引入紫色（purple/violet/indigo）作为界面色  
❌ 引入橙色（orange）作为强调色  
❌ 使用渐变色作为大面积背景（Hero/卡片/section 背景）  
❌ 使用毛玻璃 + 彩色叠加（blur + 彩色蒙层）  
❌ 引入新字体  
❌ 使用不在 Palette 中的颜色（含灰度以外的任何色相）  
❌ 标签使用描边 + 彩色文字的形式（统一用 gray2 填充 + text2 文字）  
❌ 用 emoji 装饰 UI 组件内部（文章内容可以，卡片/标签/按钮禁用）  

---

## 9. 新增页面检查清单 Checklist

新增 project-XX.html 上线前，逐条对照：

- [ ] `:root` 中的 token 与本文档 §1 完全一致
- [ ] 字体栈与本文档 §2 一致
- [ ] 未引入任何新颜色（尤其紫色/橙色）
- [ ] Hero Tag 使用 lime 背景 + black 文字
- [ ] 引用块使用 lime 左边框 + gray-100 背景
- [ ] 深色区块只用 `#0a0a0a`
- [ ] 序号/徽章使用 lime 背景
- [ ] 标签使用 gray2 背景（非彩色）
- [ ] 自定义光标已实现
- [ ] 导航栏使用返回按钮而非全导航
- [ ] 底部导航包含「上一个/下一个项目」链接
