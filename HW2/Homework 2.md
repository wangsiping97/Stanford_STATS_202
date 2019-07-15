# Homework 2

<center>
  Siping Wang 006405652
</center>

## Problem 1

If we know that
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}
$$
then,
$$
1-p(X) = 1- \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}} = \frac{1}{1+e^{\beta_0+\beta_1\textbf{x}}}
$$
So
$$
\frac{p(X)}{1-p(X)} = e^{\beta_0+\beta_1\textbf{x}}.
$$


Similarly, if we know that
$$
\frac{p(X)}{1-p(X)} = e^{\beta_0+\beta_1\textbf{x}},
$$
we can solve that
$$
p(X) =e^{\beta_0+\beta_1\textbf{x}} \times (1-p(X))
$$
then
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}.
$$

## Problem 2

**(a)**

We can conclude from the question that:

- If $x \isin [0.05, 0.95]$, then the observations we will use are in the interval $[x-0.05, x-0.95]$. 
- If $x\isin [0, 0.05)$, then the observations we will use are in the interval $[0, x+0.05]$. 
- If $x \isin (0.95, 1]$, then the observations we will use are in the interval $[x-0.05, 1]$. 

So the average fraction is, 
$$
\int\limits_{0.05}^{0.95}10dx+\int\limits_{0}^{0.05}(100x+5)dx+\int\limits_{0.95}^{1} (105-100x)dx = 9.75.
$$
**(b)**

The fraction of the available observations will we use is
$$
9.75\% \times 9.75\% = 0.950625\%.
$$
**(c)**

We will use $(9.75\%)^{100} \approx 0$ of the observations to make the prediction. 

**(d)**

The fraction of observations available with $p$ features or parameters is $(9.75\%)^{p}$.

So when $p$ is very large, the fraction will be
$$
\lim_{p\to\infty}(9.75\%)^p = 0.
$$
**(e)**

- Given $p=1$, we have $l=0.1$. 
- Given $p=2$, we have $l= (0.1)^{\frac{1}{2}}$. 
- Given $p=100$, we have $l=(0.1)^{\frac{1}{100}}$.

Comment: 

When the number of features is high, to use on average 10% of the training observations would mean that we would need to include almost the entire range of each individual feature.

## Problem 3

**(a)**
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}=\frac{e^{-6+0.05\times 40+1\times3.5}}{1+e^{-6+0.05\times 40+1\times3.5}} = 0.3775.
$$
**(b)**

Let $x_1$ denotes the amount of hours the student would need to study.

Then we have
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}=\frac{e^{-6+0.05\times x_1+1\times3.5}}{1+e^{-6+0.05\times x_1+1\times3.5}} =0.5,
$$
which is equivalent to 
$$
e^{-6+0.05\times x_1+1\times3.5} = 1.
$$
Solving the equation above, we can get that $x_1 = 50$. 

## Problem 4

## Problem 5

## Problem 6

## Problem 7

## Problem 8

## Problem 9

## Problem 10

