# LaTeX Paper Live Editor

[![GitHub Pages](https://img.shields.io/badge/demo-live-brightgreen)](https://jiahanwang0411.github.io/latex-paper-editor/)

一款基于浏览器的 LaTeX 论文写作实时预览编辑器，专为 Elsevier `elsarticle [review]` 格式设计。左侧编辑、右侧即时预览 A4 分页效果，所见即所得。

**在线使用 → [https://jiahanwang0411.github.io/latex-paper-editor/](https://jiahanwang0411.github.io/latex-paper-editor/)**

## 功能概览

### 双栏实时预览

- 左侧为结构化编辑面板，右侧为 A4 比例的分页预览
- 内容自动分页，段落跨页时在合理位置断开并续接
- 支持 KaTeX 数学公式渲染（行内 `$...$`、行间 `$$...$$`、编号公式、多行对齐等）

### 编辑面板（五个标签页）

| 标签页 | 功能 |
|--------|------|
| **Meta** | 标题、作者（支持通讯作者/共同一作标记）、单位、摘要（含字数校验 150-250 词）、关键词、术语表 |
| **Figures** | 拖拽上传图片，设置宽度和标题，一键复制 `\begin{figure}` LaTeX 代码 |
| **Tables** | 三线表编辑器（booktabs 风格），可视化编辑行列，一键复制 `\begin{table}` 代码 |
| **Sections** | 各章节内容编辑，内置 15 个 LaTeX 快捷工具按钮（加粗、斜体、引用、公式、图表等） |
| **Back** | CRediT 贡献声明、利益冲突、数据可用性、致谢 |

### 光标同步与高亮

- 左侧光标移动时，右侧预览自动滚动到对应段落
- 光标所在位置的单词在预览中以黄色脉冲动画高亮显示
- 支持重复词的精确定位（基于出现次数索引匹配）
- 同步功能可通过 Sync 开关控制

### 工具栏快捷插入

在 Section 编辑器中，工具栏提供以下一键插入：

`B` 加粗 · `I` 斜体 · `Em` 强调 · `Cite` 引用 · `Ref` 交叉引用 · `Lbl` 标签 · `H2` 子标题 · `Eq` 编号公式 · `Align` 多行对齐 · `$x$` 行内公式 · `$$x$$` 行间公式 · `Fig` 图片环境 · `Tbl` 表格环境 · `SI` 单位 · `TODO` 待办标记

选中文本后点击按钮可自动包裹。

### 数据管理

- **自动保存**：所有编辑内容实时保存到浏览器 localStorage（400ms 防抖）
- **导出**：下载为 `paper_data_YYYY-MM-DD.json` 备份文件
- **导入**：加载之前导出的 JSON 文件恢复数据
- **重置**：一键恢复默认模板（有确认提示）

### 支持的 LaTeX 语法

预览器可渲染以下 LaTeX 结构：

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

## 快速开始

直接访问在线地址即可使用，无需安装：

👉 **[https://jiahanwang0411.github.io/latex-paper-editor/](https://jiahanwang0411.github.io/latex-paper-editor/)**

也可以下载 `index.html` 文件在本地浏览器打开（需要联网加载 KaTeX）。

## 技术说明

- 纯前端单文件应用，无后端依赖
- 数学公式渲染依赖 [KaTeX](https://katex.org/) (cdnjs CDN)
- 数据持久化使用浏览器 localStorage
- 分页算法通过离屏测量 + 二分查找实现精确断页

## 许可

MIT License
