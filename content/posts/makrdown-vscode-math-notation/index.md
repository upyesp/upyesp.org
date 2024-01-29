---
title: "Cheat Sheet: Math Notation In Markdown"
description: Examples of math notation, inline & code blocks.
date: 2022-09-12T10:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [Markdown, VSCode, KaTeX]
categories: [Documentation, Windows, Mac, Linux]
series: [Markdown]
---

A quick-reference guide, how to add math notation in Markdown documents.

<!--more-->

The scope of mathematical notation included in this cheat sheet is drawn from the [Math Notation Cheat Sheet](https://www.flickr.com/photos/95869671@N08/40544016221/in/dateposted-public/) poster, created by [Dominic Walliman](https://dominicwalliman.com/), included below with permission.  The associated YouTube video, which is excellent, is [The Map of Mathematics](https://youtu.be/OmJ-4B-mS-Y).

![Math Notation Cheat Sheet, © Dominic Walliman, 2018](/images/Map_of_Mathematics.jpg)

## Adding Math Notation To Markdown Documents

LaTeX is sometimes stylised as $\LaTeX$.  Typesetting is based on $\TeX$, created by [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth).

Open source editor, VSCode, supports math typesetting with $\LaTeX$, showing the notation as you type.  The Live Preview Pane is enabled with <kbd>Ctrl</kbd> + <kbd>K</kbd> <kbd>V</kbd>.  No other libraries, extensions or apps need to be installed.  Rendering in Live Preview is performed by [KaTeX](https://katex.org/), a fast, easy-to-use JavaScript library for $\TeX$ math rendering on the web.

## Including LaTeX in Markdown

There are two ways to include $\LaTeX$ math typesetting in Markdown.  The first is `inline`, which means that the notation is included in the paragraph or sentence, with the flow of text.

The second method is as separate `code blocks`, so that the notation is shown in it's own paragraph.

Inline LaTeX math notation is wrapped in single-dollar signs. For example, for `the square of "x"`, just type `$x^2$`, which is then formatted as $x^2$.

Alternatively, `code blocks` of LaTeX begin and end with two dollar signs, wrapped inside triple backticks. For example...

~~~Latex
```
$$
\displaystyle\sum_{k=3}^5 k^2=3^2 + 4^2 + 5^2 =50
$$
```
~~~

The above is rendered as:

$$
\displaystyle\sum_{k=3}^5 k^2=3^2 + 4^2 + 5^2=50 
$$

## Cheat Sheet

> Tip: These tables are wide, so you may need to scroll horizontally to see all the columns, or rotate your phone to landscape.

### Arithmetic

| Notation                         |                         Example                        |                          Inline                          | Code Block                    |
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

### Equality

| Notation                  |           Example          |           Inline          | Code Block                              |
|---------------------------|:--------------------------:|:-------------------------:|-----------------------------------------|
| Equals                    |           $3=1+2$          |         `$3=1+2$`         | `$$`<br>`3=1+2`<br>`$$`                 |
| Not Equals                |         $3 \neq 4$         |         `$3\neq4$`        | `$$`<br>`3\neq4`<br>`$$`                |
| Identical / Equivalent To |        $a \equiv b$        |        `$a \equiv b$`       | `$$`<br>`a \equiv b`<br>`$$`              |
| Proportional To           |        $a \propto b$       |       `$a \propto b$`       | `$$`<br>`a \propto b`<br>`$$`             |
| Approximately Equal To    | $\sin(0.01) \approx 0.01$  | `$\sin(0.01) \approx 0.01$` | `$$`<br>`\sin(0.01) \approx 0.01`<br>`$$` |

### Comparison

| Notation                                                  |          Example         |          Inline          | Code Block               |
|-----------------------------------------------------------|:------------------------:|:------------------------:|--------------------------|
| a Less Than b<br>a Greater Than b                         |    $a < b$<br>$a > b$    |    `$a<b$`<br>`$a>b$`    | `$$`<br>`a<b`<br>`$$`    |
| a Less Than or Equal To b<br>a Greater Than or Equal To b | $a \leq b$<br>$a \geq b$ | `$a \leq b$`<br>`$a \geq b$` | `$$`<br>`a \leq b`<br>`$$` |
| a Much Smaller Than b<br>a Much Larger Than b             |  $a \ll b$<br>$a \gg b$  |  `$a \ll b$`<br>`$a \gg b$`  | `$$`<br>`a \ll b`<br>`$$`  |

### Algebra

| Notation               |                               Example                              |                                Inline                                | Code Block                                                         |
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

### Angles

| Notation                 |         Example         |           Inline          | Code Block                              |
|--------------------------|:-----------------------:|:-------------------------:|-----------------------------------------|
| Angle                    |         $\angle$        |         `$\angle$`        | `$$`<br>`\angle`<br>`$$`                |
| Degree, Arc Min, Arc Sec |    $30\degree45\rq30\rq\rq$   |    `$30\degree45\rq30\rq\rq$`   | `$$`<br>`30\degree45\rq30\rq\rq`<br>`$$`      |
| Radians                  | $360\degree = 2\pi rad$ | `$360\degree = 2\pi rad$` | `$$`<br>`360\degree = 2\pi rad`<br>`$$` |

### Probability & Statistics

| Notation                       |                  Example                 |                   Inline                   | Code Block                                               |
|--------------------------------|:----------------------------------------:|:------------------------------------------:|----------------------------------------------------------|
| Probability of Event A         |            $P(A)$ or $\Pr(A)$            |            `$P(A)$ or $\Pr(A)$`            | `$$`<br>`P(A)`<br>`$$`                                   |
| Intersection Prob. of A & B    |               $P(A \cap B)$              |                `$P(A \cap B)$`               | `$$`<br>`P(A \ca pB)`<br>`$$`                              |
| Union Prob. of A or B          |               $P(A \cup B)$              |                `$P(A \cup B)$`               | `$$`<br>`P(A \cup B)`<br>`$$`                              |
| Conditional Prob. of A Given B |                $P(A \| B)$               |                 `$P(A\|B)$`                | `$$`<br>`P(A\|B)`<br>`$$`                                |
| Median                         |                $\tilde{x}$               |                `$\tilde{x}$`               | `$$`<br>`\tilde{x}`<br>`$$`                              |
| Population Mean                | $\mu , \overline{x} , \langle x \rangle$ | `$\mu , \overline{x} , \langle x \rangle$` | `$$`<br>`\mu , \overline{x} , \langle x \rangle`<br>`$$` |
| Standard Deviation             |                 $\sigma$                 |                 `$\sigma$`                 | `$$`<br>`\sigma`<br>`$$`                                 |
| Varience                       |                $\sigma^2$                |                `$\sigma^2$`                | `$$`<br>`\sigma^2`<br>`$$`                               |

### Linear Algebra

#### Linear Algebra: Vectors

| Notation      |                               Example                              |                                Inline                               | Code Block                                                                                       |
|---------------|:------------------------------------------------------------------:|:-------------------------------------------------------------------:|--------------------------------------------------------------------------------------------------|
| Vectors       |                  $\mathbf{v} \overline{v} \vec{v}$                 |                  `$\mathbf{v}\overline{v}\vec{v}$`                  | `$$`<br>`\mathbf{v} \overline{v} \vec{v}`<br>`$$`                                                |
| Row Vector    |            $v = \begin{pmatrix} 1 & 2 & 3 \end{pmatrix}$           |               `$v=\begin{pmatrix}1&2&3\end{pmatrix}$`               | `$$`<br>`v = \begin{pmatrix}`<br>`   1 & 2 & 3`<br>`\end{pmatrix}`<br>`$$`                       |
| Column Vector |        $w = \begin{pmatrix} 4 \cr 5 \cr 6 \cr \end{pmatrix}$       |            `$w=\begin{pmatrix}4\cr5\cr6\cr\end{pmatrix}$`           | `$$`<br>`w=\begin{pmatrix}`<br>`   4 \cr`<br>`   5 \cr`<br>`   6 \cr`<br>`\end{pmatrix}`<br>`$$` |
| Dot Product   | $\mathbf{v} \cdot \mathbf{w}$<br>$(v,w)$<br>$\left< v\|w \right>$ | `$\mathbf{v} \cdot \mathbf{w}$<br>$(v,w)$<br>$\left<v \| w\right>$` | `$$`<br>`\mathbf{v}\cdot\mathbf{w}`<br>`(v,w)`<br>`\left<v\|w \right>`<br>`$$`                    |
| Cross Product |                            $v \times w$                            |                             `$v \times w$`                            | `$$`<br>`v \times w`<br>`$$`                                                                       |
| Length of v   |                               $\|v\|$                              |                              `$\|v\|$`                              | `$$`<br>`\|v\|`<br>`$$`                                                                          |
| Norm of v     |                             $\|\|v\|\|$                            |                            `$\|\|v\|\|$`                            | `$$`<br>`\|\|v\|\|`<br>`$$`                                                                      |

#### Linear Algebra: Matrices

| Notation                                   |                          Example                          |                      Inline                     | Code Block                                                                                     |
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


### Calculus

| Notation                                                   |             Example             |               Inline              | Code Block                                      |
|------------------------------------------------------------|:-------------------------------:|:---------------------------------:|-------------------------------------------------|
| Example Function:<br>$y = \frac{x^2}{4}$ |       $y = \frac{x^2}{4}$       |       `$y = \frac{x^2}{4}$`       | `$$`<br>`y = \frac{x^2}{4}`<br>`$$`             |
| Integration <br>(Limits: 1 to 4)   | $A = \int_1^4 \frac{x^2}{x} dx$ | `$A = \int_1^4 \frac{x^2}{x} dx$` | `$$`<br>`A = \int_1^4 \frac{x^2}{x} dx`<br>`$$` |
| Differentiation                                            |                                 |                                   |                                                 |
| First Derivative<br>With Respect To $x$                    |         $\frac{df}{dx}$         |         `$\frac{df}{dx}$`         | `$$`<br>`\frac{df}{dx}`<br>`$$`                 |
| Partial Derivative<br>With Respect To $x$                  | $\frac{\partial f}{\partial x}$ | `$\frac{\partial f}{\partial x}$` | `$$`<br>`\frac{\partial f}{\partial x}`<br>`$$` |
| First and Second Derivative<br>of Function                 |          $f\rq$<br>$f\rq\rq$          |         `$f\rq$`<br>`$f\rq\rq$`         | `$$`<br>`f\rq`<br>`f\rq\rq`<br>`$$`                   |
| First and Second Derivative<br>With Respect To Time        |      $\dot f$<br>$\ddot f$      |     `$\dot f$`<br>`$\ddot f$`     | `$$`<br>`\dot f`<br>`\ddot f`<br>`$$`           |

### Complex Numbers

| Notation                         |                 Example                |                   Inline                   | Block                                                  |
|----------------------------------|:--------------------------------------:|:------------------------------------------:|--------------------------------------------------------|
| Imaginary Unit $i$               |                $z=3+2i$                |                 `$z=3+2i$`                 | `$$`<br>`z=3+2i`<br>`$$`                               |
| Real Part Of Complex Number      | $\Re(z)=3$<br>$\operatorname{Re}(z)=3$ | `$\Re(z)=3$`<br>`$\operatorname{Re}(z)=3$` | `$$`<br>`\Re(z)=3`<br>`\operatorname{Re}(z)=3`<br>`$$` |
| Imaginary Part Of Complex Number | $\Im(z)=2$<br>$\operatorname{Im}(z)=2$ | `$\Im(z)=2$`<br>`$\operatorname{Im}(z)=2$` | `$$`<br>`\Im(z)=2`<br>`\operatorname{Im}(z)=2`<br>`$$` |
| Complex Conjugate                |             $\bar{z}=z^*=3-2i$             |              `$\bar{z}=z^*=3-2i$`              | `$$`<br>`\bar{z}=z^*=3-2i`<br>`$$`                         |

### Greek Alphabet

| Letter  | Lower      | Inline       | Upper      | Inline       |
|---------|------------|--------------|------------|--------------|
| Alpha   | $\alpha$   | `$\alpha$`   | $\Alpha$   | `$\Alpha$`   |
| Beta    | $\beta$    | `$\beta$`    | $\Beta$    | `$\Beta$`    |
| Gamma   | $\gamma$   | `$\gamma$`   | $\Gamma$   | `$\Gamma$`   |
| Delta   | $\delta$   | `$\delta$`   | $\Delta$   | `$\Delta$`   |
| Epsilon | $\epsilon$ | `$\epsilon$` | $\Epsilon$ | `$\Epsilon$` |
| Zeta    | $\zeta$    | `$\zeta$`    | $\Zeta$    | `$\Zeta$`    |
| Eta     | $\eta$     | `$\eta$`     | $\Eta$     | `$\Eta$`     |
| Theta   | $\theta$   | `$\theta$`   | $\Theta$   | `$\Theta$`   |
| Iota    | $\iota$    | `$\iota$`    | $\Iota$    | `$\Iota$`    |
| Kappa   | $\kappa$   | `$\kappa$`   | $\Kappa$   | `$\Kappa$`   |
| Lambda  | $\lambda$  | `$\lambda$`  | $\Lambda$  | `$\Lambda$`  |
| Mu      | $\mu$      | `$\mu$`      | $\Mu$      | `$\Mu$`      |
| Nu      | $\nu$      | `$\nu$`      | $\Nu$      | `$\Nu$`      |
| Xi      | $\xi$      | `$\xi$`      | $\Xi$      | `$\Xi$`      |
| Omicron | $\omicron$ | `$\omicron$` | $\Omicron$ | `$\Omicron$` |
| Pi      | $\pi$      | `$\pi$`      | $\Pi$      | `$\Pi$`      |
| Rho     | $\rho$     | `$\rho$`     | $\Rho$     | `$\Rho$`     |
| Sigma   | $\sigma$   | `$\sigma$`   | $\Sigma$   | `$\Sigma$`   |
| Tau     | $\tau$     | `$\tau$`     | $\Tau$     | `$\Tau$`     |
| Upsilon | $\upsilon$ | `$\upsilon$` | $\Upsilon$ | `$\Upsilon$` |
| Phi     | $\phi$     | `$\phi$`     | $\Phi$     | `$\Phi$`     |
| Chi     | $\chi$     | `$\chi$`     | $\Chi$     | `$\Chi$`     |
| Psi     | $\psi$     | `$\psi$`     | $\Psi$     | `$\Psi$`     |
| Omega   | $\omega$   | `$\omega$`   | $\Omega$   | `$\Omega$`   |