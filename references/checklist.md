# 质量检查清单 (Checklist)

生成完 PPT 后逐项对照。P0 级别必须全部通过。

## P0 · 必须（未通过 = 不可交付）

- [ ] **大标题是衬线字体** — 如果显示成非衬线，检查 `h-hero` / `h-xl` 类是否在 template.html 中存在
- [ ] **无 emoji** — 全部使用 Lucide 线性图标。grep `[\u{1F300}-\u{1FAFF}]` 确认
- [ ] **图片网格只用 `height:Nvh`** — 不用 `aspect-ratio`，否则会撑破
- [ ] **图片不堆到页面底部** — 不用 `align-self:end`，用 grid + `align-items:start`
- [ ] **图片只用标准比例** — 16:9 / 16:10 / 4:3 / 3:2 / 1:1，不用原图奇葩比例（如 `2592/1798`）
- [ ] **中文大标题 ≤ 5 字且 `nowrap`** — 避免 1 字 1 行
- [ ] **标题用衬线、正文用非衬线、元数据用等宽** — 三层字体分工
- [ ] **chrome 和 kicker 不写同一句话** — chrome 是栏目标签（稳定），kicker 是本页钩子（独特）
- [ ] **每页 section 有 light/dark/hero light/hero dark 之一** — 不带主题 = fallback 出错
- [ ] **无连续 3 页同主题** — grep `class="slide` 确认
- [ ] **8+ 页 deck 有 ≥1 hero dark + ≥1 hero light**
- [ ] **grep `[必填]` 返回空** — 所有占位符已替换
- [ ] **`<title>` 已替换** — 不是 `[必填] 替换为PPT标题`
- [ ] **无紫渐变 / 圆角卡片+左 border accent / SVG 手画人脸** — 反 AI slop

## P1 · 重要（影响观感但不致命）

- [ ] **图片 `object-fit:cover` + `object-position:top center`** — 只裁底部
- [ ] **单张主图 ≤ `max-height:56vh`** — 不撑出视口
- [ ] **网格 gap 合理** — horizontal 3vw / vertical 4vh
- [ ] **foot 和 chrome 内容不重复**
- [ ] **大标题无孤字成行**
- [ ] **整体视觉有呼吸感** — hero 和 non-hero 比例约 1:3

## P2 · 视频专属（仅视频模式）

- [ ] **`window.__ready` 信号存在** — 否则录制会丢首帧
- [ ] **WebGL 录制时硬限 1080p** — `window.__recording` 时 canvas ≤ 1920
- [ ] **动画仅对 `.slide.active` 生效** — 不在所有 slide 上跑动画
- [ ] **`#nav` 和 `#hint` 有 `.no-record` 类**
- [ ] **`ffprobe` 确认有 audio stream** — 没音频 = 不是成品
- [ ] **BGM 一条轨覆盖全程** — 开幕到正片无间断
- [ ] **SFX 密度合理** — 专业品牌介绍 ~1 个/10s，产品发布 ~4-6 个/10s

## P3 · 优化

- [ ] **大标题字号调整** — 根据字数在 6-10vw 之间选择合适的
- [ ] **页面节奏** — 交叉使用不同布局，避免连续两页用同一种
- [ ] **hero 页留白充足** — 不超过 3 行文字
- [ ] **英文术语有衬线斜体** — Playfair Display italic
