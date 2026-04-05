---
title: "Online Convex Optimization 2: Regularization"
layout: ../../../layouts/BlogPost.astro
---
The goal of an OCO algorithm is to minimize the regret unlike traditional convex optimization problems.
This motivates a family of algorithm called *Regularized Follow the Leader*. This is based on a simple idea 
of taking the optimal decision *on the hindsight*. Formally, 

$$
    x_{t+1} = \argmin_{x\in \mathcal{K}} \sum_{\tau=1}^t f_{\tau}(x)
$$

This is called *Follow the Leader* strategy in Machine Learning. This strategy fails miserably in worst case scenario.
Consider the formulation $\mathcal{K} = [-1, 1], \text{Let}, f_1(x) = \frac{1}{2} x, f_2(x) = -\frac{1}{2} x$ and 
Let $f_{\tau}$ for $\tau=2, \cdots, T$ alternate between $-x$ and $x$. Thus, 

$$
\sum_{\tau=1}^t f_{\tau}(x) = \begin{cases} \frac{1}{2}x, ~~~~~ t \text{ is odd} \\ -\frac{1}{2}x, ~~ \text{otherwise} \end{cases}
$$
The FTL strategy keeps shifting between $x_t=1$ and $x_t=-1$, always making the wrong choice. The algorithm can be modified to make
it more stable. Such means of stablization is called *regularization*.

## 1. Regularization Functions
*Def 1:* *A function* $f$ *is called* $\alpha$- *strongly convex if*

$$
    f(y) \ge f(x) + \nabla f(x)^T(y-x) + \frac{\alpha}{2}||y-x||^2
$$

*Def 2:* *A function* $f$ *is called* $\beta$- *smooth if*

$$
    f(y) \le f(x) + \nabla f(x)^T(y-x) + \frac{\beta}{2}||y-x||^2
$$

Regularization functions $\mathcal{R}: \mathcal{K} \rightarrow \mathbb{R}$, are *strongly convex* and *smooth*. 