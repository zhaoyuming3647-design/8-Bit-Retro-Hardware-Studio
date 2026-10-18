# 8-Bit Retro Hardware Studio

> **真实硬件级像素与 GIF 动图转换工作室 · Authentic 8-Bit Hardware Image & GIF Converter Studio**
> 
> 单文件纯前端架构 · 原生硬件分辨率 · 真实 ROM 色盘 · 瓦片属性冲突 (Attribute Clash) · 防卡顿异步渲染引擎

[Live Demo](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)
[](https://github.com/zhaoyuming3647-design/8-Bit-Retro-Hardware-Studio)
[](https://github.com/zhaoyuming3647-design/8-Bit-Retro-Hardware-Studio)
[License: MIT](https://www.google.com/search?q=https://github.com/zhaoyuming3647-design/8-Bit-Retro-Hardware-Studio/blob/main/LICENSE)

🎮 **在线免安装即刻体验 (Live Web App)**:  
👉 **[https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)**

*(支持全平台浏览器直接运行，手机移动端自动切换触控紧凑视图，支持完全离线使用)*

---

## 简体中文 (Chinese)

### 简介

**8-Bit Retro Hardware Studio** 是一款致力于**严格还原 1980 年代真实 8 位游戏主机与复古电脑图形芯片限制**的开源纯前端图像与 GIF 动图转换工具。

市面上大多数“像素化滤镜”仅仅是将图像简单打马赛克后做全局颜色量化，而真正 8-Bit 时代的游戏画面受限于极小的显存（VRAM 通常仅有 2KB~16KB），由显示芯片强制施加了不可逾越的**瓦片属性表（Attribute Table / Attribute Clash）**规则：
- **任天堂 FC / NES**：全屏被划分为 16×16 像素的属性网格，全图仅允许 4 组背景子色板，每个 16×16 区域必须强制选定其中 1 组（1 个全屏共享底色 + 3 个区域私有色）；
- **ZX Spectrum**：著名的 **8×8 颜色冲突**，每个 8×8 像素方格内严格只能同时显示 2 种颜色（INK 前景色与 PAPER 背景色）；
- **Commodore 64**：Multicolor 模式下 4×8 宽像素块最多容纳 4 种颜色（3 种全屏共享色 + 1 种 Color RAM 私有色）；
- **GIF 动图时间域防闪烁**：逐帧独立转换动图会导致背景大面积噪点闪烁。本项目引入了**硬件子色板跨帧锁定**与**Bayer 有序矩阵抖动**，使动图输出细腻且背景稳定。

本项目采用 **单文件 HTML5 架构**，零后端、零构建依赖，下载后直接双击即可离线运行，或一键部署至 GitHub Pages。

---

### v2.5 全新特性升级

1. **⚡ 防卡顿渲染与静帧调参系统（彻底告别掉帧与假死）**
   - **🎯 静帧实时调参 + 按钮渲染全帧（默认推荐）**：处理长动画 GIF 时，支持通过滑块任选某一张作为“调参基准静帧”；拖动任何滑块或切换参数时，**仅毫秒级实时重算该静帧**（拖拽极度丝滑），调满意后一键渲染全部动画帧；
   - **🖱️ 纯手动按钮渲染模式**：超高分辨率大图专用，改参数过程中不触发重算，参数调好后点击“立即执行硬件渲染”一次性生成；
   - **🔄 全帧自动重算模式**：适合小尺寸图片或单张静态图；
   - **异步非阻塞进度条（Chunked Async Pipeline）**：全帧渲染与 GIF 编码全部放入异步任务队列，每帧主动让出时间片刷新 UI 进度条（含实时百分比与取消按钮），主线程绝不假死。

2. **📐 全维度画幅横纵比与超高倍分辨率引擎**
   - **保持原图比例**：新增“🖼️ 按照原图横纵比生成 (Keep Original Ratio)”，自动读取并显示原图宽高比（如 3:2、照片长图），以真实 8-Bit 像素密度完美适配，不变形、不裁切；
   - **主流流媒体与社媒比例**：内置 **16:9**（B站/YouTube横屏）、**9:16**（抖音/TikTok竖屏）、**4:3**（复古CRT电视）、**1:1**（正方形头像/表情包）、**3:4**（小红书图文）、**21:9**（宽幅电影）；
   - **自由输入比例与像素**：支持自定义输入任意横纵比（`W : H`），或直接指定生成像素分辨率（`16 ~ 2560 px`，支持联动锁定比例）；
   - **手动输入高倍分辨率倍数**：除了 `0.25x ~ 8.0x` 快捷预设档位，右侧直接提供**常驻数字输入框**，支持键盘键入 `0.1x ~ 12.0x` 任意小数倍率！

3. **🎯 导出分辨率 1:1 严格匹配与自定义高倍放大**
   - 导出面板支持 **「🎯 1x (1:1 严格匹配设定分辨率)」**，上方设定多少实际像素，导出的 GIF/PNG 就是多少像素；
   - 支持在设定分辨率基础上再进行 `2x ~ 10x` 整数倍锐利放大，或手动输入任意导出倍数（最高 20x），并附带实时 **「最终导出尺寸像素回显」**。

4. **🌗 白天 / 黑夜模式与跟随系统 (Theme Switcher)**
   - 支持 **「🌗 跟随系统 (System)」、「🌙 黑夜模式 (Dark)」、「☀️ 白天模式 (Light)」**；
   - 实时监听系统级 `prefers-color-scheme`，随操作系统深浅色模式自动切换，并持久化本地记忆。

5. **📱 自动识别移动端 UI 与桌面端 UI (Responsive UI Mode)**
   - 自动检测手机/平板/桌面浏览器；
   - **移动端优化**：画布自动吸顶固定预览，底部提供 **「1. 选图 → 2. 主机/比例 → 3. 细节调优 → 4. 导出」** 分段 Tab 抽屉，放大触控热区，支持手指触控拖拽分割线对比。

6. **✨ 极简模式 (Simple Mode) 与 🛠️ 专业模式 (Pro Mode)**
   - **极简模式**：专为快速出图设计，隐藏底层复杂参数，用户只需 **① 选图 → ② 选主机与比例 → ③ 导出** 三步搞定；
   - **专业模式**：展开全部抖动强度、色彩距离算法、Tile 属性网格微调、精灵表与 JSON 数据导出。

---

### 10 大硬件规范对照表

| 主机 / 芯片平台 | 原生基准分辨率 | 像素宽高比 (PAR) | 系统总色盘 | 硬件属性约束规则 (Attribute Clash) |
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

#### 在线使用
直接在浏览器打开：  
👉 **[https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/](https://www.google.com/search?q=https://zhaoyuming3647-design.github.io/8-Bit-Retro-Hardware-Studio/)**

#### 本地运行
1. 克隆或下载本项目仓库：
   ```bash
   git clone https://github.com/zhaoyuming3647-design/8-Bit-Retro-Hardware-Studio.git
   ```
2. 双击打开 `index.html`（或 `8bit_retro_studio.html`）即可在任何现代浏览器中运行，无需安装 Node.js 或 Python 环境，支持断网离线使用。

#### 部署至自己的 GitHub Pages
1. 确保仓库根目录下有名为 `index.html` 的文件；
2. 进入仓库 **Settings** -> **Pages**，在 **Build and deployment** 下将 Branch 设为 `main` 分支的 `/ (root)`，点击 Save；
3. 数秒后即可获得在线地址。

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

### What's New in v2.5

1. **⚡ Anti-Lag Architecture & Reference Frame Tuning**
   - **🎯 Reference Preview Frame Mode (Default)**: Tweak parameters on a selected single static frame with sub-millisecond instant feedback; click *Apply & Render* to compute full GIF animations only when satisfied.
   - **🖱️ Manual Button Render Mode**: For ultra-high resolution images, parameters change without recalculating until the button is clicked.
   - **Async Chunked Progress Bar**: Multi-frame GIF quantization and GIF89a encoding run in non-blocking async slices with live percentage indicators, frame countdowns, and a cancel button.
2. **📐 Flexible Aspect Ratio & Resolution Engine**
   - **Keep Original Ratio**: Automatically preserves the original aspect ratio of uploaded photos or GIFs without distortion or letterboxing.
   - **Social & Streaming Presets**: 16:9 (Widescreen), 9:16 (Shorts/TikTok), 4:3 (CRT), 1:1 (Square), 3:4 (Portrait), 21:9 (Ultrawide).
   - **Direct Custom Resolution**: Enter custom aspect ratios (`W : H`) or exact pixel resolutions (`16 ~ 2560 px`).
   - **Direct Scale Multiplier Input**: Type any multiplier (e.g., `0.3x`, `1.8x`, `5.0x`, `10.0x`) directly in the numeric input box.
3. **🎯 1:1 Export Resolution Matching**
   - Select *1x (1:1 Exact Match)* to output the exact configured resolution, or scale up to *10x / 20x* with real-time export resolution readout.
4. **🌗 Dark / Light / Auto-System Theme**
   - Seamlessly synchronizes with your OS appearance (`prefers-color-scheme`) in real time.
5. **📱 Auto Device UI Mode**
   - Detects mobile vs. desktop viewports automatically; mobile layout fixes canvas to top and provides touch-sized tab controls.
6. **✨ Simple Mode vs. 🛠️ Pro Studio Mode**
   - Switch between a clutter-free 3-step workflow for casual users and a full-featured studio for pixel artists and retro coders.

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

This project is released under the [MIT License](https://www.google.com/search?q=https://github.com/zhaoyuming3647-design/8-Bit-Retro-Hardware-Studio/blob/main/LICENSE).
