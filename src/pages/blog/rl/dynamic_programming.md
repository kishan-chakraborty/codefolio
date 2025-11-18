---
title: "Understanding Value and Policy Iteration"
layout: ../../../layouts/BlogPost.astro
order: 2
---

In this blog (and the following ones) we will try to answer some fundamental questions common to almost all RL algorithms.
1. What does the agent see and do in the environment?
2. What is the objective of the algorithm?
3. How does the agent explore and experience the environment? Extrinsic Vs Intrinsic?
4. How does the agent use the learnt experience to achieve it's objective?
5. How does the agent learn new things without forgetting what already works?

Value and Policy iteration are very simple algortihms used when the environemnt is fully known. 
At each time step an agent know the state it is in as well as the probability of the next state
for a particular action.<br>
The objective of these algorithm is to find a policy $\pi$ with the largest value function for each state $s_t$.
These algorithms does it iteratively. Value iteration algorithm start with random values for each state and
updates it based on the observed reward.<br>
$$
V_{\pi}(s) = \max_{a} \bigg(r(s, a) + \gamma \sum_{s'} P(s'|s, \pi(s))V_{\pi}(s')\bigg)
$$
In the above equation the observed reward is the only true signal which is used to update the arbitrarily initialized
value functions.<br>
Policy Iteration is a two step process, policy evaluation and policy improvement.
- **Policy Evaluation**: Evaluate the existing policy.
    $$
    V_{(k)}(s) = r(s, \pi(s)) + \gamma \sum_{s'} P(s'|s, \pi(s)) V_{k}(s')
    $$
- **Policy Improvement**: Use the evaluated value functions to update the policy.
    $$
    \pi(s) = \argmax_{a \in A} \bigg(r(s, a) + \gamma \sum_{s'}p(s'|s,a)V_{k}(s')\bigg)
    $$

For a infinite horizon discounted cost ($\gamma < 1$) MDP both the algorithms are **guaranteed to converge** to optimal value function. 
Value and policy iteration also converges for $\gamma = 1$ if the **rewards are either positive or negative** and the MDP is episodic/ terminating. <br>
The major difference between value and policy iteration is the per iteration cost. The per iteration cost for value iteration is $|S|^2|A|$ and per iteration const for policy iteration is $|S|^3 + |S|^2|A|$, the cubic term is because for policy evaluation, a system of implicit equations need to be solved.