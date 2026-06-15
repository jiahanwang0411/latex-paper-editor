# LaTeX Paper Live Editor

[![GitHub Pages](https://img.shields.io/badge/demo-live-brightgreen)](https://jiahanwang0411.github.io/latex-paper-editor/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

一款基于浏览器的 LaTeX 论文写作实时预览编辑器。左侧编辑、右侧即时预览 A4 分页效果，支持 **Elsevier / Wiley / ACS** 三大出版商共 12 种期刊模板一键切换。

**在线使用 → [https://jiahanwang0411.github.io/latex-paper-editor/](https://jiahanwang0411.github.io/latex-paper-editor/)**

## 多期刊模板一键切换

首次打开时进入模板选择界面，点击出版商卡片后选择具体期刊即可开始写作。编辑器内置了三大出版商系列共 12 种模板，每种模板的字体、章节编号、摘要样式、行间距等均按照对应期刊的真实 LaTeX 模板风格渲染：

| 出版商 | 可选模板 | 风格特征 |
|--------|---------|---------|
| **Elsevier** | elsarticle [review]、Solar Energy、Journal of Power Sources、Applied Energy | Times New Roman 衬线体，编号章节标题，1.75 行高 |
| **Wiley** | Wiley Standard、Advanced Materials、Angewandte Chemie、Advanced Energy Materials | STIX 衬线体正文，Angewandte 独有 Helvetica 无衬线标题 |
| **ACS** | ACS Standard、JACS、ACS Nano、ACS Energy Letters | 不编号章节标题，紧凑排版，ACS Energy Letters 最小字号 |

在编辑器中随时点击右上角 **Switch** 按钮切换模板——只改变预览样式，不影响已写好的内容。这意味着你可以用同一份稿件快速预览不同期刊的排版效果，方便选刊投稿。

## 功能概览

### 双栏实时预览

左侧为结构化编辑面板，右侧为 A4 比例的分页预览。内容自动分页，段落跨页时在合理位置断开并续接。支持 KaTeX 数学公式渲染（行内 `$...$`、行间 `$$...$$`、编号公式、多行对齐等）。

### 编辑面板（五个标签页）

| 标签页 | 功能 |
|--------|------|
| **Meta** | 标题、作者（支持通讯作者/共同一作标记）、单位、摘要（含字数校验 150-250 词）、关键词、术语表 |
| **Figures** | 拖拽上传图片，设置宽度和标题，一键复制 `\begin{figure}` LaTeX 代码 |
| **Tables** | 三线表编辑器（booktabs 风格），可视化编辑行列，一键复制 `\begin{table}` 代码 |
| **Sections** | 各章节内容编辑，内置 15 个 LaTeX 快捷工具按钮（加粗、斜体、引用、公式、图表等） |
| **Back** | CRediT 贡献声明、利益冲突、数据可用性、致谢 |

### 光标同步与高亮

左侧光标移动时，右侧预览自动滚动到对应段落。光标所在位置的单词在预览中以黄色脉冲动画高亮显示，支持重复词的精确定位（基于出现次数索引匹配）。同步功能可通过 Sync 开关控制。

### 工具栏快捷插入

Section 编辑器的工具栏提供 15 个一键插入按钮：

`B` 加粗 · `I` 斜体 · `Em` 强调 · `Cite` 引用 · `Ref` 交叉引用 · `Lbl` 标签 · `H2` 子标题 · `Eq` 编号公式 · `Align` 多行对齐 · `$x$` 行内公式 · `$$x$$` 行间公式 · `Fig` 图片环境 · `Tbl` 表格环境 · `SI` 单位 · `TODO` 待办标记

选中文本后点击按钮可自动包裹。

### 数据管理

所有编辑内容实时自动保存到浏览器 localStorage（400ms 防抖），关闭浏览器再打开仍然保留。支持导出为 JSON 备份文件和导入恢复，也可一键重置为空白模板。

## 使用说明

### 在线使用（推荐）

直接访问在线地址，无需安装任何软件：

👉 **[https://jiahanwang0411.github.io/latex-paper-editor/](https://jiahanwang0411.github.io/latex-paper-editor/)**

1. 首次打开会看到模板选择界面，点击出版商卡片（Elsevier / Wiley / ACS）
2. 选择具体期刊子模板（如 Solar Energy、Advanced Materials、JACS 等）
3. 进入编辑器后，在左侧面板编辑论文内容，右侧实时预览排版效果
4. 数据自动保存在浏览器中，下次打开同一浏览器会自动加载上次内容
5. 点击侧边栏的 **Switch** 按钮可随时切换期刊模板

### 本地使用

下载 `index.html` 文件后双击用浏览器打开即可。唯一的外部依赖是 KaTeX 数学公式渲染库（从 CDN 加载），因此需要网络连接。

```bash
# 方式一：直接双击打开
# 在文件管理器中双击 index.html 即可

# 方式二：使用本地 HTTP 服务器（推荐，避免 file:// 协议的跨域限制）
# Python 3
python -m http.server 8080
# 然后访问 http://localhost:8080

# Node.js (npx)
npx serve .
# 然后访问 http://localhost:3000
```

本地使用的数据同样保存在浏览器的 localStorage 中。如果需要在不同设备间迁移数据，使用 **Export** 导出 JSON 文件，再到另一台设备上 **Import** 导入。

### 写作流程建议

1. **Meta 标签页**：填写标题、作者信息、单位，撰写摘要和关键词
2. **Sections 标签页**：按章节编写正文内容，使用工具栏快捷按钮插入 LaTeX 语法
3. **Figures / Tables 标签页**：上传图片和创建三线表，用 "Insert Code" 复制 LaTeX 代码后粘贴到对应章节
4. **Back 标签页**：填写致谢、声明等附加信息
5. 随时切换不同期刊模板预览最终排版效果
6. 使用 **Export** 备份数据，或将 LaTeX 代码复制到 Overleaf 等平台进行最终排版

## 与 AI Agent 联动使用

本项目采用纯 HTML 单文件格式，这一设计使其天然适合与 AI Agent（如 ChatGPT、Claude、Copilot 等）协同工作：

### 单文件即完整应用

整个编辑器是一个自包含的 HTML 文件（约 2100 行），所有 CSS 样式、JavaScript 逻辑、页面结构均内联其中。AI Agent 只需读取和修改这一个文件即可完成任何功能迭代，无需理解项目目录结构、构建工具或依赖关系。

### 零构建直接运行

与 React/Vue 等前端框架不同，本项目不需要 `npm install`、`webpack`、`vite` 等任何构建步骤。AI Agent 修改代码后，刷新浏览器即可看到效果。这消除了 AI 在复杂构建链上浪费 token 和出错的可能性。

### 易于 AI 理解和修改

- 文件结构线性清晰：`<style>` → `<body>` → `<script>`，AI 可以精确定位修改位置
- 所有配置集中在 `TEMPLATES`、`DEFAULT_DATA` 等常量中，修改模板或默认内容只需改动几行
- CSS 通过 `body.tpl-*` 类名隔离，新增模板样式不会影响已有代码
- 使用传统 `var` / `function` 语法，兼容性最好，AI 生成代码时无需考虑现代 JS 特性差异

### 典型联动场景

- **让 AI 添加新期刊模板**：告诉 AI "请添加 Nature 期刊模板"，它只需在 `TEMPLATES` 中加一条配置、在 CSS 中加几行样式覆盖
- **让 AI 调整排版细节**：如"把摘要字号改大一点"、"给 ACS 模板加上行号"
- **让 AI 修复渲染问题**：如"公式编号在第二页没有重置"，AI 可直接定位 `processEquations` 函数修复
- **让 AI 扩展功能**：如"加入参考文献管理器"、"支持 Markdown 语法"，AI 在单文件中增量添加代码即可

### 版本管理与部署

单个 HTML 文件让 Git 版本管理极为简单——每次修改就是一次 commit，差异清晰可追溯。部署到 GitHub Pages、Netlify、Vercel 等任何静态托管平台都只需上传一个文件。

## 支持的 LaTeX 语法

预览器支持渲染以下 LaTeX 结构：

- 编号公式 `\begin{equation}` 与自动编号、`\label` 引用
- 多行公式 `\begin{align}` / `\begin{align*}`
- 行内/行间数学公式（KaTeX 渲染）
- `\subsection{}` 子标题
- `\begin{figure}` 图片环境（含 `\includegraphics`、`\caption`、`\label`）
- `\begin{table}` 三线表（解析 `\toprule`、`\midrule`、`\bottomrule`）
- `\cite{}` → 蓝色编号引用 `[N]`
- `\ref{}` → 自动解析为 "Fig. N" / "Table N" / "(N)"
- `\textbf{}`、`\textit{}`、`\emph{}`
- `\todo{}` → 红色待办标记
- `\noindent`、`\indenttwo{}`

## 技术说明

- 纯前端单文件应用，无后端依赖
- 数学公式渲染依赖 [KaTeX](https://katex.org/) (cdnjs CDN)
- 数据持久化使用浏览器 localStorage
- 分页算法通过离屏测量 + 二分查找实现精确断页
- 模板切换通过 `body.tpl-*` CSS 类名 + `TEMPLATES` 配置对象实现

## 许可

MIT License
