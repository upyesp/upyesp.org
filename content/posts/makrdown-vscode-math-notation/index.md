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

A quick reference cheat sheet, on how to write math notation in Markdown documents, as supported in native VSCode.  Note that editor VSCode supports math notation based on LaTex, by way of implementing KaTeX.  Using VSCode to write or edit Markdown documents including math notation using LaTeX, there is nothing further to install; no libraries, extensions or applications.

<!--more-->

VSCode supports $\KaTeX$ in Markdown. Layout, as with $\LaTeX$, is based on $\TeX$, created by [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth). Equations are rendered in the VSCode live preview pane, enabled with <kbd>Ctrl</kbd> + <kbd>K</kbd> <kbd>V</kbd>.

Inline math notation is wrapped in single-dollar signs. For example, `$x^2$` becomes $x^2$.

Alternatively, math notation blocks begin and end with two dollar signs. For example...

```Latex
$$
\displaystyle\sum_{k=3}^5 k^2=3^2 + 4^2 + 5^2 =50
$$
```
produces:

$$
\displaystyle\sum_{k=3}^5 k^2=3^2 + 4^2 + 5^2=50
$$

The full list of supported commands is available [here](https://katex.org/docs/supported.html).

The following tables provide a quick reference for common math notation, specifically those included in the [poster](https://www.flickr.com/photos/95869671@N08/40544016221/in/dateposted-public/) created by [Dominic Walliman](https://dominicwalliman.com/).  See the associated YouTube, [The Map of Mathematics](https://youtu.be/OmJ-4B-mS-Y).

## Arithmetic

| Notation                         |                         Example                        |                          Inline                          | Block                         |
|----------------------------------|:------------------------------------------------------:|:--------------------------------------------------------:|-------------------------------|
| Addition                         |                          $a+b$                         |                          `$a+b$`                         | `$$`<br>`a+b`<br>`$$`         |
| Subtraction                      |                          $a-b$                         |                          `$a-b$`                         | `$$`<br>`a-b`<br>`$$`         |
| Various Forms of Multiplication  |        $a \times b$<br>$a \ast b$<br>$a \cdot b$       |         `$a \times b$`<br>`$a \ast b$`<br>`$a \cdot b$`        | `$$`<br>`a \cdot b`<br>`$$`     |
| Various Forms of Division        | $a \colon b$<br>$a / b$<br>$a \div b$<br>$\frac{a}{b}$ | `$a \colon b$`<br>`$a / b$`<br>`$a \div b$`<br>`$\frac{a}{b}$` | `$$`<br>`a \div b`<br>`$$`      |
| Remainder / Modulo               |                     $5 \mod 2 = 1$                     |                       `$5\mod 2=1$`                       | `$$`<br>`5\mod 2=1`<br>`$$`    |
| Negative Value                   |                          $-a$                          |                          `$-a$`                          | `$$`<br>`-a`<br>`$$`          |
| Plus or Minus, Minus or Plus     |                   $\pm a$<br>$\mp a$                   |                   `$\pm a$`<br>`$\mp a$`                   | `$$`<br>`\pm a`<br>`$$`        |
| Squared, Cubed, nth-Power        | $a^2$<br>$a^3$<br>$a^n$                                | `$a^2$`<br>`$a^3$`<br>`$a^n$`                            | `$$`<br>`a^3`<br>`$$`         |
| Square Root, Cube Root, nth-Root | $\sqrt{a}$<br>$\sqrt[3]{a}$<br>$\sqrt[n]{a}$           | `$\sqrt{a}$`<br>`$\sqrt[3]{a}$`<br>`$\sqrt[n]{a}$`       | `$$`<br>`\sqrt[3]{a}`<br>`$$` |

## Equality

| Notation                  |           Example          |           Inline          | Block                                   |
|---------------------------|:--------------------------:|:-------------------------:|-----------------------------------------|
| Equals                    |           $3=1+2$          |         `$3=1+2$`         | `$$`<br>`3=1+2`<br>`$$`                 |
| Not Equals                |         $3 \neq 4$         |         `$3\neq4$`        | `$$`<br>`3\neq4`<br>`$$`                |
| Identical / Equivalent To |        $a \equiv b$        |        `$a \equiv b$`       | `$$`<br>`a \equiv b`<br>`$$`              |
| Proportional To           |        $a \propto b$       |       `$a \propto b$`       | `$$`<br>`a \propto b`<br>`$$`             |
| Approximately Equal To    | $\sin(0.01) \approx 0.01$  | `$\sin(0.01) \approx 0.01$` | `$$`<br>`\sin(0.01) \approx 0.01`<br>`$$` |

## Comparison

| Notation                                                  |          Example         |          Inline          | Block                    |
|-----------------------------------------------------------|:------------------------:|:------------------------:|--------------------------|
| a Less Than b<br>a Greater Than b                         |    $a < b$<br>$a > b$    |    `$a<b$`<br>`$a>b$`    | `$$`<br>`a<b`<br>`$$`    |
| a Less Than or Equal To b<br>a Greater Than or Equal To b | $a \leq b$<br>$a \geq b$ | `$a \leq b$`<br>`$a \geq b$` | `$$`<br>`a \leq b`<br>`$$` |
| a Much Smaller Than b<br>a Much Larger Than b             |  $a \ll b$<br>$a \gg b$  |  `$a \ll b$`<br>`$a \gg b$`  | `$$`<br>`a \ll b`<br>`$$`  |

## Algebra

| Notation               |                               Example                              |                                Inline                                | Block                                                              |
|------------------------|:------------------------------------------------------------------:|:--------------------------------------------------------------------:|--------------------------------------------------------------------|
| Factorial              |            $5 ! = 5 \times 4 \times 3 \times 2 \times 1$           |                  `$5!=5 \times 4 \times 3 \times 2 \times 1$`                  | `$$`<br>`5!=5 \times 4 \times 3 \times 2 \times 1`<br>`$$`                 |
| Absolute Value         |                           $\| -5 \| = 5$                           |                             `$\|-5\|=5$`                             | `$$`<br>`\|-5\|=5`<br>`$$`                                         |
| Function Of            |                            $f(x) = 2x^2$                           |                             `$f(x)=2x^2$`                            | `$$`<br>`f(x)=2x^2`<br>`$$`                                        |
| Change or Difference   |                       $\Delta x = x_1 - x_0$                       |                          `$\Delta x  = x_1 - x_0$`                         | `$$`<br>`\Delta x = x_1 - x_0`<br>`$$`                                  |
| Pi                     |                         $\pi = 3.14159...$                         |                          `$\pi = 3.14159...$`                          | `$$`<br>`\pi`<br>`$$`                                              |
| Euler's Constant       |                          $e = 2.71828...$                          |                           `$e = 2.71828...$`                           | `$$`<br>`e = 2.71828...`<br>`$$`                                   |
| Sum                    |       $\displaystyle\sum_{k=3}^5 k^2 = 3^2 + 4^2 + 5^2 = 50$       |         `$\displaystyle\sum_{k=3}^5 k^2=3^2 + 4^2 + 5^2 =50$`         | `$$`<br>`\displaystyle\sum_{k=3}^5 k^2=3^2 + 4^2 + 5^2 =50`<br>`$$` |
| Series Product         | $\displaystyle\prod_{x=2}^4 x^2 = 2^2 \times 3^2 \times 4^2 = 576$ | `$\displaystyle\prod_{x=2}^4 x^2 = 2^2 \times 3^2 \times 4^2 = 576$` | `$$`<br>`\displaystyle\sum_{k=2}^4 k^2=2^2 \times 3^2 \times 4^2 = 576`<br>`$$`     |
| Brackets & Parentheses |                         $[\ldots]$    $(\ldots)$                         |                           `$[\ldots]   (\ldots)$`                          | `$$`<br>`[\ldots]   (\ldots)`<br>`$$`                                    |

## Angles

| Notation                 |         Example         |           Inline          | Block                                   |
|--------------------------|:-----------------------:|:-------------------------:|-----------------------------------------|
| Angle                    |         $\angle$        |         `$\angle$`        | `$$`<br>`\angle`<br>`$$`                |
| Degree, Arc Min, Arc Sec |    $30\degree45\rq30\rq\rq$   |    `$30\degree45\rq30\rq\rq$`   | `$$`<br>`30\degree45\rq30\rq\rq`<br>`$$`      |
| Radians                  | $360\degree = 2\pi rad$ | `$360\degree = 2\pi rad$` | `$$`<br>`360\degree = 2\pi rad`<br>`$$` |

## Probability & Statistics

| Notation                       |                  Example                 |                   Inline                   | Block                                                    |
|--------------------------------|:----------------------------------------:|:------------------------------------------:|----------------------------------------------------------|
| Probability of Event A         |            $P(A)$ or $\Pr(A)$            |            `$P(A)$ or $\Pr(A)$`            | `$$`<br>`P(A)`<br>`$$`                                   |
| Intersection Prob. of A & B    |               $P(A \cap B)$              |                `$P(A \cap B)$`               | `$$`<br>`P(A \ca pB)`<br>`$$`                              |
| Union Prob. of A or B          |               $P(A \cup B)$              |                `$P(A \cup B)$`               | `$$`<br>`P(A \cup B)`<br>`$$`                              |
| Conditional Prob. of A Given B |                $P(A \| B)$               |                 `$P(A\|B)$`                | `$$`<br>`P(A\|B)`<br>`$$`                                |
| Median                         |                $\tilde{x}$               |                `$\tilde{x}$`               | `$$`<br>`\tilde{x}`<br>`$$`                              |
| Population Mean                | $\mu , \overline{x} , \langle x \rangle$ | `$\mu , \overline{x} , \langle x \rangle$` | `$$`<br>`\mu , \overline{x} , \langle x \rangle`<br>`$$` |
| Standard Deviation             |                 $\sigma$                 |                 `$\sigma$`                 | `$$`<br>`\sigma`<br>`$$`                                 |
| Varience                       |                $\sigma^2$                |                `$\sigma^2$`                | `$$`<br>`\sigma^2`<br>`$$`                               |

## Linear Algebra

### Linear Algebra: Vectors

| Notation      |                               Example                              |                                Inline                               | Block                                                                                            |
|---------------|:------------------------------------------------------------------:|:-------------------------------------------------------------------:|--------------------------------------------------------------------------------------------------|
| Vectors       |                  $\mathbf{v} \overline{v} \vec{v}$                 |                  `$\mathbf{v}\overline{v}\vec{v}$`                  | `$$`<br>`\mathbf{v} \overline{v} \vec{v}`<br>`$$`                                                |
| Row Vector    |            $v = \begin{pmatrix} 1 & 2 & 3 \end{pmatrix}$           |               `$v=\begin{pmatrix}1&2&3\end{pmatrix}$`               | `$$`<br>`v = \begin{pmatrix}`<br>`   1 & 2 & 3`<br>`\end{pmatrix}`<br>`$$`                       |
| Column Vector |        $w = \begin{pmatrix} 4 \cr 5 \cr 6 \cr \end{pmatrix}$       |            `$w=\begin{pmatrix}4\cr5\cr6\cr\end{pmatrix}$`           | `$$`<br>`w=\begin{pmatrix}`<br>`   4 \cr`<br>`   5 \cr`<br>`   6 \cr`<br>`\end{pmatrix}`<br>`$$` |
| Dot Product   | $\mathbf{v} \cdot \mathbf{w}$<br>$(v,w)$<br>$\left< v\|w \right>$ | `$\mathbf{v} \cdot \mathbf{w}$<br>$(v,w)$<br>$\left<v \| w\right>$` | `$$`<br>`\mathbf{v}\cdot\mathbf{w}`<br>`(v,w)`<br>`\left<v\|w \right>`<br>`$$`                    |
| Cross Product |                            $v \times w$                            |                             `$v \times w$`                            | `$$`<br>`v \times w`<br>`$$`                                                                       |
| Length of v   |                               $\|v\|$                              |                              `$\|v\|$`                              | `$$`<br>`\|v\|`<br>`$$`                                                                          |
| Norm of v     |                             $\|\|v\|\|$                            |                            `$\|\|v\|\|$`                            | `$$`<br>`\|\|v\|\|`<br>`$$`                                                                      |

### Linear Algebra: Matrices

| Notation                                   |                          Example                          |                      Inline                     | Block                                                                                          |
|--------------------------------------------|:---------------------------------------------------------:|:-----------------------------------------------:|------------------------------------------------------------------------------------------------|
| Matrix, 2 By 3                             | $A=\begin{bmatrix} 1 & 2 & 3 \cr 4 & 5 & 6 \end{bmatrix}$ | `$A=\begin{bmatrix}1&2&3\cr4&5&6\end{bmatrix}$` | `$$`<br>`A=`<br>`\begin{bmatrix}`<br>`1 & 2 & 3 \cr`<br>`4 & 5 & 6`<br>`\end{bmatrix}`<br>`$$` |
| Product                                    |                        $A \cdot B$                        |                  `$A \cdot B$`                  | `$$`<br>`A \cdot B`<br>`$$`                                                                    |
| Hadamard Product                           |                        $A \circ B$                        |                  `$A \circ B$`                  | `$$`<br>`A \circ B`<br>`$$`                                                                    |
| Kronecker Product                          |                       $A \otimes B$                       |                 `$A \otimes B$`                 | `$$`<br>`A \otimes B`<br>`$$`                                                                  |
| Transposed Matrix                          |                           $A^T$                           |                     `$A^T$`                     | `$$`<br>`A^T`<br>`$$`                                                                          |
| Hermitian Matrix or<br>Conjugate Transpose |                    $A^\dag$<br>$A^\ast$                   |             `$A^\dag$`<br>`$A^\ast$`            | `$$`<br>`A^\dag`<br>`A^\ast`<br>`$$`                                                           |
| Inverse Matrix                             |                          $A^{-1}$                         |                    `$A^{-1}$`                   | `$$`<br>`A^{-1}`<br>`$$`                                                                       |
| Determinant                                |                          $\|A\|$                          |                    `$\|A\|$`                    | `$$`<br>`\|A\|`<br>`$$`                                                                        |
| Norm                                       |                        $\|\|A\|\|$                        |                  `$\|\|A\|\|$`                  | `$$`<br>`\|\|A\|\|`<br>`$$`                                                                    |


## Calculus

| Notation                                                   |             Example             |               Inline              | Block                                           |
|------------------------------------------------------------|:-------------------------------:|:---------------------------------:|-------------------------------------------------|
| Example Function:<br>$y = \frac{x^2}{4}$ |       $y = \frac{x^2}{4}$       |       `$y = \frac{x^2}{4}$`       | `$$`<br>`y = \frac{x^2}{4}`<br>`$$`             |
| Integration <br>(Limits: 1 to 4)   | $A = \int_1^4 \frac{x^2}{x} dx$ | `$A = \int_1^4 \frac{x^2}{x} dx$` | `$$`<br>`A = \int_1^4 \frac{x^2}{x} dx`<br>`$$` |
| Differentiation                                            |                                 |                                   |                                                 |
| First Derivative<br>With Respect To $x$                    |         $\frac{df}{dx}$         |         `$\frac{df}{dx}$`         | `$$`<br>`\frac{df}{dx}`<br>`$$`                 |
| Partial Derivative<br>With Respect To $x$                  | $\frac{\partial f}{\partial x}$ | `$\frac{\partial f}{\partial x}$` | `$$`<br>`\frac{\partial f}{\partial x}`<br>`$$` |
| First and Second Derivative<br>of Function                 |          $f'$<br>$f''$          |         `$f'$`<br>`$f''$`         | `$$`<br>`f'`<br>`f''`<br>`$$`                   |
| First and Second Derivative<br>With Respect To Time        |      $\dot f$<br>$\ddot f$      |     `$\dot f$`<br>`$\ddot f$`     | `$$`<br>`\dot f`<br>`\ddot f`<br>`$$`           |