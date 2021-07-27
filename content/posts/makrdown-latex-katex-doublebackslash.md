---
title: "LaTex & KaTeX Math Rendering, the Double Backslash \\\\ in Markdown"
description: Avoiding Double BackSlash Being Escaped in Katex and Latex  
date: 2021-07-27T08:00:00+01:00
draft: false
toc: false
featuredImage: ''
tags: [Latex, KaTex, Markdown]
categories: [Windows, Linux]
series: [Markdown]
---

The double backSlash, \\\\, when specified in math formula in LaTeX and KaTeX might not render correctly. This is due to the \\ character being used as an escape character in some rendering frameworks.

Within the context of KaTex (which is math specific) and when specifying math formula in LaTeX, a possible workaround is to use \cr as a replaced for \\\\. 

<!--more-->

For example,

```Katex
$$
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$
```

Might render as:

\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$

Where as:

```Katex
$$
\begin{pmatrix}
a & b \cr
c & d
\end{pmatrix}
$$
```

Renders as:



$$
\begin{pmatrix}
a & b \cr
c & d
\end{pmatrix}
$$


