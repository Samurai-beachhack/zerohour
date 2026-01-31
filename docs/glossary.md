# Glossary

This glossary defines terms as used **specifically in ZeroHour**.

---

## SAST
Static Application Security Testing.

Tools that analyze source code to detect vulnerabilities.
ZeroHour does not perform SAST itself.

---

## Semgrep
A static analysis engine used by ZeroHour to scan source code.

Semgrep is responsible for:
- Detecting issues
- Producing structured findings

ZeroHour builds decision logic **on top of Semgrep output**.

---

## Decision Layer
A layer that determines **priority and focus**, not detection.

ZeroHour operates as a decision layer on top of SAST findings to decide
what matters first.

---

## Failure Impact
The extent to which a failure affects critical functionality or business workflows.

Estimated conceptually based on structure, propagation, and centrality.
Not measured numerically.

---

## Failure-Prone Area
Code that, if it fails, can cause:
- Cascading failures
- Service disruption
- Blocking of core workflows

---

## Forced Prioritization
A design rule where only a fixed number of findings are reported.

ZeroHour enforces **Top 10 by default** to ensure decision clarity.

---

## Grok
The reasoning engine used by ZeroHour to interpret findings.

Grok is responsible for:
- Correlating issues
- Estimating failure impact
- Providing explanations and prioritization

Grok does not scan code.

---

## LLM Reasoning
The use of large language models to reason over structured data.

In ZeroHour, LLM reasoning is used for:
- Interpreting Semgrep findings
- Explaining why issues matter
- Suggesting possible fixes

LLMs do not perform detection or execute code.

---

## SDK
A programmatic interface that exposes ZeroHour functionality.

The SDK allows:
- Integration into CI/CD pipelines
- Embedding ZeroHour into existing tools
- Access to structured output

The CLI is a consumer of the SDK.

