# 8-Bit Retro Hardware Studio

> **真实硬件级像素与 GIF 动图转换器 · Authentic 8-Bit Hardware Image & GIF Converter**
> 
> 单文件纯前端架构 · 原生硬件分辨率 · 真实 ROM 色盘 · 瓦片属性冲突 (Attribute Clash) · GIF 动图防闪烁引擎

[Live Demo](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)
[GitHub Repo](https://www.google.com/search?q=https://github.com/zhaoyuming3647-design/8-Bit-Retro-Hardware-Studio)
[License: MIT](https://www.google.com/search?q=LICENSE)

🎮 **在线免安装即刻体验 (Live Web App)**:  
👉 **[https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)**

*(如果你的仓库内主页面文件名仍为 `8bit_retro_studio.html`，可直接访问：[在线备用链接](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/8bit_retro_studio.html)；或建议将文件在仓库中重命名为 `index.html`)*

---

## 简体中文 (Chinese)

### 简介

**8-Bit Retro Hardware Studio** 是一款致力于**严格还原 1980 年代真实 8 位游戏主机与微型电脑图形硬件限制**的开源纯前端图像/动图转换工作室。

不同于市面上常见的“低分辨率马赛克+全局 256 色量化”滤镜，8-Bit 时代真实的显存（VRAM 通常仅有 2KB~16KB）受限于极度严苛的**瓦片属性表（Attribute Table / Attribute Clash）**：
- **任天堂 FC / NES**：全屏被划分为 16×16 像素的属性网格，全图仅能定义 4 组背景子色板，每个 16×16 块必须强制绑定其中 1 组（1 个全屏共享底色 + 3 个块私有色）；
- **ZX Spectrum**：著名的 **8×8 颜色冲突**，每个 8×8 像素方格内严格只能同时显示 2 种颜色（INK 前景色与 PAPER 背景色）；
- **Commodore 64**：Multicolor 模式下 4×8 宽像素块最多容纳 4 种颜色（3 种全屏共享色 + 1 种 Color RAM 私有色）；
- **GIF 动图时间域一致性**：传统图像转换在处理动图时，每帧独立计算色盘会导致背景大面积雪花闪烁。本工具创新性地引入了**硬件子色板跨帧锁定**与**有序矩阵抖动（Bayer Matrix Dithering）**，完美解决了动图闪烁难题。

项目为 **单文件 HTML5 架构**，零后端、零构建依赖，下载后直接双击即可离线运行，或一键部署至 GitHub Pages。

---

### 核心特性

1. **10 大经典 8-Bit 硬件平台对标**
   - **Nintendo FC / NES (Ricoh 2C02)**: 256×240 原生分辨率，标准 54 色 NTSC 硬件色盘，真实 16×16 属性块或 MMC5 8×8 细粒度瓦片量化。
   - **Game Boy Classic (DMG-01)**: 160×144，经典 4 阶橄榄绿 LCD 液晶显示。
   - **Game Boy Pocket (MGB-001)**: 160×144，4 阶纯正黑白灰阶。
   - **Game Boy Color (CGB)**: 160×144，8 组 4 色背景子色板，15-bit RGB555 硬件空间聚类。
   - **Sinclair ZX Spectrum**: 256×192，15 色（7 色相 × 正常/高亮），精确再现 8×8 属性冲突（Attribute Clash）。
   - **Commodore 64 (VIC-II)**:
     - Multicolor 模式：160×200（2:1 宽像素渲染为 320×200），4×8 块限 4 色（3 共享 + 1 块私有）。
     - Hi-Res 模式：320×200，8×8 块限 2 色。
   - **MSX / ColecoVision (TMS9918A)**: 256×192，8×1 水平扫描线段限 2 色。
   - **Sega Master System (Mark III)**: 256×192，64 色 RGB222 色盘，双 16 色硬件子色板。
   - **Apple II (Hi-Res)**: 140×192（2:1 宽像素），7×1 像素组严格遵循 NTSC 彩色副载波相位群限制。
   - **PICO-8**: 128×128 正方形经典 16 色 Fantasy Console 规格。

2. **多帧 GIF 动图防闪烁引擎**
   - 原生支持上传多帧 Animated GIF，内置帧合成管线；
   - **首帧硬件子色板锁定（Temporal Palette Lock）**：自动保持全屏硬件子色板在动画周期内稳定，根除闪烁；
   - 动画播放控制条：支持实时播放/暂停、单帧逐帧步进、0.5x~2.0x 播放倍速调节、以及 1x/2x/3x 抽帧模拟复古主机低帧率感。

3. **多样化抖动与色彩距离模型**
   - **有序矩阵抖动（动图推荐）**：Bayer 2×2（经典 FC 棋盘格）、Bayer 4×4、Bayer 8×8、Cluster 4×4 网点抖动、水平扫描线抖动；
   - **误差扩散抖动（静态图推荐）**：Floyd-Steinberg、Atkinson（经典 Mac 高反差质感）、Sierra Lite；
   - **色彩匹配距离**：Redmean 人眼感知加权 RGB、BT.601 明度优先、标准线性欧氏距离。

4. **实时硬件属性检查器与视口对比**
   - 三种对比视图：单画面、双栏对比、实时左右滑动分割线对比；
   - 硬件属性网格叠加：高亮显示当前系统 16×16、8×8、4×8 或 8×1 瓦片边界；
   - 交互式瓦片探测：鼠标悬停任意像素，实时显示该瓦片坐标、ID 及绑定的硬件 HEX 色盘；
   - 硬件色盘探测器：可视化展开系统 Master ROM 色盘与当前帧激活的各组子色板，支持一键复制 HEX；
   - CRT 监视器模拟：可选纯净像素输出或叠加扫描线与磷光栅格质感。

5. **多规格无损像素导出**
   - **8-Bit Animated GIF 导出**：内置纯 JS 编写的二进制 GIF89a LZW 编码器，支持 1x~4x 整数倍锐利放大，防社交媒体压缩模糊；
   - **PNG 单帧导出**；
   - **序列帧精灵表（Sprite Sheet）导出**：一键生成游戏引擎（Unity / Godot / Phaser）即开即用的网格精灵图；
   - **硬件配置 JSON 导出**：导出瓦片分配数据与 HEX 调色板，方便复古游戏开发者直接导进 ROM 开发工具。

---

### 硬件规范对照表

| 主机 / 芯片平台 | 原生分辨率 | 像素宽高比 (PAR) | 系统总色盘 | 硬件属性约束规则 (Attribute Clash) |
| :--- | :--- | :--- | :--- | :--- |
| **Nintendo FC / NES** | 256 × 240 | 1 : 1 | 54 色 (2C02 NTSC) | **16×16 像素**属性块从 4 组子色板中选 1 组（1 共享底色 + 3 块私有色） |
| **Game Boy DMG** | 160 × 144 | 1 : 1 | 4 阶橄榄绿 | 8×8 瓦片，全屏 2bpp 固定灰度 |
| **Game Boy Pocket** | 160 × 144 | 1 : 1 | 4 阶纯灰度 | 8×8 瓦片，中性黑白灰度 |
| **Game Boy Color** | 160 × 144 | 1 : 1 | 32,768 色 (RGB555) | 8×8 瓦片，同屏划分 8 组 4 色背景子色板 |
| **ZX Spectrum** | 256 × 192 | 1 : 1 | 15 色 (带 Bright 位) | **8×8 属性冲突**：每个 8×8 网格严格限 2 色（INK + PAPER），且需共享 Bright 位 |
| **Commodore 64 (Multi)** | 160 × 200 | 2 : 1 宽像素 | 16 色 (VIC-II) | **4×8 宽像素块**限 4 色（3 全局共享寄存器色 + 1 块 Color RAM 色） |
| **Commodore 64 (Hi-Res)** | 320 × 200 | 1 : 1 | 16 色 (VIC-II) | **8×8 像素块**限 2 色（从 16 色中任选 2 色） |
| **MSX (TMS9918A)** | 256 × 192 | 1 : 1 | 15 色 | **8×1 水平扫描线段**内严格限 2 色（前景色 + 背景色） |
| **Sega Master System** | 256 × 192 | 1 : 1 | 64 色 (RGB222) | 8×8 瓦片，从 64 色主色盘提取 2 组 16 色硬件调色板 |
| **Apple II (Hi-Res)** | 140 × 192 | 2 : 1 宽像素 | 6 色 (NTSC 相位) | **7×1 像素组**：每个 7 像素字节内绿/紫与橙/蓝不可混用 |
| **PICO-8** | 128 × 128 | 1 : 1 | 16 色 | 8×8 瓦片，严格模式每块限 4 色 |

---

### 使用与部署方法

#### 在线使用 (GitHub Pages)
直接访问项目在线地址：
👉 **[https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)**

> **提示**：若打开显示 404，请确认仓库设置：
> 1. 进入仓库 **Settings** -> 左侧 **Pages**；
> 2. **Build and deployment** 下的 **Branch** 选择 `main` 分支，目录选择 `/ (root)`，点击 **Save**；
> 3. 确保仓库根目录下的入口 HTML 文件名为 `index.html`（如果当前上传的文件名为 `8bit_retro_studio.html`，可以在 GitHub 仓库页面将其重命名为 `index.html`，或者访问 `.../8bit_retro_studio.html`）。

#### 本地运行
1. 克隆或下载本项目仓库；
2. 直接在任何现代浏览器中双击打开 `index.html`（或 `8bit_retro_studio.html`）即可使用，支持完全离线操作。

---

## English (README)

### Overview

**8-Bit Retro Hardware Studio** is an open-source, client-side web application engineered to **accurately reproduce authentic 1980s 8-bit gaming console and retro microcomputer graphics constraints**.

🎮 **Live Web Application**:  
👉 **[https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)**

Unlike generic "pixelate filter" tools that merely downsample an image and perform standard 256-color quantization, genuine 8-bit video hardware (operating under tiny 2KB–16KB VRAM limitations) strictly enforced **tile attribute tables and attribute clash rules**:
- **Nintendo Entertainment System (NES / Famicom)**: The screen is segmented into 16×16 pixel attribute blocks. Only 4 background sub-palettes can be defined simultaneously, and each 16×16 area must choose exactly 1 sub-palette (1 global backdrop color + 3 block colors).
- **Sinclair ZX Spectrum**: The iconic **8×8 Attribute Clash** — each 8×8 pixel grid can only contain 2 colors (INK and PAPER) from the same brightness bank.
- **Commodore 64**: Multicolor mode restricts each 4×8 wide-pixel cell to 4 colors (3 globally shared colors + 1 per-block Color RAM color).
- **Temporal Consistency for Animated GIFs**: Naive frame-by-frame quantization causes massive noise and flicker across frames. This tool integrates **temporal sub-palette locking** and **Bayer ordered dithering** to ensure rock-solid animated retro GIFs.

Built as a **single-file self-contained HTML5 application**, it requires zero build steps, zero backend services, and runs entirely in your browser offline.

---

### Key Features

1. **10 Authentic 8-Bit Hardware Architectures**
   - Full support for NES (2C02 NTSC 54-color ROM palette & 16×16 attribute blocks), Game Boy DMG (4-shade olive green), Game Boy Pocket (neutral monochrome), Game Boy Color (RGB555 tile sub-palettes), ZX Spectrum (8×8 ULA clash), C64 Multicolor & Hi-Res, MSX TMS9918A (8×1 line clash), Sega Master System, Apple II (7×1 artifact group clash), and PICO-8.
2. **Anti-Flicker Animated GIF Engine**
   - Multi-frame GIF upload, decoding, and playback timeline controller;
   - First-frame hardware palette lock prevents jarring color switches across animation frames;
   - Pure-JavaScript GIF89a binary LZW encoder allows exporting high-speed retro GIFs directly in the browser.
3. **Advanced Dithering & Color Metrics**
   - Ordered matrices (Bayer 2×2, 4×4, 8×8, Cluster Dot, Scanline) with adjustable spread strength;
   - Error diffusion (Floyd-Steinberg, Atkinson, Sierra Lite) with per-block palette boundary clamping;
   - Color metrics: Perceptual Redmean, BT.601 Luma priority, and Linear sRGB Euclidean.
4. **Interactive Hardware Inspector**
   - Side-by-side and interactive split slider comparisons;
   - Overlay attribute grids matching native hardware dimensions (16×16, 8×8, 4×8, 8×1);
   - Live tile hover inspector displaying block coordinates, sub-palette assignment, and active hex colors;
   - CRT scanline & phosphor simulation toggle.
5. **Lossless Integer Export Options**
   - Export crisp, unblurred 1x–4x scaled **Animated GIFs**;
   - Export current frame as **PNG**;
   - Export animation sequences as **Sprite Sheet PNGs** ready for game engines (Unity, Godot, Phaser);
   - Export **Hardware Specification JSON** containing color maps and tile structures.

---

### Hardware Specification Matrix

| Console / Chipset | Native Res | Pixel Aspect Ratio | System Master Palette | Hardware Attribute Constraint Rule |
| :--- | :--- | :--- | :--- | :--- |
| **Nintendo FC / NES** | 256 × 240 | 1 : 1 | 54 Colors (2C02 NTSC) | **16×16 Attribute Block** selects 1 of 4 sub-palettes (1 backdrop + 3 unique colors) |
| **Game Boy DMG** | 160 × 144 | 1 : 1 | 4 Olive Green Shades | 8×8 Tiles, fixed 2bpp monochrome LCD gamut |
| **Game Boy Pocket** | 160 × 144 | 1 : 1 | 4 Grayscale Shades | 8×8 Tiles, neutral monochrome LCD |
| **Game Boy Color** | 160 × 144 | 1 : 1 | 32,768 Colors (RGB555) | 8×8 Tiles, 8 sub-palettes of 4 colors each |
| **ZX Spectrum** | 256 × 192 | 1 : 1 | 15 Colors (Normal/Bright) | **8×8 Attribute Clash**: Max 2 colors (INK + PAPER) per 8×8 block sharing Bright bit |
| **Commodore 64 (Multi)** | 160 × 200 | 2 : 1 Wide Pixels | 16 Colors (VIC-II) | **4×8 Wide-Pixel Block**: 3 global shared colors + 1 Color RAM color per block |
| **Commodore 64 (Hi-Res)** | 320 × 200 | 1 : 1 | 16 Colors (VIC-II) | **8×8 Pixel Block**: Max 2 colors per block selected from the 16 VIC-II colors |
| **MSX (TMS9918A)** | 256 × 192 | 1 : 1 | 15 Colors | **8×1 Horizontal Strip**: Max 2 colors per 8-pixel byte |
| **Sega Master System** | 256 × 192 | 1 : 1 | 64 Colors (RGB222) | 8×8 Tiles, 2 sub-palettes of 16 colors |
| **Apple II (Hi-Res)** | 140 × 192 | 2 : 1 Wide Pixels | 6 Colors (NTSC Artifact) | **7×1 Byte Group**: Cannot mix Green/Violet with Orange/Blue in the same group |
| **PICO-8** | 128 × 128 | 1 : 1 | 16 Colors | 8×8 Tiles, 16 fixed colors (Max 4 colors per tile in strict mode) |

---

### Acknowledgements & Credits / 致谢与声明

- **AI Collaboration & Development**: Specially designed, architected, and developed with **Gemini** (Google DeepMind).
- **Retro Computing Inspirations**:
  - Steven Hugg ([8bitworkshop](https://8bitworkshop.com/) / [Dithertron](https://github.com/sehugg/dithertron)) for foundational retro architecture insights.
  - Dean McNamee ([omggif](https://github.com/deanm/omggif)) for the browser GIF parsing library.
  - Rilden ([tiledpalettequant](https://github.com/rilden/tiledpalettequant)) for tile quantization research.
  - Nesdev Wiki and C64-Wiki contributors for detailed hardware attribute table specifications.

---

### License

This project is released under the [MIT License](https://www.google.com/search?q=LICENSE).
