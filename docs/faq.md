# FAQ

---

## Is ZeroHour a SAST tool?
No.

ZeroHour does not detect vulnerabilities or CVEs.

---

## How does ZeroHour relate to SAST?
ZeroHour is a **decision layer on top of SAST**.

- SAST finds what is wrong
- ZeroHour decides what matters first

ZeroHour helps **interpret and prioritize** results, not replace scanners.

---

## Does ZeroHour run instead of SAST?
No.

It is designed to be used **alongside or after SAST** to focus attention on the highest-impact failure areas.

---

## Does ZeroHour use AI?
Yes.

ZeroHour uses AI for reasoning, prioritization explanation, and fix suggestions.
It does not rely on AI for raw code scanning.

---

## What role does Semgrep play?
Semgrep performs the static analysis and generates structured findings.
ZeroHour builds decision logic on top of these findings.

---

## How many issues does ZeroHour report?
Maximum of **10**.

This limit is intentional and enforced. You can adjust the value.

---

## What kind of issues does it surface?
- Failure-prone logic
- High-impact breakpoints
- Single points of failure
- Risk concentration areas

Not vulnerabilities.

---

## Is the output deterministic?
Yes.

Same input always produces the same output.
No randomness. No learning.

---

## Is ZeroHour production ready?
No.

It is a prototype built during a hackathon.

---

## Why are there no risk scores?
Numeric scores hide reasoning.

ZeroHour prioritizes **explainability and decision clarity** over scoring.

