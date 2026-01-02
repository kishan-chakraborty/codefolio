---
title: "Finite Markov Decision Process"
layout: ../../../layouts/BlogPost.astro
order: 2
---
## Agent Environment Interface
In finite MDP the states actions and rewards all have a finite no. of elements in it.
In this case, the *random variable* $R_t, S_t$ have well defined *discrete probability distributions* 
dependent only on the preceding state and actions. $i.e.$
$$
p(s', r | s, a) = Pr\{S_t=s', R_t=r|S_{t-1}=s,A_{t-1}=a\} \hspace{0.2 in }\forall s', s \in \mathbb{S}, a \in \mathbb{A}(s)
$$

p is called *dynamics* of the MDP, an arbitrary deterministic function of four variables.
$$
\sum_{s', a} p(s', r | s, a) = 1 \hspace{0.2 in }\forall s \in \mathbb{S}, r \in \mathbb{R}
$$

*Markov Property* means that the probability for $S_t, R_t$ depends only on the preceding state. 
This is best viewed as a restriction not on the environment but the state. The state must include 
information about all the past agent-environment interaction that make a difference to the future.

## Goals and Rewards
*Reward Hypothesis*: The goal and purpose of the agent can be thought of maximizing the expected cumulative reward.
If we want the agent to work as expected, we need to hack reward accordingly.

## Returns and Episodes
For a sequence of rewards received after t $R_{t+1}, R_{t+2} \cdots$, in general we wish to maximize the *expected return*, 
which is a function of the reward sequence. *i.e.*

$$
G_t \overset{\cdot}{=}  R_{t+1} + R_{t+1} \cdots + R_{T}
$$

Here $T$ is the final step (makes sense when there is a natural notion of final state called *terminal state*). 
This sequence is called an *episode*. The next episode begins independent of the terminal state.

Tasks where agent environment interaction does not break naturally are called *continuing tasks*. The previous formulation 
is problematic because the *terminal state* maybe at $T = \infty$. The modified return is called discounted return

$$
\begin{align*}
G_t &\overset{\cdot}{=}  R_{t+1} + \gamma R_{t+1} + \gamma^2 R_{t+2} + \cdots \\
&= \sum_{k=0}^\infty \gamma^k R_{t+k+1}\\
&= R_{t+1} + \gamma G_{t+1}
\end{align*}

$$

$0 \leq \gamma \leq 1$ is called *discount factor*.
The notion of episodic and continuing tasks can be unified by assuming that for episodic tasks there exists a virtual 
*absorption state* where once reached the process can not return and always receive a reward of 0.

## Policies and Value functions
