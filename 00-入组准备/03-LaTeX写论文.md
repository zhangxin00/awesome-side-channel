# LaTeX：写出第一份研究笔记

[返回入组准备](README.md) · [上一节：SSH 做实验](02-SSH与北大VPN.md)

LaTeX 将 `.tex` 源文件编译成 PDF。本节用提供的示例写一页阅读笔记。

## 1. 选择环境

可以在 [Overleaf](https://www.overleaf.com/) 新建空白项目，也可以使用本地 TeX 环境。第一次使用建议先试 Overleaf。

在 Overleaf 上传下一节的两个文件，将 `main.tex` 设为主文件，选择 pdfLaTeX 编译。操作见[官方教程](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)。

本地环境需要包含 `pdflatex` 与 `bibtex` 的 TeX 发行版。在终端用 `pdflatex --version`、`bibtex --version` 检查；编辑器本身不是编译器。

## 2. 打开最小项目

示例文件：[main.tex](latex-example/main.tex) 与 [refs.bib](latex-example/refs.bib)。复制整个 `latex-example` 目录到自己的工作目录。

`main.tex` 的主体如下，完整文件可点击上方链接查看：

```latex
\documentclass{article}
\title{Reading Note}
\author{Your Name}
\begin{document}
\maketitle
\section{Research Question}\label{sec:question}
This note studies speculative execution attacks~\cite{kocher2019spectre}.
\section{Method and Evidence}
The question in Section~\ref{sec:question} requires an explicit threat model.
\bibliographystyle{plain}
\bibliography{refs}
\end{document}
```

`section` 划分章节，`label/ref` 管理交叉引用，`cite` 引用文献，`bibliography` 指定 `.bib` 文件。把示例正文换成自己的笔记。

## 3. 编译并检查

在**本地终端**进入自己复制的项目目录，按顺序运行：

```sh
pdflatex -halt-on-error main.tex
bibtex main
pdflatex -halt-on-error main.tex
pdflatex -halt-on-error main.tex
```

第一次生成引用信息，BibTeX 处理文献，后续编译更新编号。打开 `main.pdf`，应看到标题、两个章节、正文中的引用编号和末尾参考文献。在线编辑环境通常会自动执行所需的多轮编译。

试着修改正文再编译。保存 `.tex`、`.bib` 和 PDF，方便以后修改。

## 4. 接入 Zotero

完成 [Zotero 练习](01-Zotero看论文.md)后，先备份示例的 `refs.bib`，再用自己导出的 BibTeX 文件替换它。打开新文件查找条目的引用键，把 `main.tex` 中 `\cite{kocher2019spectre}` 的键改为实际导出的键。

重新编译，核对参考文献中的标题、作者和年份。

## 5. 写一页阅读报告

用自己的话写下论文的问题、攻击条件、方法和疑问，引用至少一篇论文。以后做实验时，可以继续加入方法、结果和图表。

若要写中文，可把文档类改为 `\documentclass[UTF8]{ctexart}` 并使用 XeLaTeX 编译，环境须已安装 `ctex` 和可用中文字体；本地命令中的 `pdflatex` 相应替换为 `xelatex`。第一次练习也可继续使用英文示例。

## 6. 常见报错

| 现象 | 优先检查 |
| --- | --- |
| 引用显示 `?` | 键名是否匹配、是否运行 BibTeX、是否完成后续编译 |
| 找不到 `.bib` | 文件是否在项目中，文件名与 `bibliography` 是否一致 |
| `Undefined control sequence` | 命令是否拼错，是否缺少所需宏包 |
| `Missing $ inserted` | 普通文字中的下划线是否写成了 `\_`；数学式是否置于数学环境 |
| 中文显示错误 | 是否使用支持中文的文档类、字体和编译器 |
| `Overfull ...` | 行、公式或表格超出宽度，检查 PDF 而不是忽略警告 |

先修复日志中的第一个错误，再重新编译。正式写论文时使用目标会议当年的模板。

完成后进入[第一周：如何阅读论文](../01-如何阅读论文/README.md)。更多排版建议见 [latex-advice](https://github.com/dspinellis/latex-advice)。
