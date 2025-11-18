---
title: "Glossary"
layout: ../../../layouts/BlogPost.astro
order: 1
---
1. **Bellman Optimality Equation**: Represents the value function of a state wrt to an **optimal policy**.
   $$
      V^*(s) = \max_{a} r(s, a) + \gamma \mathbb{E}_{s'}[V^*(s')]
   $$
   
2. **Environment**: RL environment is the universe of an RL agent. It consists of **states** containing the *location* of the agent.
   It has a set of **actions** from which an agent choose what to *do*. Corresponding to each action at each state the environment awards
   it with a **reward** and it moves to a new state.
   Mathematically an environment is given by an MDP $(S, A, P, R, \gamma)$
   - $S$: Set of all possible states.
   - $A$: Set of all possible actions.
   - $P(s'|s,a)$: Transition probability form state $s$ to $s'$.
   - $R(s, a, s')$: Reward for action $a$ in state $s$ and following state $s'$.
   - $\gamma$: Discount factor.
  
3. **Value Function**: It is a metric to evaluate a policy $\pi$. It tells what could an agent achieve starting
   from a state $s_t$ by following a policy $\pi$ in the long run. Mathematically
   $$
   V_{\pi}(s_t) = \sum_{i=0}^{\infty} \gamma^{i} r_{t+1+i}
   $$
