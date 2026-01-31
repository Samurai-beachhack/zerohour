# Limitations

This document lists **explicit, intentional limits** of ZeroHour in its current design.

---

## No Native Vulnerability Detection

ZeroHour does not perform vulnerability detection on its own.

- No CVE database
- No dependency scanning
- No custom security rule engine

All raw detection is delegated to **Semgrep**.

---

## Dependence on Semgrep Quality

ZeroHour’s analysis quality depends on:
- The Semgrep rules used
- Rule coverage and correctness
- The structure of Semgrep findings

Poor or incomplete rules lead to poor downstream reasoning.

---

## AI Reasoning Limitations

AI is used for:
- Prioritization reasoning
- Explanation generation
- Fix or remediation suggestions

Limitations:
- Explanations may vary between runs
- Suggested fixes are advisory only
- Output requires human validation

ZeroHour does not apply fixes automatically.

---

## No Business Context Awareness

ZeroHour cannot infer:
- Revenue impact
- Legal or compliance requirements
- Organization-specific priorities
- User intent or domain meaning

Impact is inferred **structurally**, not semantically.

---

## Static Analysis Only

- No runtime execution
- No production telemetry
- No performance profiling
- No behavioral tracing

Runtime failures that require live data cannot be detected.

---

## Language and Framework Dependence

Analysis effectiveness depends on:
- Languages supported by Semgrep
- Recognizable project layouts
- Common architectural patterns

Unconventional structures may reduce accuracy.

---

## Not a Risk Scoring Tool

- No numeric severity scores
- No confidence percentages
- No probabilistic guarantees

ZeroHour prioritizes **explainability and decision clarity** over metrics.

---

## SDK and Integration Constraints

- SDK behavior depends on host environment
- CI/CD integrations may impose execution limits
- External API availability can affect AI features

These constraints vary by integration context.

