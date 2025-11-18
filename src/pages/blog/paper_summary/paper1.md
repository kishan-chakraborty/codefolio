---
title: "Discovering state-of-the-art reinforcement learning algorithms"
date: "2025-10-31"
layout: ../../../layouts/BlogPost.astro
---
Human and other animals use powerful RL mechanism which is learnt by billions years of <br> evolution. Machine on the other hand learn through hand-crafted learning rules. The goal <br>
is autonomously discover  RL algorithm for better learning mechanism. This is achieved by meta-learning from diverse experience of various agents across many challenging environments. Meta learning is a subfield of ML where agents
are trained to learn how to learn. The discovered rule is able to out perform all the existing rules.<br>
Standard RL rules updates the predictions $V(s)$ or $Q(s, a)$ as well as the policy $\pi$ towards targets. The standard targets are some form of expected discounted reward. For 
$$
    \text{TD Learning} = r + \gamma V(s') \\
    \text{Q Learning} = \gamma\max_{a'} Q(s, a') \\
    \text{TD Learning} = r_t + \gamma V(s_{t+1}) - V(s_{t}) \\
$$
The targets define the nature of predictions like $V$, $Q$ or the advantage function.

