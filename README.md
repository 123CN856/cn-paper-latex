# cn-paper-latex

**中文论文 LaTeX 模板 —— XeLaTeX + ctex，开箱即用，适合国内期刊与学位论文。**

---

## 特点

- ✅ **XeLaTeX + ctex**，中文标点挤压、断行、首行缩进全部正常
- ✅ **中文章节编号**：`一、二、三` / `（一）（二）`
- ✅ **三线表**（booktabs），符合中文论文排版惯例
- ✅ **摘要 / 关键词**独立环境
- ✅ 页脚页码、1.45 倍行距、宋体正文黑体标题
- ✅ 无需任何额外字体安装，用系统自带字体

---

## 快速开始

```bash
# 需要 TeX Live 或 MiKTeX
xelatex main.tex
xelatex main.tex   # 跑两遍，交叉引用才正确
```

或者用 `latexmk`：

```bash
latexmk -xelatex main.tex
```

---

## 目录结构

```
cn-paper-latex/
├── main.tex          # 主文件（改这里）
├── README.md
├── LICENSE
└── .gitignore
```

---

## 怎么改成你自己的

| 要改的地方 | 在 main.tex 里搜 |
|---|---|
| 标题 | `\title{` |
| 作者 | `陈\quad 诺` |
| 摘要 | `\begin{cnabstract}` |
| 关键词 | `\keywords{` |
| 正文 | `\section{` |

### 章节编号

已经在导言区写好了，**不用动**：

```latex
\titleformat{\section}{\Large\heiti}{\chinese{section}、}{0.3em}{}
\titleformat{\subsection}{\large\heiti}{（\chinese{subsection}）}{0.2em}{}
```

> **踩过的坑**：用 `\ctexset{section/number=...}` 会被 `titlesec` 覆盖，
> 编号会退回成阿拉伯数字。必须在 `\titleformat` 里直接指定 `\chinese{section}`。

---

## 字体说明

模板用 `ctex` 的 windows 字体集，自动调用系统字体：

| 用途 | 字体 |
|---|---|
| 正文 | 宋体（SimSun） |
| 标题 | 黑体（SimHei） |

**另一个坑**：`\bfseries\heiti` 会报 `TU/SimHei/b/n undefined` —— 因为 SimHei 没有粗体字重。
本模板已经去掉了 `\bfseries`，**黑体本身视觉上已经够粗**。

---

## 编译产物

`.gitignore` 已排除全部中间文件，只保留 `.tex` 和 `.pdf`。

---

## 适用场景

- 国内 CSSCI / 中文核心期刊论文
- 学位论文（需要改成 `ctexbook`）
- 课程论文、研究报告

> ⚠️ **注意**：多数中文期刊投稿要求 **Word（.docx）**，不是 LaTeX。
> 本模板适合：① 自己排版校对；② 生成高质量 PDF；③ 转 Word 的底稿；④ 投英文刊时复用结构。

---

## License

MIT
