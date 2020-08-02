---
title: "交叉引用"
---

##  `\label` 和 `\ref` 机制

当您在编写任意长度的文档时，您想要引用编号的项目，如：图片、表格或者公式。幸运的是，我们只需要进行设置
LaTeX 便能够自动的添加正确的编号。为了让 LaTeX 记住您文档中的一个点，您必须标记它，然后在其他位置引用它。

```latex
\documentclass{article}

\begin{document}
Hey world!

This is a first document.

\section{Title of the first section}

Text of material for the first section.

\subsection{Subsection of the first section}
\label{subsec:labelone}

Text of material for the first subsection.
\begin{equation}
  e^{i\pi}+1 = 0
\label{eq:labeltwo}
\end{equation}

In subsection~\ref{subsec:labelone} is equation~\ref{eq:labeltwo}.
\end{document}
```

这里有两个 `label{...}` 命令，一个在 subsection 之后，一个在 equation 环境内部。它们在最后一句的 `\ref{...}` 命令中一起出现。当您运行 LaTeX 时，它保存 labels 的信息到辅助文件`(.aux)`中。对于 `\label{subsec:labelone}` ，LaTeX 知道现在位于 subsection 环境中，所以保存了 subsection 的编号。对于 `\label{eq:labeltwo}`，LaTeX 知道最新的兴趣环境是 equation，所以它保存了对应 equation 的信息。当您要求引用时，LaTeX 在会辅助文件中得到它。

`subsec:` 和 `eq:` 不在 LaTeX 中使用；相反，它只是对最近处理的内容保持跟踪。但是，在您编写他们时可以帮助您记住标签的含义。

您也许会看到引用的内容在输出的 PDF 文件中显示为两个加粗的问号，**??**。这是由于辅助文件的工作性质所导致，在第一次编译文档时标签尚未保存到辅助文件中。再运行一次 LaTeX，您会得到正确的结果。（通常，在您编写文档时无论如何都会多次运行 LaTeX，因此在实践中这并不麻烦。）

You may see references that show in an output PDF
as boldface double question marks, **??**.
The explanation is that because of this auxiliary file work,
the first time that you compile a document the label has not
yet been saved.
Run LaTeX one more time and you'll be all set.

注意引用前的符号带子(`~`)。您不想在 `subsection` 和它的编号之间，或者在`equation` 和它的编号之间产生断行。放一个符号带子表示 LaTeX 不会在这里产生断行。

## 在哪里加入 `label`

`\label` 命令总是引用之前编号的实体：一个章节，一个公式，一个浮动体等。这意味着 `label` 总是添加在你想引用的东西 _后面_。特别是，当您创建浮动体时，`\label` 会在后面跟在（或者更好的方式是在里面） `\caption` 命令后面，但是在浮动体环境中。

In particular, when you create
floats, the `\label` has to come _after_ (or better, in), the `\caption` command,
but within the float environment.

## 练习

## Exercises

尝试添加新的可编号环境（section，subsection，编号的列表）来测试文档，找出让 `\label` 命令运行都需要多少次运行。

Try adding new numbered parts (sections, subsections, enumerated lists) to
the test document and finding out how many runs are needed to make `\label`
commands work.

添加一些浮动体，查看将 `\label` 命令放在 `\caption` _前面_ 而不是后面会发生什么；您能预测这个结果吗？

如果你把 `\label` 放在 equation 环境的 `\end{equation}` _后面_ 会发生什么？