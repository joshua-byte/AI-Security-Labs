# Prompt Injection Security Assessment

## Overview
Hands-on assessment of direct and indirect prompt injection in intentionally vulnerable LLM applications using DVLLM and PortSwigger Web Security Academy.

## Vulnerabilities Tested

### 1. Direct Prompt Injection
**Platform:** DVLLM

- **Vulnerability:** Malicious user instructions manipulated chatbot behaviour.
- **Impact:** Demonstrated disclosure of simulated sensitive information and restricted data.
- **Remediation:** Treat user input as untrusted, restrict access to sensitive information, and enforce authorization independently of the LLM.

### 2. Indirect Prompt Injection
**Platform:** PortSwigger Web Security Academy

- **Vulnerability:** Malicious instructions embedded in product-review content influenced an LLM-powered application.
- **Impact:** Demonstrated that untrusted content could influence application behaviour and trigger unintended actions.
- **Remediation:** Treat retrieved content as untrusted, validate tool calls, enforce server-side authorization, and apply least-privilege permissions.

## Remediations
- **Direct prompt injection:** Treat user input as untrusted and enforce access controls independently of the LLM.
- **Indirect prompt injection:** Treat retrieved documents and external content as untrusted; prevent embedded instructions from overriding trusted application logic.
- **Insecure output handling:** Treat LLM-generated output as untrusted. Validate and sanitize it before rendering, executing, or passing it to downstream systems.


## Tools
- DVLLM
- PortSwigger Web Security Academy

## Disclaimer
Testing was conducted in intentionally vulnerable training environments for educational purposes.
