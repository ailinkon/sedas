# SEDAS — Social Engineering Defence and Awareness System

> A layered, human-centred cybersecurity framework for educational institutions. Combines AI-driven phishing detection, blockchain URL verification, adaptive awareness training, and governance analytics into a single defence-in-depth platform.

[![Status](https://img.shields.io/badge/status-capstone--complete-brightgreen)]()
[![Domain](https://img.shields.io/badge/domain-higher%20education-blue)]()
[![Approach](https://img.shields.io/badge/approach-AI%20%2B%20Blockchain%20%2B%20TPB-orange)]()
[![Literature](https://img.shields.io/badge/literature%20review-40%20papers-lightgrey)]()

---

## Overview

Social engineering has become the dominant initial access vector behind modern breaches, exploiting human psychology rather than system vulnerabilities. Universities are especially exposed: highly networked environments, diverse user communities, open external collaboration, and seasonal spikes (enrolment, exams) that reduce user vigilance.

SEDAS is a theory-grounded, microservices-based defence system designed specifically for the higher education sector. It moves beyond point solutions (spam filters, one-off awareness videos) by integrating four reinforcing layers: an AI detection engine, a blockchain verification service, an adaptive training engine, and a governance dashboard. The goal is to shift users from passive targets into active defenders, while giving CISOs, deans, and SOC analysts the evidence they need to act.

The project was completed as the capstone unit (MIS5203 — Applied IS Project) of the Master of Information Systems (Cyber Security specialisation) at Apex Australia Higher Education. The design is backed by a structured review of 40 peer-reviewed papers, coded across input, process, output, and research-gap dimensions.

---

## The Problem

Traditional controls — secure email gateways, endpoint agents, allow-lists — are necessary but insufficient against:

- Psychologically tuned lures that exploit authority, urgency, fear, or curiosity
- Business email compromise (BEC) and spear-phishing that imitates faculty writing style
- QR-phishing that bypasses domain allow-lists
- Context-aware attacks timed to academic calendar peaks (enrolment, exams, grade release)

More than 90% of breaches involve a human element. Generic awareness training, delivered once a semester, does not shift behaviour. SEDAS addresses this by treating human behaviour as a primary security surface with continuous measurement and responsive hardening.

---

## System Architecture

SEDAS follows a hub-and-spoke microservices architecture with four primary functional components:

| Component | Purpose | Core Tech |
|---|---|---|
| *AI Detection Engine* | Real-time classification of phishing and SE content | Transformer NLP (BERT, RoBERTa), stylometry, sender reputation |
| *Blockchain Verification Service* | Tamper-resistant URL trust registry | Ethereum-compatible chain, Layer-2 (Polygon), off-chain cache |
| *Adaptive Training Engine* | Just-in-time micro-interventions tailored to user risk profile | TPB-based risk scoring, persona-driven content delivery |
| *Governance Dashboard* | Institutional visibility and audit-ready reporting | Role-based views (CISO, dean, dept lead), drill-down analytics |

*Layers and stack:*

- *Frontend.* React/Angular SPA, accessibility to WCAG 2.1 AA, security banners, trust indicators, micro-lessons.
- *Backend.* Python (Flask / FastAPI) RESTful services; TensorFlow / PyTorch model serving on GPU/TPU nodes.
- *Data.* PostgreSQL for structured records (profiles, risk scores, training history, compliance logs); MongoDB / Elasticsearch for threat-intel indexing and log analytics; Kafka / RabbitMQ for event streaming.
- *Security.* TLS 1.3, institutional MFA, role-based access control, immutable audit logs.
- *Integration.* LMS, SIEM, LDAP/SSO, ticketing — all via standards-based connectors.
- *Deployment.* Kubernetes clusters with a hybrid option (core services in cloud, sensitive user data on-prem), 99.7% availability target via geo-replication.

---

## Theoretical Foundations

SEDAS is deliberately grounded in three reinforcing theories:

1. *Theory of Planned Behaviour (TPB)* — models why users fall for phishing through attitude, subjective norm, and perceived behavioural control. Drives adaptive training content and alert severity.
2. *AI-powered threat detection* — transformer-based NLP (BERT / RoBERTa) consistently reports >95% detection accuracy in the literature, outperforming static rule-based filters.
3. *Blockchain trust mechanisms* — tamper-resistant ledgers for URL provenance remove reliance on centralised, easily compromised allow-lists.

The novelty is in the integration. Most existing work addresses only one of these dimensions; SEDAS combines them into a behaviourally informed technical system.

---

## Phased MVP Rollout

| Phase | Deliverables | Key Metrics |
|---|---|---|
| *Phase 1 — Core Detection* | AI phishing engine, blockchain URL verification, basic dashboard | Precision ≥ 95%, latency < 200 ms |
| *Phase 2 — Behavioural Layer* | Adaptive training engine, persona-based interventions, feedback loops | 30% reduction in risky click behaviour |
| *Phase 3 — Institutional Integration* | Full LMS, SIEM, and identity integration; advanced dashboards | ≥ 90% institutional traffic coverage |

---

## Evaluation Framework

*Technical KPIs*
- Phishing detection F1 ≥ 0.95
- URL verification latency < 200 ms
- Dashboard uptime ≥ 99.7%

*Behavioural KPIs*
- ≥ 30% reduction in risky click-through rate
- ≥ 80% voluntary training completion
- Positive shift in security-culture index (pre/post survey)

*Institutional KPIs*
- Compliance audit pass rates
- Reduced incident-response cost
- Improved risk reporting at department level

---

## Literature Review (40 Papers)

A structured review of 40 peer-reviewed papers, drawn from Q1–Q3 journals (including Computers & Security, Information & Management, Journal of Applied Security Research, International Journal of Advanced and Applied Sciences), underpins every design decision. The review matrix is coded across eight dimensions:

- *Input* — hardware, software, methods, datasets, features, platforms
- *Process* — methods, models, algorithms, architectures, techniques, frameworks
- *Output* — accuracy, reduction rate, latency, precision, recall, F1, error rate, throughput
- *Others* — advantages, limitations, domain, novelty, practical applicability, research gaps

The compiled matrix is published in reports/literature_review.xlsx and can be used as a standalone reference for researchers entering the field.

*Ashraful Islam's contribution* — 10 papers covering SOAR-based SE mitigation, human factors in SE, phishing detection with LLMs, and behavioural analysis for corporate environments.

---

## Ethics, Privacy, and Sustainability

SEDAS treats ethics as a first-class design requirement, not an afterthought:

- *Informed consent and transparency.* Users are told what is collected, why, and how to opt out where appropriate.
- *Data minimisation.* Only essential behavioural indicators are captured; pseudonymisation is default, with controlled re-identification only by privileged roles.
- *Fairness and non-discrimination.* Training content adapts for language and accessibility (WCAG 2.1 AA), with alternative formats for neurodiverse students.
- *Autonomy and psychological safety.* The system is designed for coaching and enablement, never punitive measures.
- *Legal compliance.* FERPA, GDPR, and the Australian Privacy Act 1988 (including the Notifiable Data Breaches scheme) are all explicitly addressed.
- *Sustainability.* Efficient inference workloads, Layer-2 blockchain to reduce energy and gas costs, and an operational model built around institutional self-sufficiency rather than vendor lock-in.

---

## Limitations (Honest Caveats)

- SEDAS is a research and design artefact. Production deployment requires institutional budget, IT change-management capacity, and legal sign-off that are outside the scope of this project.
- The AI detection component depends on access to institutional email flow and representative phishing corpora; public datasets underfit targeted spear-phishing.
- Blockchain latency is a real trade-off; the design mitigates this with off-chain caching, but on-chain verification is not suitable for every use case.
- User-resistance and alert-fatigue risks are managed via adaptive thresholds and digest modes, but long-term behavioural change requires institutional cultural commitment, not just technology.

---

## Future Work

- Federated learning to train detection models across institutions without sharing raw data.
- Cross-institutional threat intelligence sharing via the blockchain layer.
- Longitudinal behavioural studies measuring training impact over multiple semesters.
- Multilingual corpora (including Bengali) for non-English-medium campuses.
- Integration with national and global policy frameworks (Essential Eight, NIST CSF 2.0, APRA CPS 234 for university-affiliated finance entities).

---

## Team and My Contribution

This was a team capstone project. Team members contributed 10 papers each to the compiled literature review, and collaborated on the overall system design.

*My contribution (Ashraful Islam  — Student ID 240135):*
- Coordinated the 10-paper literature segment on SOAR-based mitigation, behavioural analysis, and LLM-assisted phishing detection.
- Contributed to the AI Detection Engine component design and threat model.
- Authored the ethics, privacy, and Australian regulatory alignment sections.
- Built the coded matrix cells for my paper set across Input, Process, Output, and Others dimensions.

---

## About the Author

*Ashraful Islam Linkon*
Master of Information Systems (Cyber Security specialisation) — Apex Australia Higher Education, Sydney
Targeting graduate and junior roles in Cyber Security Analysis, GRC, or Data/IS Analysis across Australia.

- LinkedIn: [linkedin.com/in/linkon](https://www.linkedin.com/in/linkon)
- GitHub: [github.com/ailinkon](https://github.com/ailinkon)
- Email: Islam.ashraful.linkon@gmail.com

Languages: English (professional), Bengali (native).

---

## Academic Attribution

Completed as part of MIS5203 — Applied IS Project at Apex Australia Higher Education (2025). References cited in reports/sedas_final_report.pdf follow APA 7th edition. The literature review matrix is a team artefact; individual contributions are attributed within the spreadsheet.

---

## License

Released under the MIT License — see [LICENSE](./LICENSE).

Use for educational, research, or defensive security purposes is encouraged. Use to conduct unauthorised phishing, social engineering, or any other offensive activity is expressly forbidden.
