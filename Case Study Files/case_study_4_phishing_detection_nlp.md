# Case Study 4: Phishing Detection Using NLP and Machine Learning

## Abstract
Phishing remains one of the most common attack vectors in cybersecurity, often bypassing traditional blacklist-based filters. This case study examines an NLP + ML approach that analyzes email/URL content directly, comparing it against blacklist-based detection.

## Introduction
Blacklist-based phishing detection blocks known malicious domains/URLs but fails against newly registered phishing sites (zero-hour phishing). NLP-based detection instead analyzes the *content* of emails or URLs — wording, structure, urgency cues — enabling detection of previously unseen phishing attempts.

## Literature Review
Blacklist approaches are reactive: a site must be reported and verified before being blocked, leaving a window of vulnerability. ML-based classification instead learns generalizable patterns from labeled phishing/legitimate examples, offering automated feature extraction without labor-intensive manual rule engineering — critical since attackers constantly change wording and domains to evade static rules.

## Methodology
**Feature types:**
- **URL-based:** domain age (via WHOIS), URL length, presence of IP address instead of domain name, use of URL shorteners, suspicious subdomains.
- **Content-based (NLP):** TF-IDF or word embeddings on email body text, presence of urgency language ("verify your account immediately"), spelling/grammar anomalies, mismatched sender/reply-to domains.

**Pipeline:**
1. Collect a labeled dataset of phishing vs. legitimate emails/URLs (e.g., PhishTank, public Kaggle phishing datasets).
2. Preprocess text: tokenization, stopword removal, TF-IDF vectorization.
3. Extract URL structural features separately.
4. Train classifiers: Naive Bayes, Logistic Regression, Random Forest.
5. Evaluate with accuracy, precision, recall, F1-score.

## Results (from literature)
Logistic Regression on TF-IDF features achieves strong accuracy (reported around 95%) on large labeled email datasets. Naive Bayes performs competitively as a lightweight baseline. Combining URL structural features with content-based NLP features further improves detection of borderline cases.

## Proposed Extension (for Implementation)
- Build a Flask API or browser extension: paste a URL/email → extract features → classify with confidence score.
- Add explainability: highlight which words/phrases triggered the "phishing" classification (e.g., using LIME/SHAP).
- Combine with a WHOIS lookup for domain-age checking as an additional signal.

## Conclusion
NLP-based phishing detection generalizes better than blacklists against novel attacks, and is straightforward to prototype using standard text-classification techniques — a good fit for a cybersecurity-focused, demoable college project.

## References
1. Context-Aware Phishing Email Detection Using Machine Learning and NLP (2025). ResearchGate/arXiv.
2. Enhancing Phishing Detection in Financial Systems through NLP (2025). arXiv:2507.04426.
