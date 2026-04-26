---
name: xuemu-ppt
description: 雪沐江南厂牌PPT技能——5套汽车工业视觉风格（杂志风/黑板报/维度冲击/CFD水晶/电光纸），HTML交互版+MP4视频版双输出，自适应开幕画廊。触发词：做PPT、厂牌PPT、汽车概念PPT、工业风PPT、视频PPT、xuemu deck、杂志风PPT、黑板报PPT。
---

# xuemu-ppt · 雪沐江南厂牌PPT

## 这个 Skill 做什么

生成一份**单文件 HTML** 的横向翻页 PPT，可选 **MP4 视频版**（含开幕画廊 + BGM + SFX）。视觉基因来自雪沐江南公众号 50+ 篇汽车概念拆解文章的实战沉淀。

**5 套视觉风格**（一份 deck 只用一套）：
| # | 风格 | 气质 |
|---|------|------|
| 1 | 🖋 杂志风 | 纸纹理 + 普鲁士蓝 + 俯拍平铺，高端编辑杂志 × Braun 设计 |
| 2 | 📝 黑板报 | 暗绿黑板 + 粉笔手写 + 不锈钢零件，工程感最强 |
| 3 | 💥 维度冲击 | 2D 图纸 vs 3D 机械 撕裂/碾压，戏剧化发布 |
| 4 | 🔮 CFD 水晶 | 毛玻璃 + 全息 HUD + 青色发光线 + 爆炸图 |
| 5 | ⚡ 电光纸 | 赛博工业 + 酸色 + 电路板走线，高互动社媒 |

**双输出**：HTML 交互版（浏览器横向翻页） + MP4 视频版（开幕画廊 → 正片，连续 BGM + SFX）

## 何时使用 vs 不何时使用

**适合**：线下分享 / 行业内部讲话 / 产品发布 / 个人品牌展示 / 需要「一次做完，不用翻页工具」的网页版 slides / 汽车技术内容可视化

**不适合**：大段表格数据图表 / 培训课件 / 多人协作编辑 / 非视觉型内容

## 工作流

### Gate 0 · 模式判断（动手前必做）

- 用户给了**完整大纲 + 素材 + 图片** → **快速模式** · 跳过澄清，直接搭大纲 → 选风格 → 出成品
- 用户只给了**主题或模糊想法** → **顾问模式** · 用下方 9 问逐个对齐后再动手

### 顾问模式 · 9 问澄清清单

| # | 问题 | 为什么问 |
|---|------|---------|
| 0 | **选哪套视觉风格？**（5 套各展示预览卡：色板 + 气质关键词 + 适合场景）| 决定 CSS 变量 + 布局偏好 |
| 1 | 受众是谁？分享场景？ | 决定语言风格和深度 |
| 2 | 分享时长？（15min≈10页 / 30min≈20页） | 定页数 |
| 3 | 有没有原始素材？（文档/数据/旧PPT/文章链接） | 有素材就基于素材 |
| 4 | 有没有图片？放在哪？（≥1600px宽，标准比例） | 见下方图片约定 |
| 5 | **输出形态？** 仅 HTML / 仅视频 / 双输出 | 决定后续管线 |
| 6 | （视频模式）**开幕偏好？** 有 X 张图可用 | 自适应当前：≥10→画廊墙 / 3-9→卡片瀑布 / 1-2→聚焦 / 0→文字 |
| 7 | 有没有硬约束？ | 避免返工 |
| 8 | BGM 风格？（tech / ad / educational / tutorial，默认 tech） | 见 `references/audio-guide.md` |

快速模式用户只答 #0 和 #5。

### 搭大纲

用叙事弧模板：
```
钩子(Hook)      → 1 页   : 抛一个反差/问题/硬数据
定调(Context)   → 1-2 页 : 说明背景/你是谁
主体(Core)      → 3-5 页 : 核心内容，穿插不同布局
转折(Shift)     → 1 页   : 打破预期/新观点
收束(Takeaway)  → 1-2 页 : 金句/悬念/行动建议
```

配合**主题节奏表**（每页 light/dark/hero light/hero dark）。硬规则：无连续 3 页同主题、每 3-4 页插入 hero、8+ 页 deck 至少 1 个 hero dark + 1 个 hero light。

### 填充内容

#### HTML 路径

1. 拷贝 `assets/template.html` → 注入风格 CSS 变量块（从 `assets/styles/<style>.css` 复制 `:root` 块）
2. 替换 `<title>` 和 `[必填]` 占位符
3. 从 `references/layouts.md` 选布局骨架粘贴到 `<div id="deck">` 中
4. 替换文案 + 图片路径（图片放 `images/` 目录，命名 `{页号}-{语义}.{ext}`）
5. 对照 `references/checklist.md` 自检
6. `open index.html` 本地预览

#### 视频路径（HTML 路径完成后）

1. 将入场动画 CSS 块注入 template（已在 template 中预设）
2. 生成开幕序列（如有图）→ 独立 `opening.html`
3. Playwright 分别录制开幕 + 主 PPT
4. FFmpeg 拼接 → 一条连续 BGM 覆盖全程 → SFX 按时间轴分布
5. `ffprobe` 确认有 video + audio (stereo)

详见 `references/video-pipeline.md`。

### 图片约定

- **文件夹**：`images/` 下（和 `index.html` 同级）
- **命名**：`{页号}-{语义}.{ext}`，如 `01-cover.jpg`、`03-chassis.png`
- **规格**：≥1600px 宽，JPG 照片/PNG 透明，总大小 ≤10MB
- **比例**：只用标准比例（16:9 / 16:10 / 4:3 / 3:2 / 1:1），不用原图奇葩比例
- **替换**：同名覆盖最稳；文件名变了记得全局搜 `images/旧名` 改新名

## 5 套视觉风格

详见 `references/themes.md`。每套含：
- CSS 变量块（`:root` 中 `--bg-base` / `--ink-base` / `--accent` / `--surface` / `--bg-texture` / `--shadow-preset`）
- 3 个专属布局骨架
- 气质关键词 + 适合场景

**硬规则**：一份 deck 只用一套风格 / 不允许混搭 / 不允许自定义 hex 值 / 选风格时展示 5 张预览卡。

## 核心设计原则

1. **结构优于装饰** — 不用阴影、浮动卡片，信息靠大字号 + 字体对比 + 网格留白
2. **克制优于炫技** — WebGL 背景只在 hero 页透出，普通页几乎看不见
3. **内容层级由字号和字体共同定义** — 最大衬线=主标题，中衬线=副标，大非衬线=lead，小非衬线=body，等宽=元数据
4. **图片是第一公民** — 只裁底部，保证顶部和左右完整；网格用 `height:Nvh` 固定
5. **节奏靠 hero 页** — hero 和 non-hero 交替制造呼吸
6. **反 AI slop** — 不用紫渐变/emoji/圆角卡片+左border accent/SVG手画人脸的默认模式产物
7. **音乐是半条命** — 视频版必带 BGM+SFX 双轨，无声版等于未完成

## 资源文件导览

```
xuemu-ppt/
├── SKILL.md                    ← 你正在读
├── assets/
│   ├── template.html           ← 核心模板（WebGL + 翻页 + 入场动画 + 录制模式）
│   ├── styles/                 ← 5 套风格 CSS 变量块
│   │   ├── magazine.css
│   │   ├── blackboard.css
│   │   ├── dimension.css
│   │   ├── cfd-glass.css
│   │   └── holo-flux.css
│   ├── opening-templates/      ← 3 种开幕 HTML 模板
│   ├── bgm-*.mp3               ← 6 首场景化 BGM
│   └── sfx/                    ← 9 类 SFX 音效
├── references/
│   ├── layouts.md              ← 布局库
│   ├── themes.md               ← 5 套风格文档
│   ├── components.md           ← 组件手册
│   ├── checklist.md            ← 质量检查清单
│   ├── opening-guide.md        ← 开幕设计指南
│   ├── video-pipeline.md       ← 视频管线操作手册
│   └── audio-guide.md          ← 音频设计规则
└── scripts/
    ├── render-video.js         ← Playwright 录制
    ├── add-music.sh            ← BGM 混合
    └── convert-formats.sh      ← 格式转换
```
