# Data Poisoning Assessment

## Overview
Hands-on assessment of data poisoning vulnerabilities in an intentionally vulnerable AI training portal using DVLLM.

## Vulnerabilities Identified

### 1. Training Data Injection
- **Vulnerability:** The application accepted attacker-controlled content submitted as training data.
- **Impact:** Malicious or misleading entries could influence model behaviour if incorporated into the training dataset.
- **Remediation:** Validate and sanitize submitted data, restrict dataset write access, and review contributions before including them in training.

### 2. Training Data Label Poisoning
- **Vulnerability:** Incorrect labels were accepted into the training dataset, including a successful attempt to submit poisoned labels.
- **Impact:** Corrupted labels could degrade model accuracy and cause unreliable predictions.
- **Remediation:** Validate labels, enforce data-quality checks, track data provenance, and audit training datasets before retraining.

### 3. Input Filtering Bypass
- **Vulnerability:** The lab demonstrated that content filtering alone did not prevent every malicious training-data submission.
- **Impact:** Poisoned examples could enter the dataset despite basic filtering.
- **Remediation:** Use layered validation, trusted-source controls, anomaly detection, and human review for suspicious contributions.

## Tools Used
- DVLLM — Damn Vulnerable LLM
- Web browser

## Key Takeaway
AI training pipelines must protect data integrity. Input filtering alone is insufficient; training data requires provenance tracking, label validation, access controls, and ongoing quality checks.

## Disclaimer
For educational purposes and authorized security testing only.
