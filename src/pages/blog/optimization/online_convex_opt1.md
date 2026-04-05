---
title: "Online Convex Optimization 1: Introduction"
layout: ../../../layouts/BlogPost.astro
---

## 1. Model Formulation
Let $\mathcal{K} \subseteq \mathbb{R}^n$ be a convex set available to a user to take actions from for $T$ rounds.
1. At iteration t, a user chosses $x_t \in K$
2. A bounded convex function $f_t \in \mathcal{F}: \mathcal{K} \rightarrow \mathbb{R}$ is revealed to it, $\mathcal{F}$ is a set of bounded functions.
3. The user incurs a loss given by $f_t(x_t).$

Let $A$ be an algorithm for OCO, which maps certain game history to a decision in $\mathcal{K}$.

$$
    x_t^A = A(f_1, f_2, \cdots, f_{t-1})    \in \mathcal{K}
$$

To quantify the performance of the user, introduce a **regret function** as follows

$$
    regret_T =  \sum_{t=1}^T f_t(x_t) - \min_{x\in \mathcal{K}} \sum_{t=1}^T f_t(x)
$$

**Worst case regret** is given by:
$$
    Regret_T =  \sup_{(f_1, f_2, \cdots, f_T) \in \mathcal{F}} \left(\sum_{t=1}^T f_t(x_t) - \min_{x\in \mathcal{K}} \sum_{t=1}^T f_t(x)\right)
$$

## 2. First Order Algorithm
The goal of an OCO algorithm is to minimize the regret, rather than the **optimization error**. 
There is a relationship between the regret and optimization error but this is out of scope for now.

# 2.1 Online Gradient Descent (Algorithm)

$$
\begin{array}{l}
\bold{Algorithm: Online Convex Optimization} \\
\text{1. Input: A convex set } \mathcal{K}, T, x_1 \in \mathcal{K}, \text{step size } \eta \\
\text{2. for } t=1, 2, \cdots, T \text{ do}\\
\text{3. } \quad \text{Play action } x_t \text{ and observe cost } f_t(x_t) \\
\text{4. } \quad \text{Update and project: }\\
        \begin{aligned}
        \quad \quad \quad y_{t+1} &= x_t - \eta_t \nabla f_t(x_t) \leftarrow \text{Towards the direction of least cost.}\\
        \quad \quad \quad x_{t+1} &= \prod_{\mathcal{k}}(y_{t+1}) \leftarrow \text{Project } y_{t+1} \text{ back to } \mathcal{K}.
        \end{aligned}\\
\text{5. end for }
\end{array}
$$
Line 4 of the above algorithm, first take a step opposite to the direction of steepest ascent of the last cost function.
Such a step may take the resultant vector out of the decision set $\mathcal{K}$. Therefore, we need to project $y_{t+1}$ 
back to $\mathcal{K}$ to calculate the next action $x_{t+1}$.


Despite the fact that the next cost function $f_{t+1}$ can be very different from the cost observed thus far, the regret
attained by the algorithm is **sublinear**.

# 2.2 Analysis of online gradient descent

**Theorem 2.1** *Online gradient descent with step size* $\eta_t = \frac{D}{G \sqrt{t}},~~t \in [T]$ 
*guarantees the following for all* $T \ge 1$
$$
    Regret_T =  \sup_{(f_1, f_2, \cdots, f_T) \in \mathcal{F}} \left(\sum_{t=1}^T f_t(x_t) - \min_{x\in \mathcal{K}} \sum_{t=1}^T f_t(x)\right) \le \frac{3}{2} GD \sqrt{T}
$$
where, $G > 0$ an upper bound on the norm of the subgradients of $f$ over $\mathcal{K},$ i.e., $||\nabla f(x)|| \le G ~~ \forall G \in \mathcal{K}$
and $D$ is an upper bound on the diameter of $\mathcal{K}: i.e.,  \forall x,y \in \mathcal{K}, ||x-y|| \le D$


An interesting observation about Online Convex Optimization is that any algorithm incurs a regret bounded by $\sqrt{T}$. More formally \
**Theorem 2.2** *Any algorithm for online convex optimization incurs* $\Omega (DG \sqrt{T})$ *regret in worst case. This is even true
when the the cost functions are generated from a fixed stationary distribution*.


Readers familier with Multi-armed Bandit might be worndering about *logarithmic regret* in OCO problems. Yes, there are certain problems 
where *logarithmic regret* is achievable but this is out of scope for this article.