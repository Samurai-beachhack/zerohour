# Glossary

This glossary defines terms as used **specifically in ZeroHour**.

---

## SAST
Static Application Security Testing.

Tools that analyze source code to detect vulnerabilities.
ZeroHour does not perform SAST.

---

## Decision Layer
A layer that helps decide **priority and focus**, not detect issues.

ZeroHour operates as a decision layer on top of SAST outputs.

---

## Failure Impact
The extent to which a failure affects critical functionality or business workflows.

Measured conceptually, not numerically.

---

## Failure-Prone Area
Code that, if it fails, causes:
- Cascading failures
- Service disruption
- Blocking of core flows

---

## Forced Prioritization
A design rule where only a small fixed number of findings are reported.

ZeroHour enforces this intentionally.

