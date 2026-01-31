# Architecture

This document explains **how ZeroHour is structured** and how data flows through the system.

ZeroHour is a **decision layer on top of SAST**, not a scanner itself.

---

## High-Level Flow

┌───────────────────────────┐
│     Project Codebase      │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│      Semgrep Runner       │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│       Raw Findings        │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│    Findings Normalizer    │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│       Grok Reasoner       │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│   Prioritization Engine   │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│  Fix Generator (optional) │
└─────────────┬─────────────┘
              │
              ▼
┌───────────────────────────┐
│   CLI Output / SDK Output │
└───────────────────────────┘

---

## Core Components

### 1. Semgrep Runner

**Responsibility**
- Executes Semgrep on the target project
- Collects raw static analysis findings

**Details**
- Uses Semgrep as the primary SAST engine
- No custom scanning logic inside ZeroHour
- Language support and rule quality depend on Semgrep

**Output**
- Structured Semgrep findings (JSON or equivalent)

---

### 2. Findings Normalizer

**Responsibility**
- Converts raw Semgrep output into a unified internal format

**Why this exists**
- Semgrep rules vary in structure and verbosity
- ZeroHour needs consistent data for reasoning

**Normalization includes**
- Standardized severity fields
- File and location mapping
- Deduplication
- Metadata enrichment (context, category, scope)

**Output**
- Normalized failure dataset

---

### 3. Grok Reasoner

**Responsibility**
- Interprets normalized findings
- Determines **failure impact**, **priority**, and **context**

**What Grok does**
- Correlates related findings
- Estimates blast radius and failure propagation
- Explains *why* an issue matters
- Helps decide *what to fix first*

**What Grok does NOT do**
- Scan code
- Replace Semgrep
- Execute or modify code

**Output**
- Ranked findings (Top 10 by default)
- Human-readable explanations

---

### 4. Prioritization Engine

**Responsibility**
- Enforces **forced prioritization**

**Rules**
- Default output: **Top 10 issues**
- Ranking based on:
  - Impact
  - Failure propagation
  - Centrality in the system
- Remaining findings are intentionally discarded unless explicitly requested

**Guarantees**
- Clear ordering
- Decision-oriented output
- No long unranked lists by default

---

### 5. Fix Generator (AI)

**Responsibility**
- Generates suggested fixes or remediation guidance

**Characteristics**
- Optional feature
- AI-assisted, not auto-applied
- Suggestions require human review

**Scope**
- Can generate:
  - Code-level fixes
  - Refactoring guidance
  - Best-practice recommendations

**Limitations**
- Fixes are advisory
- Not guaranteed to be correct or optimal

---

### 6. SDK Interface Layer

**Responsibility**
- Exposes ZeroHour functionality for integration

**Use cases**
- CI/CD pipelines
- Existing developer platforms
- Security tooling ecosystems
- Custom dashboards

**Capabilities**
- Programmatic execution
- Structured output (JSON)
- Access to full or prioritized findings

**Separation of concerns**
- CLI is a consumer of the SDK
- SDK is the core integration surface

---

## Design Constraints

- ZeroHour does not scan code directly
- ZeroHour does not replace SAST tools
- AI is used for reasoning and guidance, not detection
- Human decision-making remains central

---

## What This Architecture Explicitly Excludes

- Custom vulnerability scanners
- CVE databases
- Runtime instrumentation
- Automatic code modification
- Autonomous remediation

These exclusions are intentional.
