#Reading 
# Overview
## What is the book about
- Most of the time, writing a working program is not sufficient, the program must also be time efficient to run on large datasets
- Throughout the book we will see how to estimate the running time of a program for large inputs, and more importantly **how to compare the running times of two programs without coding them**
## Maths review
### Formulas to Memorize
#### Exponents
$$
\begin{gathered}
X^aX^b = X^{a+b}\\
\frac{X^a}{X^b} = X^{a-b}\\
(X^a)^b = X^{ab}\\
X^n + X^n = 2X^n \neq X^{2n}\\
2^n + 2^n = 2^{n+1}
\end{gathered}
$$
#### Logarithms
All logs are base 2 unless otherwise specified
$$
\begin{gathered}
X^a = B \iff log_XB = A\\
\text{change of base formula}
log_AB = \frac{log_CB}{log_CA}; A,B,C \gt 0, A \neq 1\\
\end{gathered}

$$
#### Series
##### Geometric
$$
\begin{gathered}
\sum\limits^{N}_{i=0}2^i = 2^{N+1} - 1\\
\sum\limits^{N}_{i=0}A^i = \frac{2A{N+1} - 1}{A-1}\\
\text if 0 < A < 1, then
\sum\limits^{N}_{i=0}A^i = \frac{1}{A-1}\\
\text{as n tends to } \infty,\text{the sum approaches}\frac{1}{1-A}
\end{gathered}
$$
##### Arithmetic
$$
\begin{gathered}
\sum\limits_{i=1}^{N}i = \frac{N(N+1)}{2} \approx \frac{N^2}{2}\\
\sum\limits_{i=1}^{N}i^k \approx \frac{N^{k+1}}{|k+1|}; k \neq -1\\
\text{the latter formula is not valid when } k = -1\\
\text{the following formula is used much more in computer science}\\
\text{and is called the harmonic sum for harmonic numbers } H_N\\
\text{the follwoing aporximation texts to }\gamma= 0.57721566,\text{ which is known as eulers constant}\\
H_N = \sum\limits^{i=1}_{N}\frac{1}i\approx log_eN\\
\text{these two are just algebreic manipulations}\\
\sum\limits_{i=n_0}^{N}f(N)=Nf(N)\\
\sum\limits_{i=1}^{N}f(i)=\sum\limits^{i=1}{N}f(i)=\sum\limits^{n_0-1}_{i=1}f(i)\\
\end{gathered}
$$

#### Proofs

##### Proof by induction
process is as follows:
1. prove a *base case*, that is, establish that a theorem is true for some small value(s)
2. **inductive hypothesis**  