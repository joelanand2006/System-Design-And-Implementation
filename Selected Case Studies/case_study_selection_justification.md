# Justification for Selected Case Studies

## Case Studies Chosen
1. **Malware Detection Using Machine Learning Algorithms**
2. **Reinforcement Learning-Based Adaptive Load Balancing for Dynamic Cloud Environments**

---

## 1. Balance Between Cybersecurity and General CSE

The brief called for a mix, not an all-cybersecurity list. Malware Detection represents the **cybersecurity specialization** — directly relevant to prior internship and project background (NetPulse). RL Load Balancing represents a **general CSE/systems** topic. Together, they demonstrate breadth rather than a one-note portfolio.

## 2. Different, Complementary Problem Types

- **Malware Detection** is a **classification problem** — label a file as malicious or benign based on its features.
- **RL Load Balancing** is a **sequential decision-making problem** — choose actions over time, learning from feedback.

Selecting one of each demonstrates the ability to work across two fundamentally different ML paradigms — **supervised learning vs. reinforcement learning** — rather than two variations of the same technique.

## 3. Feasibility Given Timeline and Existing Stack

- **Malware Detection** uses tabular ML (scikit-learn, XGBoost) — a well-understood pipeline, realistically implementable, testable, and defensible within the available time.
- **RL Load Balancing** can be simplified to a pure-Python simulation with a Q-table — no real cloud infrastructure or GPU-heavy deep RL required, keeping it buildable while still being conceptually richer than a standard classifier project.

## 4. Panel Appeal and Originality

A malware classifier alone risks looking like "yet another Random Forest on Kaggle data" — panels have seen many similar submissions. Pairing it with the RL load balancer adds a **systems-design component** (state/action/reward, a self-improving agent) that is less common in typical student submissions and demonstrates deeper engineering than simply calling `.fit()` on a dataset.

## 5. Strong, Accessible Base Papers

Both topics had a clear, citable, fully free base paper — no IEEE paywall involved:
- **Tiwari et al. (2025)** — IJSRSET, fully open access.
- **Chawla (2024)** — arXiv, fully open access.

Both papers report results detailed enough to benchmark against, and both supported a full literature survey built entirely from free, non-paywalled sources.

## 6. Extendability / Future Scope

Both case studies have credible, well-documented "future scope" directions grounded in existing literature — useful if a panel asks "what would you do next?":
- **Malware Detection:** incorporating dynamic/behavioral analysis (sandboxing) for resilience against obfuscation; adversarial training against evasion.
- **RL Load Balancing:** scaling to Deep Q-Networks (DQN) for larger server pools; incorporating cost- or energy-efficiency terms into the reward function (multi-objective RL).

---

## Summary

| Criterion | Malware Detection | RL Load Balancing |
|---|---|---|
| Domain | Cybersecurity | General CSE / Systems |
| ML Paradigm | Supervised (classification) | Reinforcement Learning |
| Implementation Effort | Low-Moderate | Moderate |
| Base Paper Access | Free (IJSRSET, open access) | Free (arXiv) |
| Panel Differentiation | Familiar but well-executed | Less common, systems-design depth |
| Future Scope | Dynamic/behavioral analysis, adversarial training | Deep Q-Networks, cost-aware rewards |

Together, these two case studies balance specialization with breadth, feasibility with originality, and familiarity with technical depth — while both remaining fully supportable with free, credible reference material.
