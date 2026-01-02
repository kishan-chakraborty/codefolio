---
title: "Temporal Difference (TD) Learning"
layout: ../../../layouts/BlogPost.astro
---

The concept of TD learning was introduced by Richard Sutton in the year 1988. 
It was introduced as a class of incremental learning procedures for *prediction problems*.
Conventional prediction problems are driven by minimizing the difference between prediction <br>
and original value, TD learning is driven by difference between *temporarily successive predictions.<br>
**For example**, in a task of predicting the probability of rain on saturday an agent can have two approach. 
One, on Monday it can predict the probability only for saturday or it can predict the probability of each
successive day starting from Tuesday.<br>
- can update it's probability only after the observation on saturday.
- It can observe the weather of the next day and update it's prediction (TD learning).
  
It estimates it's value based on another estimate, this is called **Bootstrapping**. 
Sutton advocates to view TD learning as a method for efficiently learning
arbitrary events, not only the goal-related ones.

## Temporal-difference and supervised-learning approaches to prediction
A prediction problem can be formulated as a supervised learning paradigm by taking the first part of the data as
input and the second part as label. In the above problem, the measurement on monday can be used to predict the
weather of staurday, and repeat for tuesday and so on. This ignores the sequential nature of the problem 

**Single-step and Multi-step prediction** <br>
In *single step* prediction, correctness of each prediction is revealed at the next step (predicting tuesday's weather
on monday). In *multi-step* prediction, the actual outcome is not revealed at the immidiate step but partial information
is available at each step (Use weather observation on tuesday to update the actual prediction). In single step problem 
there is no distinction between supervised and TD learning.

**Supervised updates are equivalent to TD**<br>
Consider the sequence of observation sequence $\{x_t\}_1^m$ and $z$ is the outcome of the sequence. For each observations
let $P_t$ be the predictions. Assume that $P_t$ depends only on $x_t$. It can depend on previous observations in which 
case the formulation can be modified accordingly. The predictions are calculated using a modifiable parameter $w$.
Learning in this process corresponds to updating weights to make bettern prediction, $P(x_t, w)$.

Weights are updated only after the full observation not intermediate sequence. For each observation an increment 
$\Delta w_t$ calculated after the full sequence. 
$$
w \leftarrow w + \sum_{t=1}^m \Delta w_t
$$

In supervised approach, the data is represented as ${(x_t, z)}_1^m$ and after the *full sequence* the update is given by
$$
\Delta w_t = \alpha (z-P_t)\nabla_w P_t
$$
If $P(x_t, w) = w^Tx_t$ *(linear)* then we have Widrow-Hoff rule
$$
\Delta w_t = \alpha (z- w^Tx_t)x_t
$$

The same result can also be obtained using incremental TD learning. <br> 
Using $z-P_t = \sum_{k=t}^m(P_{k+1} - P_k), P_{m+1} = z$, we have 
$$
\Delta = \alpha  (P_{t+1} - P_t) \sum_{k=1}^t \nabla_w P_k
$$
This equation can be computed incrementally.