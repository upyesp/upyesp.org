---
title: "LaTeX & KaTeX Math Rendering: The Double Backslash \\\\ in Markdown"
description: Avoiding Double Backslash Being Escaped in KaTeX and LaTeX  
date: 2021-09-16T08:00:00+01:00
draft: false
toc: false
pinned: false
featuredImage: ''
tags: [KaTeX, LaTeX, Markdown]
categories: [Documentation]
series: [Markdown]
---

The double backslash, '\\\\', when specified in math formula in LaTeX and KaTeX might not render correctly. Here's how to avoid that.

<!--more-->

This is due to the '\\' character being used as an escape character in some rendering frameworks.

Within the context of $\KaTeX$ (which is math specific) and when specifying math formula in $\LaTeX$, a possible workaround is to use '\cr' as a replacement for '\\\\'. 

## $\KaTeX$ Examples

### Matrices

The double backslash, '\\\\', in the matrix below:

```latex
$$
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$
```

Might render as:

$$
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$

Where as changing '\\\\' to '\cr', like this:

```latex
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

### Aligned Expressions

The double backslash, '\\\\', in the aligned expressions below:

```latex
$$
\begin{alignedat}{2}
10&x+ &3&y = 2 \\
3&x+&13&y = 4
\end{alignedat}
$$
```

Might render as:

$$
\begin{alignedat}{2}
10&x+ &3&y = 2 \\
3&x+&13&y = 4
\end{alignedat}
$$

Where as:

```latex
$$
\begin{alignedat}{2}
10&x+ &3&y = 2 \cr
3&x+&13&y = 4
\end{alignedat}
$$
```

Renders as:

$$
\begin{alignedat}{2}
10&x+ &3&y = 2 \cr
3&x+&13&y = 4
\end{alignedat}
$$

So when using $KaTeX$ in Markdown, consider using '\cr' rather than '\\\\'.
