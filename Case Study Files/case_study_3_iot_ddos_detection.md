# Case Study 3: Machine Learning-Based DDoS Detection for IoT Devices

## Abstract
IoT devices are frequent targets and vectors for Distributed Denial of Service (DDoS) attacks due to weak security and predictable behavior. This case study examines using IoT-specific traffic characteristics — limited endpoint counts and regular packet timing — as features for ML-based DDoS detection.

## Introduction
Unlike general-purpose computers, IoT devices (cameras, sensors, smart plugs) typically communicate with a small, fixed set of endpoints on a regular schedule. This narrow, predictable behavior makes anomalies (like DDoS attack traffic) easier to detect than in general network traffic — but it also makes these devices attractive targets for botnets (e.g., Mirai) that hijack them to launch attacks.

## Literature Review
Traditional network intrusion detection relies on signature matching or simple thresholding (e.g., packet-rate limits), which generates high false positives on legitimate traffic bursts and misses novel attack patterns. Recent work applies supervised ML models — trained on IoT-specific behavioral features — to distinguish normal device traffic from DDoS attack traffic with high accuracy, leveraging the fact that IoT traffic is inherently more regular than general-purpose network traffic.

## Methodology
**Feature Engineering (IoT-specific):**
- Number of unique destination endpoints contacted (IoT devices talk to very few endpoints normally).
- Packet timing regularity (IoT devices send data on fixed intervals; attack traffic disrupts this pattern).
- Packet size distribution.
- Protocol usage patterns (e.g., unexpected protocols indicate compromise).

**Pipeline:**
1. Capture network traffic (e.g., via a testbed of IoT devices or public datasets like N-BaIoT or CICIDS).
2. Extract the above behavioral features per time window.
3. Train classifiers: Decision Trees, Random Forest, and simple Neural Networks.
4. Evaluate using accuracy, precision, recall on held-out attack/benign traffic.

## Results (from literature)
Models leveraging IoT-specific behavioral features consistently outperform generic network-traffic classifiers, since the narrower behavior space makes attack deviations stand out more clearly. Neural network-based classifiers, in particular, achieve strong detection accuracy across multiple attack types (e.g., SYN flood, UDP flood).

## Proposed Extension (for Implementation)
- Simulate an IoT network in a lab (Raspberry Pi devices, or a virtual testbed with `hping3` to generate synthetic DDoS traffic).
- Use `Scapy` (already familiar to you from NetPulse) to capture and extract features.
- Train a lightweight classifier (Random Forest) suitable for edge deployment.
- Build a real-time dashboard showing device traffic health and DDoS alerts.

## Conclusion
DDoS detection tailored to IoT traffic patterns is more tractable than general network intrusion detection because IoT behavior is narrower and more predictable, making this a practical and demonstrable cybersecurity project.

## References
1. Doshi, R., Apthorpe, N., & Feamster, N. (2018). Machine Learning DDoS Detection for Consumer Internet of Things Devices. arXiv:1804.04159.
2. Meidan, Y., et al. (2018). N-BaIoT—Network-based detection of IoT botnet attacks using deep autoencoders. IEEE Pervasive Computing.
