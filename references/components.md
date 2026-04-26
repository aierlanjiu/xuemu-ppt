# 组件手册 (Components)

所有组件使用 template.html 预定义的类，走 `var(--...)` 自动适配当前风格。

## 字体层级

| 角色 | 类/标签 | 字体 | 字号 | Weight | 用途 |
|------|---------|------|------|--------|------|
| 页面主标题 | `.h-hero` | Noto Serif SC | 10vw | 900 | 封面大标题 |
| 页面大标题 | `.h-xl` | Noto Serif SC | 6.2vw | 700 | 各页标题 |
| 副标题 | `.h-sub` | Noto Serif SC | 3.1vw | 500 | 封面副标题 |
| 中等标题 | `.h-md` | Noto Serif SC | 2.3vw | 600 | 区块标题 |
| 引导语 | `.lead` | Noto Serif SC | 1.75vw | 400 | 标题下引导句 |
| 正文 | `.body-zh` | Noto Sans SC | 1.22vw | 400 | 正文段落 |
| Kicker | `.kicker` | IBM Plex Mono | 12px | 400 | 页面钩子/前缀 |
| 元数据 | `.meta-row` | IBM Plex Mono | 0.92vw | 400 | 底部作者/日期 |
| 英文展示 | `.display` | Playfair Display | 11vw | 700 | 英文大字 |
| 英文数字 | `.big-num` | Playfair Display | 10vw | 800 | 大数字 |
| 英文引用 | `em` | Playfair Display | — | Italic | 英文斜体 |

## 色彩语义

所有组件通过以下 CSS 变量自动适配当前风格：

| 变量 | 语义 |
|------|------|
| `var(--bg-base)` | 页面底色（light 页） |
| `var(--ink-base)` | 页面文字色（dark 页） |
| `var(--accent)` | 强调色（stat 数字/高亮） |
| `var(--surface)` | 卡片/容器背景 |
| `var(--ink-rgb)` | ink 的 RGB 分量（用于 rgba() 叠加） |
| `var(--bg-rgb)` | bg 的 RGB 分量（用于 rgba() 叠加） |

`.slide.light` 和 `.slide.dark` 自动切换文字色为 `var(--ink-base)` 或 `var(--bg-base)`。

## Stat Card（数据卡片）

```html
<div class="stat-card">
  <div class="stat-label">英文标签</div>
  <div class="stat-nb">8,845</div>
  <div class="stat-note">中文注释</div>
</div>
```

- `.stat-label` — 等宽英文小字，如 "Subscribers"
- `.stat-nb` — Playfair 大数字，支持 K/M 简写
- `.stat-note` — 非衬线中文注释
- 包在 `.grid-6`（3×2）、`.grid-4`（2×2）或 `.grid-3`（3×1）里

## Pipeline（流水线）

```html
<div class="pipeline-section">
  <div class="pipeline-label">阶段名 · Phase Name</div>
  <div class="pipeline">
    <div class="step">
      <div class="step-nb">01</div>
      <div class="step-title">步骤名</div>
      <div class="step-desc">一句话描述</div>
    </div>
  </div>
</div>
```

- 默认 5 列，可用 `data-cols="3"` 或 `data-cols="4"` 调整
- 两组之间自动有分隔线
- 步骤名用非衬线加粗，描述用非衬线常规

## Callout（引用框）

```html
<div class="callout">
  "引用内容"
  <div class="callout-src">— 来源</div>
</div>
```

- 左侧 3px border，自动跟随 currentColor
- light 页微暗底 / dark 页微亮底

## Grid 网格

```html
<div class="grid-2-7-5">   <!-- 左7右5 文字为主 -->
<div class="grid-2-6-6">   <!-- 1:1 对半分 -->
<div class="grid-2-8-4">   <!-- 左8右4 大段文字+小图 -->
<div class="grid-3-3">     <!-- 3×2 六宫格，图片用 -->
<div class="grid-6">       <!-- 3×2 数据卡用 -->
<div class="grid-3">       <!-- 1:1:1 三项并列 -->
<div class="grid-4">       <!-- 2×2 四数据卡 -->
```

所有 grid 默认 `align-items:start`, `gap: 3vw 4vh`。

## Frame Image（图片容器）

```html
<figure class="frame-img" style="aspect-ratio:16/10; max-height:56vh">
  <img src="images/example.png" alt="描述">
  <figcaption class="img-cap">图片说明</figcaption>
</figure>
```

- 自动 `object-fit:cover + object-position:top center`（只裁底部）
- 图片网格中：`style="height:26vh"` 固定高度，不用 aspect-ratio

## Image Slot（占位符）

```html
<div class="img-slot r-4x3">
  <span class="plus">+</span>
  <span class="label">图片描述 · 01-cover.jpg</span>
</div>
```

- 虚线框占位，等图片后期补
- 比例类：`.r-4x3` / `.r-3x2` / `.r-1x1`（默认 16/9）

## Hi（高亮标记）

```html
<span class="hi">被强调的文字</span>
```

- 底部有半透明色块衬底，light 页用 ink tint / dark 页用 bg tint

## Rowline（表格行）

```html
<div class="rowline">
  <span class="k">键（衬线）</span>
  <span class="v">值（非衬线）</span>
  <span class="m">元数据（等宽）</span>
</div>
```

## Tag（标签）

```html
<span class="tag">标签文字</span>
```

- 等宽字符 + border，适合版本号/分类标签

## Rule（分隔线）

```html
<div class="rule"></div>
```

- 全宽 1px 横线，opacity .25

## Signature（签名）

```html
<span class="sign">Brand Name</span>
```

- Playfair 斜体，2vw，opacity .7
