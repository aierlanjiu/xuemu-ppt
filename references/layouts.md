# 页面布局库 (Layouts)

## Pre-flight · 生成前必读

### A. 类名必须来自 template.html

所有类（`h-hero` / `h-xl` / `h-sub` / `h-md` / `lead` / `meta-row` / `stat-card` / `stat-label` / `stat-nb` / `stat-unit` / `stat-note` / `pipeline-section` / `pipeline-label` / `pipeline` / `step` / `step-nb` / `step-title` / `step-desc` / `grid-2-7-5` / `grid-2-6-6` / `grid-2-8-4` / `grid-3-3` / `grid-6` / `grid-3` / `grid-4` / `frame` / `frame-img` / `img-cap` / `callout` / `callout-src` / `kicker`）都在 template.html 的 `<style>` 里预定义。

**不要发明新类名**。如需自定义用 `style="..."` inline。不确定某个类是否存在时，grep template.html 确认。

### B. 图片规范

| 场景 | 比例 | 写法 |
|------|------|------|
| 左文右图主图 | 16:10 或 4:3 | `aspect-ratio:16/10; max-height:56vh` |
| 图片网格（多图）| 固定高度 | `height:26vh`，不用 aspect-ratio |
| 竖版小图 | 3:4 | `aspect-ratio:3/4; max-width:30vw` |
| 全屏主视觉 | 16:9 | `aspect-ratio:16/9; max-height:64vh` |

图片必须包在 `<figure class="frame-img">` 里，img 自动 `object-fit:cover + object-position:top center`。

### C. 图片定位准则

- 图文混排**必须用** `.grid-2-7-5` 等 grid 结构，别用 `align-self:end`
- 左列若需 callout 贴底：左列用 flex column + `justify-content:space-between`
- 所有 grid 父容器加 inline `style="padding-top:6vh"`

### D. 主题节奏规划

每页 `<section>` 必须带 `light` / `dark` / `hero light` / `hero dark` 之一。

硬规则：
- 无连续 3 页同主题
- 8+ 页 deck 必须有 ≥1 hero dark + ≥1 hero light
- 整个 deck 不能只有 light 正文页
- 每 3-4 页插入 1 个 hero

**8 页节奏模板**:
| 页 | 主题 | 布局 |
|---|------|------|
| 1 | hero dark | 封面 |
| 2 | light | 大字报 |
| 3 | dark | 左文右图 |
| 4 | light | Pipeline |
| 5 | hero light | 章节幕封 |
| 6 | dark | 左文右图/引用 |
| 7 | hero dark | 问题页 |
| 8 | light | 结尾 |

### E. chrome 和 kicker 不重复

- `.chrome` 左上 = 栏目标签（跨多页可复用）
- `.kicker` = 本页独一份的引导句（每页不同）

---

## 基础结构

```html
<section class="slide [light|dark|hero light|hero dark]">
  <div class="chrome">
    <div>上下文标签 · 子标签</div>
    <div>ACT · 页号 / 总页数</div>
  </div>
  <!-- 主内容 -->
  <div class="foot">
    <div>页码说明</div>
    <div>— · —</div>
  </div>
</section>
```

---

## Layout 1: 开场封面 (Hero Cover)

```html
<section class="slide hero dark">
  <div class="chrome"><div>Vol.01 · Topic</div><div>01 / N</div></div>
  <div class="frame" style="display:grid; gap:4vh; align-content:center; min-height:80vh">
    <div class="kicker">Kicker · 一行引语</div>
    <h1 class="h-hero" style="font-size:8.5vw">主标题</h1>
    <h2 class="h-sub">副标题</h2>
    <p class="lead" style="max-width:58vw">一行引导文案，说明这份deck的主题和价值。</p>
    <div class="meta-row"><span>作者</span><span>·</span><span>日期</span></div>
  </div>
  <div class="foot"><div>封面说明</div><div>— 2026 —</div></div>
</section>
```

## Layout 2: 章节幕封 (Act Divider)

```html
<section class="slide hero light">
  <div class="chrome"><div>第X幕 · 标题</div><div>Act X · 页号 / 总页数</div></div>
  <div class="frame" style="display:grid; gap:6vh; align-content:center; min-height:80vh">
    <div class="kicker">Act X</div>
    <h1 class="h-hero" style="font-size:7.5vw">幕标题</h1>
    <p class="lead" style="max-width:55vw">一行引语。</p>
  </div>
  <div class="foot"><div>引子</div><div>— · —</div></div>
</section>
```

## Layout 3: 数据大字报 (Big Numbers)

```html
<section class="slide light">
  <div class="chrome"><div>数据 · Data</div><div>页号 / 总页数</div></div>
  <div class="frame" style="padding-top:6vh">
    <div class="kicker">数据先行</div>
    <h2 class="h-xl">标题</h2>
    <p class="lead" style="margin-bottom:5vh">引导句。</p>
    <div class="grid-6" style="margin-top:4vh">
      <div class="stat-card">
        <div class="stat-label">Label</div>
        <div class="stat-nb">8,845</div>
        <div class="stat-note">注释</div>
      </div>
      <!-- repeat ×6 -->
    </div>
  </div>
  <div class="foot"><div>数据来源</div><div>Data</div></div>
</section>
```

## Layout 4: 左文右图 (Quote + Image)

```html
<section class="slide dark">
  <div class="chrome"><div>主题 · Topic</div><div>页号 / 总页数</div></div>
  <div class="frame grid-2-7-5" style="padding-top:6vh">
    <div style="display:flex; flex-direction:column; justify-content:space-between; gap:3vh">
      <div>
        <div class="kicker">独特钩子</div>
        <h2 class="h-xl" style="white-space:nowrap; font-size:7vw">大标题</h2>
        <p class="lead" style="margin-top:3vh">引导描述。</p>
      </div>
      <div class="callout">"引用内容"<div class="callout-src">— 来源</div></div>
    </div>
    <figure class="frame-img" style="aspect-ratio:16/10; max-height:56vh">
      <img src="images/example.png" alt="描述">
      <figcaption class="img-cap">图片说明</figcaption>
    </figure>
  </div>
  <div class="foot"><div>页码说明</div><div>— · —</div></div>
</section>
```

## Layout 5: 图片网格 (Image Grid)

```html
<section class="slide light">
  <div class="chrome"><div>展示 · Gallery</div><div>页号 / 总页数</div></div>
  <div class="frame" style="padding-top:5vh">
    <div class="kicker">视觉实证</div>
    <h2 class="h-xl">标题</h2>
    <div class="grid-3-3" style="margin-top:4vh">
      <figure class="frame-img" style="height:26vh">
        <img src="images/01.png" alt="A">
        <figcaption class="img-cap">A · 说明</figcaption>
      </figure>
      <!-- repeat ×6 -->
    </div>
  </div>
  <div class="foot"><div>来源</div><div>Gallery</div></div>
</section>
```

## Layout 6: Pipeline (流水线)

```html
<section class="slide light">
  <div class="chrome"><div>流程 · Pipeline</div><div>页号 / 总页数</div></div>
  <div class="frame">
    <div class="kicker">Pipeline · 流水线</div>
    <h2 class="h-xl">标题</h2>
    <div class="pipeline-section">
      <div class="pipeline-label">阶段一 · Phase One</div>
      <div class="pipeline">
        <div class="step">
          <div class="step-nb">01</div>
          <div class="step-title">步骤名</div>
          <div class="step-desc">一句话描述</div>
        </div>
        <!-- repeat ×5 -->
      </div>
    </div>
  </div>
  <div class="foot"><div>页码说明</div><div>Pipeline</div></div>
</section>
```

## Layout 7: 悬念问题页 (Hero Question)

```html
<section class="slide hero dark">
  <div class="chrome"><div>留给你</div><div>页号 / 总页数</div></div>
  <div class="frame" style="display:grid; gap:8vh; align-content:center; min-height:80vh">
    <div class="kicker">The Question</div>
    <h1 class="h-hero" style="font-size:7vw; line-height:1.15">核心问题？</h1>
    <p class="lead" style="max-width:50vw">点破一句话。</p>
  </div>
  <div class="foot"><div>页码说明</div><div>— · —</div></div>
</section>
```

## Layout 8: 大引用 (Big Quote)

```html
<section class="slide dark">
  <div class="chrome"><div>金句 · Quote</div><div>页号 / 总页数</div></div>
  <div class="frame" style="display:grid; gap:5vh; align-content:center; min-height:80vh">
    <div class="kicker">Quote · 金句</div>
    <blockquote style="font-family:var(--serif-zh); font-weight:700; font-size:5.8vw; line-height:1.2; letter-spacing:-.01em; max-width:72vw">"引用原文。"</blockquote>
    <p class="lead" style="max-width:55vw; opacity:.65">英文翻译或注释。</p>
    <div class="meta-row"><span>— 出处</span><span>·</span><span>日期</span></div>
  </div>
  <div class="foot"><div>页码说明</div><div>— · —</div></div>
</section>
```

## Layout 9: 并列对比 (Before / After)

```html
<section class="slide light">
  <div class="chrome"><div>旧 vs 新</div><div>页号 / 总页数</div></div>
  <div class="frame" style="padding-top:5vh">
    <div class="kicker">Before / After · 范式转变</div>
    <h2 class="h-xl" style="margin-bottom:4vh">标题</h2>
    <div class="grid-2-6-6" style="gap:5vw 4vh">
      <div style="padding:3vh 2vw; border-left:3px solid currentColor; opacity:.55">
        <div class="kicker" style="opacity:.9">Before · 旧</div>
        <h3 class="h-md" style="margin-top:2vh">旧模式标题</h3>
        <ul style="margin-top:3vh; padding-left:1.2em; display:flex; flex-direction:column; gap:1.4vh; font-family:var(--sans-zh); font-size:max(14px,1.1vw); line-height:1.55">
          <li>旧方式描述</li>
        </ul>
      </div>
      <div style="padding:3vh 2vw; border-left:3px solid currentColor">
        <div class="kicker" style="opacity:.9">After · 新</div>
        <h3 class="h-md" style="margin-top:2vh">新模式标题</h3>
        <ul style="margin-top:3vh; padding-left:1.2em; display:flex; flex-direction:column; gap:1.4vh; font-family:var(--sans-zh); font-size:max(14px,1.1vw); line-height:1.55">
          <li>新方式描述</li>
        </ul>
      </div>
    </div>
  </div>
  <div class="foot"><div>页码说明</div><div>Before / After</div></div>
</section>
```

## Layout 10: 图文混排 (Lead Image + Side Text)

```html
<section class="slide light">
  <div class="chrome"><div>深度 · Deep Dive</div><div>页号 / 总页数</div></div>
  <div class="frame grid-2-8-4" style="padding-top:6vh">
    <div>
      <div class="kicker">Phase · 阶段名</div>
      <h2 class="h-xl" style="margin-top:1vh; margin-bottom:3vh">标题</h2>
      <p class="lead" style="margin-bottom:3vh">引导描述。</p>
      <p style="font-family:var(--sans-zh); font-size:max(14px,1.15vw); line-height:1.75; opacity:.78; margin-bottom:2.4vh">正文段落。</p>
      <div class="callout" style="margin-top:3vh">"引用"<div class="callout-src">— 来源</div></div>
    </div>
    <figure class="frame-img" style="aspect-ratio:3/4; max-height:60vh">
      <img src="images/figma.png" alt="描述">
      <figcaption class="img-cap">图片说明</figcaption>
    </figure>
  </div>
  <div class="foot"><div>页码说明</div><div>详情</div></div>
</section>
```

---

## 网格速查

| 类名 | 配比 | 用途 |
|------|------|------|
| `.grid-2-6-6` | 1:1 | 对半分 |
| `.grid-2-7-5` | 7:5 | 文字为主+辅助图 |
| `.grid-2-8-4` | 2:1 | 大段文字+小图 |
| `.grid-3` | 1:1:1 | 3项并列 |
| `.grid-3-3` | 3×2 | 6图矩阵 |
| `.grid-6` | 3×2 | 6数据卡 |
| `.grid-4` | 2×2 | 4数据卡 |
