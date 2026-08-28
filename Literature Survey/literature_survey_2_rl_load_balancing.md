# Literature Survey: Reinforcement Learning-Based Load Balancing in Cloud Computing

## Purpose of This Survey

This survey reviews the broader body of research on RL-based cloud resource management and load balancing — beyond the single base paper (Chawla, 2024) used for this project — to establish context, compare methodologies, and identify open gaps.

---

## 1. Evolution of Load Balancing in Cloud Computing

1. **Classical/heuristic scheduling** — Round-Robin, Least Connections, Weighted Balancing, First-Come-First-Serve (FCFS), Shortest Job First (SJF), MinMin, MaxMin. Simple and predictable, but static — they don't adapt to real-time workload variability, which leads to unfair task allocation, longer execution times, and higher energy consumption.
2. **Meta-heuristic / nature-inspired optimization** — genetic algorithms, particle swarm optimization, ant colony optimization, and similar bio-inspired methods used to search for near-optimal task-to-server assignments. A 2024 review examined 47 such nature-inspired algorithms applied to cloud load balancing, building a taxonomy across ten comparison dimensions from a decade of literature (2014–2024).
3. **Machine Learning-based scheduling** — supervised models predicting traffic/load to inform proactive allocation.
4. **Reinforcement Learning-based scheduling** — agents that learn optimal task-distribution policies through trial-and-error interaction with the environment, without needing labeled training data.

---

## 2. Key Papers Reviewed

### 2.1 Foundational RL Frameworks
- **Chawla (2024)** [base paper] — proposed a Q-learning-based adaptive load balancer, benchmarked against round-robin, least-connections, and weighted balancing using the CloudSim simulator across 10 heterogeneous servers; demonstrated improved response time, resource utilization, and task completion rate, especially under high/bursty load.
- **Mnih et al. (2015)** — established Deep Q-Networks (DQN), combining Q-learning with deep neural networks; foundational for scaling RL beyond small, tabular state spaces — directly relevant to scaling load-balancing RL agents to larger server pools.
- **Mao et al. (2016)** — applied deep RL to general resource management problems, showing RL can learn scheduling policies competitive with hand-tuned heuristics.

### 2.2 Applied Cloud/Fog RL Studies (2023–2025)
- A Springer-published study used the **WorkflowSim** simulation environment to empirically compare RL-based resource scheduling and load balancing against classical algorithms across four workload scenarios, explicitly framing the goal as satisfying Quality of Service (QoS) and Service-Level Agreement (SLA) requirements — echoing the same motivation as the base paper.
- An IEEE-published framework used **Q-learning to dynamically select among scheduling algorithms** (rather than directly assigning tasks), tested on the real-world Google Cloud Jobs Dataset, and reported concrete gains: 91.31% load-balancing efficiency, 50.67 tasks/second throughput, 88.78% resource utilization, and energy savings — demonstrating RL's value extends to algorithm-selection meta-strategies, not just direct task routing.
- Research on **RL for fog computing resource management** provides a comprehensive analysis covering provisioning, placement, scheduling, allocation, offloading, and load balancing — noting that most prior surveys focus on traditional optimization and only "briefly" cover RL, identifying this as a specific literature gap.
- A **Deep RL for cloud resource scheduling** review (Artificial Intelligence Review, 2024) surveyed the broader landscape, referencing earlier load-balancing-specific reviews (e.g., Xu et al.'s review of VM placement load-balancing algorithms) as important precedent literature.

### 2.3 Risk- and Cost-Aware Extensions
- Recent work applies **Deep Reinforcement Learning to balance risk and cost** in cloud-based IoT business processes across multiple cloud providers, integrating a confidentiality-risk metric and cost-evaluation function into the Q-learning reward — extending pure performance-based RL load balancing toward multi-objective optimization (performance + security + cost simultaneously).

---

## 3. Comparative Summary Table

| Approach | Representative Work | Strengths | Limitations |
|---|---|---|---|
| Classical heuristics | Round-Robin, Least-Connections, FCFS, SJF | Simple, predictable, easy to implement | Static; fails under dynamic/bursty workloads |
| Nature-inspired optimization | 47-algorithm review (2014–2024) | Can find near-optimal solutions without gradient information | Often slow to converge; many competing variants with unclear best choice |
| Predictive ML (supervised) | Neural net/regression traffic forecasting | Can proactively pre-allocate resources | Needs accurate historical data; struggles to generalize to unseen conditions |
| Q-learning (tabular RL) | Chawla (2024) [base paper]; Google Cloud Jobs Dataset study | No labeled data needed; adapts continuously; strong reported gains (efficiency, throughput, energy) | Training time can be a bottleneck; state-space grows fast with more servers |
| Deep RL (DQN and beyond) | Mnih et al.; Mao et al. | Scales to large, complex state spaces | Higher implementation complexity; more compute-intensive |
| Multi-objective RL (cost/risk-aware) | Risk-cost DRL for multicloud IoT | Balances performance, security, and cost together | Newer, more complex reward design |

---

## 4. Identified Research Gaps

1. **Narrow scope in most studies:** many RL-based load balancers optimize a single objective (usually response time or utilization) without comprehensively addressing the full complexity of dynamic cloud environments — a gap explicitly named in the base paper itself.
2. **Limited large-scale, real-world validation:** most studies (including the base paper) rely on simulators like CloudSim or WorkflowSim rather than production cloud infrastructure; the Google Cloud Jobs Dataset study is a rarer example of using real-world data.
3. **Integration with modern cloud-native tooling:** limited research connects RL-based load balancing with container orchestration platforms like Kubernetes, despite these being the dominant deployment model in production cloud systems today.
4. **Multi-objective trade-offs underexplored:** most classical RL load balancers optimize primarily for latency/utilization, while real deployments also care about cost and security — only recently addressed by risk/cost-aware DRL extensions.

---

## 5. How This Project Positions Itself

This project builds on the **tabular Q-learning approach** from the base paper (Chawla, 2024) rather than deep RL, for practical reasons validated by the survey:
- Tabular Q-learning is implementable in pure Python without requiring GPU resources or large-scale infrastructure — appropriate for a student project timeline.
- It directly benchmarks against the same three classical baselines (round-robin, least-connections, weighted balancing) used throughout the surveyed literature, enabling a fair, literature-consistent comparison.
- The proposed simplification — simulating servers as Python objects rather than using full CloudSim — mirrors the WorkflowSim-based study's approach of using a lighter-weight simulation environment while still producing comparable, defensible metrics (response time, utilization, task completion rate).

The survey also suggests two credible "future work" directions consistent with what examiners might ask about: (a) scaling to Deep Q-Networks for larger server pools, and (b) incorporating a cost or energy-efficiency term into the reward function, following the multi-objective RL trend identified above.

---

## References

1. Chawla, K. (2024). Reinforcement Learning-Based Adaptive Load Balancing for Dynamic Cloud Environments [base paper]. arXiv:2409.04896.
2. Mnih, V., et al. (2015). Human-level control through deep reinforcement learning. Nature, 518(7540), 529-533.
3. Mao, H., Alizadeh, M., Menache, I., & Kandula, S. (2016). Resource management with deep reinforcement learning. HotNets.
4. Reinforcement Learning to Improve Resource Scheduling and Load Balancing in Cloud Computing. SN Computer Science (2023).
5. Reinforcement Learning Approach for Optimizing Cloud Resource Utilization With Load Balancing. IEEE Xplore.
6. Nature-Inspired optimization algorithms for enhanced load balancing in cloud computing: A comprehensive review with taxonomy, comparative analysis, and future trends (2024).
7. Reinforcement learning-based solution for resource management in fog computing: A comprehensive survey. ScienceDirect (2025).
8. Deep reinforcement learning-based methods for resource scheduling in cloud computing: a review and future directions. Artificial Intelligence Review (2024).
9. Toward a Reinforcement Learning Approach for Balancing Risk and Cost in Cloud-Based IoT-Driven Business Processes.
10. Calheiros, R. N., et al. (2011). CloudSim: A toolkit for modeling and simulation of cloud computing environments.
