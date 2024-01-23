---
title: "Markdown, Mathematical Expressions and VSCode"
description: Math expressions can be represented in Markdown. 
date: 2021-07-27T10:00:00+01:00
draft: false
toc: false
pinned: false
featuredImage: ''
tags: [Markdown, VSCode, KaTeX]
categories: [Documentation, Windows, Mac, Linux]
series: [Markdown]
---

Markdown documents can include elegant representations of algebraic formulae, using KaTeX.

<!--more-->

The [CommonMark](https://commonmark.org/) specification of Markdown does not include scope for representing formulae or equations.  Fortunately, there is [KaTeX](https://katex.org/), an excellent typesetting library, which can be embedded in Markdown. KaTeX is supported extensively.

VSCode supports $\KaTeX$ in Markdown, equations are rendered in the VSCode preview pane, <kbd>Ctrl</kbd> + <kbd>K</kbd> <kbd>V</kbd>.

Inline math equations are wrapped in single dollar signs. For example, `$x^2$` becomes $x^2$.

$\KaTeX$ blocks begin and end with two dollar signs:

```Latex
$$
x^2
$$
```
produces
$$
x^2
$$

Here are a few more examples:

Pythagorean Theorem

```latex
$$
a^2 + b^2 = c^2
$$
```

$$
a^2 + b^2 = c^2
$$

Einstein's Theory of Special Relativity

```latex
$$
e=mc^2
$$
```

$$
e=mc^2
$$

Matrices

```latex
$$
\begin{pmatrix}
a & b \cr
c & d
\end{pmatrix}
+
\begin{pmatrix}
e & f \cr
g & h
\end{pmatrix}
$$
```

$$
\begin{pmatrix}
a & b \cr
c & d
\end{pmatrix}
+
\begin{pmatrix}
e & f \cr
g & h
\end{pmatrix}
$$

Special Cases

```latex
$$
\begin{dcases}
   a &\text{if } b \cr
   c &\text{if } d
\end{dcases}
$$
```

$$
\begin{dcases}
   a &\text{if } b \cr
   c &\text{if } d
\end{dcases}
$$

See many more examples at [Cheat Sheet: Mathematical Notation in Markdown](https://www.upyesp.org/posts/makrdown-vscode-math-notation/).