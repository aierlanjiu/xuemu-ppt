# xuemu-ppt · 雪沐江南厂牌PPT技能

5套汽车工业视觉风格的 Claude Code / Codex 双平台 PPT 技能。HTML 交互版 + MP4 视频版双输出，自适应开幕画廊，Motion.js 动效引擎。

## 视觉风格

| # | 风格 | 气质 |
|---|------|------|
| 🖋 | 杂志风 | 纸纹理 + 普鲁士蓝 + 俯拍平铺 |
| 📝 | 黑板报 | 暗绿黑板 + 粉笔手写 + 不锈钢零件 |
| 💥 | 维度冲击 | 2D 图纸 vs 3D 机械 撕裂/碾压 |
| 🔮 | CFD 水晶 | 毛玻璃 + 全息 HUD + 青色发光线 |
| ⚡ | 电光纸 | 赛博工业 + 酸色 + 电路板走线 |

## 快速开始

### 安装到 Claude Code

```bash
git clone https://github.com/aierlanjiu/xuemu-ppt.git ~/.claude/skills/xuemu-ppt
```

### 安装到 Codex

```bash
git clone https://github.com/aierlanjiu/xuemu-ppt.git ~/.codex/skills/xuemu-ppt
```

### 使用

在 Claude Code 或 Codex 中说：

- "用 xuemu-ppt 做一份杂志风PPT"
- "帮我生成一份汽车概念拆解的视频PPT"
- "用 CFD 水晶风格做一份技术发布会deck"

## 特性

- **5 套视觉体系**：不只是配色，是完整的 CSS 变量 + 布局偏好 + 纹理系统
- **双输出**：HTML 交互版（浏览器横向翻页）+ MP4 视频版（开幕画廊 + 连续 BGM + SFX）
- **Motion.js 动效**：hero / cascade / directional / pipeline 四种动画配方
- **自适应开幕**：图多→画廊墙 / 图少→卡片瀑布 / 无图→文字动画
- **双模工作流**：素材充足→自动驾驶 / 需求模糊→9 问顾问模式
- **WebGL 双背景**：深色页钛金暗流 + 浅色页银色漩涡

## 文件结构

```
xuemu-ppt/
├── SKILL.md                    # 主技能文档
├── assets/
│   ├── template.html           # 核心模板
│   ├── motion.min.js           # Motion.js v11 动效引擎
│   ├── styles/                 # 5套风格CSS
│   ├── bgm-*.mp3               # 6首场景化BGM
│   └── sfx/                    # 9类34个SFX音效
├── references/
│   ├── layouts.md              # 布局库
│   ├── themes.md               # 风格文档
│   ├── components.md           # 组件手册
│   └── checklist.md            # 质量检查清单
└── scripts/
    ├── render-video.js         # Playwright录制
    ├── add-music.sh            # BGM混合
    └── convert-formats.sh      # 格式转换
```

## 技术栈

- Motion.js v11 动效引擎
- WebGL GLSL 着色器（全息色散 + 旋转涡流）
- Playwright 录制 + FFmpeg 编码
- 频段隔离 BGM + SFX 双轨音频
- CSS 三层变量体系（字体/色板/纹理）

## 灵感来源

- [guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) — Deck 结构 / WebGL / 排版系统
- [huashu-design](https://github.com/op7418/huashu-design) — 动画引擎 / 视频管线 / 音频系统
- 雪沐江南公众号 50+ 篇汽车概念拆解实战

## 贡献者

- [Claude Code](https://claude.ai/code) — Skill 架构设计、核心模板开发
- [Codex](https://github.com/openai/codex) — 双平台适配
- [DeepSeek V4 Pro](https://deepseek.com) — 内容生成与优化

## 许可

MIT
