# Retro-Style-Studio

**双引擎复古图像实验室 · Dual-Engine Retro Image Lab**

两个独立的纯前端单文件工具，在同一个仓库中并行部署，互不依赖。

**在线体验 / Live Demo**

| 工具 Tool | 入口 Entry |
|---|---|
| **8-Bit Retro Hardware Studio** 真实硬件级像素与 GIF 转换 | [👉 立即打开](https://zhaoyuming3647-design.github.io/Retro-Style-Studio/) |
| **DREAMCORE 旧核·梦核·怪核滤镜实验室** 像素级 Canvas 梦境渲染 | [👉 立即打开](https://zhaoyuming3647-design.github.io/Retro-Style-Studio/dreamcore.html) |

支持全平台浏览器，手机移动端自动适配，完全离线可用。

---

## 简体中文

### 简介

**Retro-Style-Studio** 是一个“双工具并行”的纯前端复古图像工作站。两个 HTML 文件各自独立、零后端、零构建依赖，下载后双击即可离线运行，也可一键部署至 GitHub Pages。

#### 工具一：8-Bit Retro Hardware Studio

严格还原 1980 年代真实 8 位游戏主机与微型电脑的图形硬件限制。不是简单马赛克，而是复刻显存约束下的 **Attribute Clash（瓦片属性冲突）**、真实 ROM 色盘与跨帧子色板锁定，让像素输出经得起硬件规格推敲。

**核心能力**
- FC/NES 16×16 属性网格、ZX Spectrum 8×8 颜色冲突、C64 Multicolor 4×8 色块
- 真实硬件分辨率与 Bayer 有序矩阵抖动
- GIF 动图时间域防闪烁（硬件子色板跨帧锁定）
- 异步分块渲染，长动图不卡死主线程
- 全维度画幅比例（16:9 / 9:16 / 4:3 / 1:1 / 3:4 / 21:9）

#### 工具二：DREAMCORE // 旧核·梦核·怪核滤镜实验室

基于 HTML5 Canvas 2D 的像素级梦境滤镜渲染器。不依赖 WebGL 与后端，逐像素操作完成旧核、梦核、怪核、模拟恐怖与 VHS 信号退化效果。

**核心能力**
- 12 款预设：千禧午后、阈限走廊、深海残梦、损坏磁带、模拟恐怖档案、深渊精神污染等
- 真实像素管线：RGB 通道分离、低清降采样、恐怖色阶断层、扫描线、雪花噪点、水平撕裂
- 怪核符号层：可拖拽 / 旋转 / 镜像的文字标签、眼部遮挡条、DV 日期戳、VHS OSD
- **风格 Seed / 复刻码**：任意随机或手动微调后的效果，均可编码为 `DC1-...` 复刻码或短数字种子，一键精确还原
- 内置 4 张程序化测试底图（走廊 / 晴空 / 泳池 / 游园），也支持拖拽本地图片
- 原图对比、PNG 导出

### 项目结构

```text
Retro-Style-Studio/
├── index.html        # 8-Bit Retro Hardware Studio
├── dreamcore.html    # DREAMCORE 旧核·梦核·怪核滤镜实验室
└── README.md
