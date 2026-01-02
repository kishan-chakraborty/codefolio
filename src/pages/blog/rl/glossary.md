---
title: "Glossary"
layout: ../../../layouts/BlogPost.astro
order: 1
---
1. **Agent**: The learner (decision maker) is the called *agent*.
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
  
3. **Episode** : A natural notion of final step where agent environment interaction breaks. This end state often called *terminal state*.
4. **Policy**: A mapping between *states* and probabilities of selecting each possible action. For a policy $\pi$, $\pi(a|s)$
   is the probability that $A_t = a$ for $S_t = s$.

5. **Rewards**: The environment produces the reward as a result of the agent's interaction. An agent seeks to maximize 
      over time through it's choice of *actions*.
      Expected reward can be expressed using two/ three tuple
      $$
         r(s, a) = \mathbb{E}[R_t | S_{t-1} = s, A_{t-1} = a] = \sum_{r \in R}r\sum_{s' \in S}p(s', r | s, a)
      $$
      $$
      r(s, a, s') = \mathbb{E}[R_t | S_{t-1} = s, A_{t-1} = a, S_t=s'] = \sum_{r \in R}r\frac{p(s',r|s,a)}{p(s'|s,a)}
      $$
  
6. **Value Function**: It is a metric to evaluate a policy $\pi$. It tells what could an agent achieve starting
   from a state $s_t$ by following a policy $\pi$ in the long run. Mathematically
   $$
   V_{\pi}(s_t) = \sum_{i=0}^{\infty} \gamma^{i} r_{t+1+i}
   $$