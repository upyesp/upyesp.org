---
title: "Cheat Sheet: Math Notation In Markdown With VSCode"
description: Cheat Sheet of common mMath notation in Markdown documents. 
date: 2022-09-05T10:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [Markdown, VSCode, KaTeX]
categories: [Documentation, Windows, Mac, Linux]
series: [Markdown]
---

A quick reference cheat sheet, on how to write math notation in Markdown documents, as supported in native VSCode.  Note that editor VSCode supports math notation based on TeX, LaTex, and KaTeX, without having to install  further libraries or applications that are sometimes required when using other editors and authoring tools.

<!--more-->

VSCode supports $\KaTeX$ in Markdown. Layout, as with $\LaTeX$, is based on $\TeX$, created by [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth). Equations are rendered in the VSCode preview pane, enabled with <kbd>Ctrl</kbd> + <kbd>K</kbd> <kbd>V</kbd>.

Inline math notation is wrapped in single dollar signs. For example, `$x^2$` becomes $x^2$.

$\KaTeX$ blocks begin and end with two dollar signs. So...

```Latex
$$
\sum_{
\begin{subarray}{l}
   i\in\Lambda\\
   0<j<n
\end{subarray}}
$$
```
produces

$$
\sum_{
\begin{subarray}{l}
   i\in\Lambda\\
   0<j<n
\end{subarray}}
$$

## Arithmetic

| Notation                         |                         Example                        |                          Inline                          | Block                         |
|----------------------------------|:------------------------------------------------------:|:--------------------------------------------------------:|-------------------------------|
| Addition                         |                          $a+b$                         |                          `$a+b$`                         | `$$`<br>`a+b`<br>`$$`         |
| Subtraction                      |                          $a-b$                         |                          `$a-b$`                         | `$$`<br>`a-b`<br>`$$`         |
| Various Forms of Multiplication  |        $a \times b$<br>$a \ast b$<br>$a \cdot b$       |         `$a\timesb$`<br>`$a\astb$`<br>`$a\cdotb$`        | `$$`<br>`a\cdotb`<br>`$$`     |
| Various Forms of Division        | $a \colon b$<br>$a / b$<br>$a \div b$<br>$\frac{a}{b}$ | `$a\colonb$`<br>`$a/b$`<br>`$a\divb$`<br>`$\frac{a}{b}$` | `$$`<br>`a\divb`<br>`$$`      |
| Remainder / Modulo               |                     $5 \mod 2 = 1$                     |                       `$5\mod2=1$`                       | `$$`<br>`5\mod2=1`<br>`$$`    |
| Negative Value                   |                          $-a$                          |                          `$-a$`                          | `$$`<br>`-a`<br>`$$`          |
| Plus or Minus, Minus or Plus     |                   $\pm a$<br>$\mp a$                   |                   `$\pma$`<br>`$\mpa$`                   | `$$`<br>`\pma`<br>`$$`        |
| Squared, Cubed, nth-Power        | $a^2$<br>$a^3$<br>$a^n$                                | `$a^2$`<br>`$a^3$`<br>`$a^n$`                            | `$$`<br>`a^3`<br>`$$`         |
| Square Root, Cube Root, nth-Root | $\sqrt{a}$<br>$\sqrt[3]{a}$<br>$\sqrt[n]{a}$           | `$\sqrt{a}$`<br>`$\sqrt[3]{a}$`<br>`$\sqrt[n]{a}$`       | `$$`<br>`\sqrt[3]{a}`<br>`$$` |

## Equality

| Notation                  |           Example          |           Inline          | Block                                   |
|---------------------------|:--------------------------:|:-------------------------:|-----------------------------------------|
| Equals                    |           $3=1+2$          |         `$3=1+2$`         | `$$`<br>`3=1+2`<br>`$$`                 |
| Not Equals                |         $3 \neq 4$         |         `$3\neq4$`        | `$$`<br>`3\neq4`<br>`$$`                |
| Identical / Equivalent To |        $a \equiv b$        |        `$a\equivb$`       | `$$`<br>`a\equivb`<br>`$$`              |
| Proportional To           |        $a \propto b$       |       `$a\proptob$`       | `$$`<br>`a\proptob`<br>`$$`             |
| Approximately Equal To    | $\sin(0.01) \approx 0.01$  | `$\sin(0.01)\approx0.01$` | `$$`<br>`\sin(0.01)\approx0.01`<br>`$$` |

## Comparison

| Notation                                                  |          Example         |          Inline          | Block                    |
|-----------------------------------------------------------|:------------------------:|:------------------------:|--------------------------|
| a Less Than b<br>a Greater Than b                         |    $a < b$<br>$a > b$    |    `$a<b$`<br>`$a>b$`    | `$$`<br>`a<b`<br>`$$`    |
| a Less Than or Equal To b<br>a Greater Than or Equal To b | $a \leq b$<br>$a \geq b$ | `$a\leqb$`<br>`$a\geqb$` | `$$`<br>`a\leqb`<br>`$$` |
| a Much Smaller Than b<br>a Much Larger Than b             |  $a \ll b$<br>$a \gg b$  |  `$a\llb$`<br>`$a\ggb$`  | `$$`<br>`a\llb`<br>`$$`  |

## Algebra

| Notation             |                         Example                        |                          Inline                          | Block                                                                  |
|----------------------|:------------------------------------------------------:|:--------------------------------------------------------:|------------------------------------------------------------------------|
| Factorial            |      $5 ! = 5 \times 4 \times 3 \times 2 \times 1$     |            $5!=5\times4\times3\times2\times1$            | `$$`<br>`5!=5\times4\times3\times2\times1`<br>`$$`                     |
| Absolute Value       |                     $\| -5 \| = 5$                     |                       `$\|-5\|=5$`                       | `$$`<br>`\|-5\|=5`<br>`$$`                                             |
| Function Of          |                      $f(x) = 2x^2$                     |                       `$f(x)=2x^2$`                      |                       `$$`<br>`f(x)=2x^2`<br>`$$`                      |
| Change or Difference |                 $\Delta x = x_1 - x_0$                 |                    `$\Deltax=x_1-x_0$`                   | `$$`<br>`\Deltax=x_1-x_0`<br>`$$`                                      |
| Sum                  | $\sum\limits_{k=2}^5 k^2 = 2^2 + 3^2 + 4^2 + 5^2 = 54$ | `$\sum\limits_{k=2}^5 k^2 = 2^2 + 3^2 + 4^2 + 5^2 = 54$` | `$$`<br>`\sum\limits_{k=2}^5 k^2 = 2^2 + 3^2 + 4^2 + 5^2 = 54`<br>`$$` |
|                      |                                                        |                                                          |                                                                        |
|                      |                                                        |                                                          |                                                                        |