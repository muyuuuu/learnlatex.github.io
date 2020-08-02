---
title: "更多: 交叉引用"
---

## 为交叉引用添加链接

通过 `hyperref` 宏包，您可以为交叉引用添加超链接。在大多情况下，`hyperref` 应该在导言区的其他宏包被指定之后才加载。

```latex
\documentclass{article}
\usepackage[hidelinks]{hyperref}
\begin{document}

\section{Introduction}
Some exciting text with a reference~\ref{sec:next}.

\section{Next thing}
\label{sec:next}

More text here.
\end{document}
```

我们选择了让链接和正常文本颜色相同，尝试删除 `hidelinks` 查看这是为什么！