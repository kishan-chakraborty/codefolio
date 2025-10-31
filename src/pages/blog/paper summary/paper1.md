---
title: "Discovering state-of-the-art reinforcement learning algorithms"
date: "2025-10-31"
---

**Proximal Policy Optimization (PPO)** is one of the most popular policy-gradient algorithms in reinforcement learning.

It strikes a balance between **trust-region methods** (like TRPO) and **simple policy updates** by limiting how much the new policy can deviate from the old one during optimization.

---

## 🧩 Key Idea

PPO modifies the policy-gradient objective using a **clipped surrogate loss**:

\[
L^{CLIP}(\theta) = \mathbb{E}_t \left[ \min\left( r_t(\theta)\hat{A}_t, \text{clip}(r_t(\theta), 1 - \epsilon, 1 + \epsilon)\hat{A}_t \right) \right]
\]

where  
- \(r_t(\theta) = \frac{\pi_\theta(a_t|s_t)}{\pi_{\theta_{old}}(a_t|s_t)}\) is the probability ratio, and  
- \(\hat{A}_t\) is the advantage estimate.

---

## 🧠 Intuition

- If the policy update changes actions too much (beyond ±ε), the **clip** term prevents large destructive updates.  
- PPO is simple, stable, and works well in high-dimensional continuous control tasks.

---

That’s it for this first post! 🚀
