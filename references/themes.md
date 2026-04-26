# 视觉风格 (Themes)

5 套汽车工业视觉风格，**一份 deck 只用一套**。不允许混搭、不允许自定义 hex 值。

## 使用方法

1. 基于用户内容推荐一套，或展示 5 张预览卡让用户选
2. 打开 `assets/template.html`，找到 `:root{` 块中「风格主题」注释区域
3. 从 `assets/styles/<style>.css` 复制对应的 `:root` 变量块，整体替换
4. 其他 CSS 都走 `var(--...)`，无需任何其他改动

---

## 🖋 杂志风 (Magazine)

**适合**: 通用分享 / 商业发布 / 品牌展示 / 不知道选啥的默认

**调性**: 纸纹理 + 普鲁士蓝 + 90° 俯拍平铺 + 硬日光影。像 *Monocle* × Braun 设计。

```css
--bg-base:#f1efea; --bg-rgb:241,239,234; --bg-tint:#e8e5de;
--ink-base:#0a0a0b; --ink-rgb:10,10,11; --ink-tint:#18181a;
--accent:#c44536; --accent-rgb:196,69,54;
--surface:rgba(255,255,255,.7); --bg-texture:none;
--shadow-preset:0 12px 40px -16px rgba(0,0,0,.15);
```

**专属布局**: Hero 俯拍封面 · 左文右图 7:5 · 大字报 grid-6

---

## 📝 黑板报 (Blackboard)

**适合**: 工程教育 / 硬核技术分享 / 需要强烈差异化的场景

**调性**: 暗绿黑板 + 粉笔白线 + 不锈钢 3D 零件 + 游标卡尺道具。像工程课堂 × 实验室。

```css
--bg-base:#1a2a1f; --bg-rgb:26,42,31; --bg-tint:#253d2c;
--ink-base:#d4c8a8; --ink-rgb:212,200,168; --ink-tint:#b8a878;
--accent:#c44a3a; --accent-rgb:196,74,58;
--surface:rgba(212,200,168,.08); --bg-texture:none;
--shadow-preset:none;
```

**字体例外**: 标题可替换为行书手写体（Xingshu），正文保持非衬线

**专属布局**: 全屏黑板+大标题 · 手写侧栏+3D 零件图 · 粉笔数据卡 grid-3

---

## 💥 维度冲击 (Dimension Breaker)

**适合**: 产品发布 / 概念演示 / 需要戏剧化冲击力的场景

**调性**: 2D 图纸 vs 3D 机械 冲突/撕裂/碾压。重工业 × 高端编辑。

```css
--bg-base:#f5f0e8; --bg-rgb:245,240,232; --bg-tint:#e0d5b8;
--ink-base:#1a1a1a; --ink-rgb:26,26,26; --ink-tint:#3a3a3a;
--accent:#e63900; --accent-rgb:230,57,0;
--surface:rgba(255,255,255,.6); --bg-texture:none;
--shadow-preset:0 16px 48px -8px rgba(0,0,0,.3);
```

**专属布局**: 图纸撕裂+3D 冲破 · 2D 蓝图 vs 3D 实物对比 · 冲击大字报

---

## 🔮 CFD 水晶 (Crystal Slate)

**适合**: 技术发布会 / 工程仿真展示 / 数据密集型分享

**调性**: 毛玻璃 + 全息 HUD + 青色发光线 + 爆炸图。空间计算 × 工程仿真。

```css
--bg-base:#0a1628; --bg-rgb:10,22,40; --bg-tint:#0d2240;
--ink-base:#e0f0ff; --ink-rgb:224,240,255; --ink-tint:#a0c8e8;
--accent:#00d4ff; --accent-rgb:0,212,255;
--surface:rgba(255,255,255,.05); --bg-texture:none;
--shadow-preset:0 0 30px rgba(0,212,255,.15);
```

**专属布局**: 毛玻璃 HUD+标题 · 爆炸图+数据标注 · 雷达图网格

---

## ⚡ 电光纸 (Holo-Flux)

**适合**: 社媒传播 / Z 世代受众 / 需要高互动性的视觉内容

**调性**: 赛博工业 + 全息纹理 + 酸色 + 电路板走线。像 Cyberpunk × 社媒卡片。

```css
--bg-base:#0d0d0d; --bg-rgb:13,13,13; --bg-tint:#1a1a2e;
--ink-base:#e0ffe0; --ink-rgb:224,255,224; --ink-tint:#80cc80;
--accent:#39ff14; --accent-rgb:57,255,20;
--surface:rgba(57,255,20,.05); --bg-texture:none;
--shadow-preset:0 0 20px rgba(57,255,20,.2);
```

**专属布局**: 电路板走线+标题 · 酸色对比卡 2 列 · 全息数据流

---

## 推荐选择参考

| 如果是... | 推荐风格 |
|-----------|---------|
| 不知道选啥 / 第一次用 | 🖋 杂志风 |
| 汽车工程 / 技术培训 | 📝 黑板报 |
| 产品发布 / 概念展示 | 💥 维度冲击 |
| 数据报告 / 技术白皮书 | 🔮 CFD 水晶 |
| 社媒传播 / 年轻受众 | ⚡ 电光纸 |

## ❌ 不要做的事

- 不要混搭（如杂志风的 bg + 黑板报的 ink）
- 不要让用户自定义 hex 值
- 一份 deck 中途不要切换风格
- 不要修改 template.html 中 `:root` 以外的地方的颜色
