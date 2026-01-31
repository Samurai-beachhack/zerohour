# ZeroHour

ZeroHour is a terminal-native CLI that answers one question:

> **What breaks the business first if this code fails?**

It is **not a SAST replacement**.  
It is the **decision layer before SAST**.

---

🌐 **ZeroHour website:**  
https://samurai-beachhack.github.io/zerohour

---

## What Problem It Solves

Modern SAST tools:
- Generate hundreds of findings
- Treat all issues as equal
- Lack business or failure impact context

Teams know *what is wrong*  
They do **not know what to fix first**

---

## What ZeroHour Does

ZeroHour analyzes a codebase and outputs:

- **Only the top 10 issues**
- Ranked by **failure impact**
- Explained in **business consequences**

It focuses on:
- Failure-prone areas
- Single-point-of-failure logic
- Risk concentration, not volume

---


## Core Principles

- Failure-first, not vulnerability-first
- Forced prioritization (Top 10 only)
- Business impact over technical noise
- Deterministic and auditable logic
- Terminal-only workflow

---

## How It Fits With SAST

**SAST tools**
- Find what is wrong

**ZeroHour**
- Decides what matters first

Recommended flow:
ZeroHour → Decide priorities → SAST → Fix

---

## Usage

After building the project:

```bash
# Analyze current directory
./zerohour analyze

# Analyze a specific directory
./zerohour analyze -C examples/sample-app

# Plain output (no box UI)
./zerohour analyze --no-box

Optional ways to run:
npm run analyze
npm run analyze -- -C examples/sample-app
npx zerohour analyze
npm link && zerohour analyze
To run from anywhere:
export PATH="/path/to/zerohour:$PATH"
zerohour analyze
```

---

## Documentation

Start here:
- 📘 **Overview** — what ZeroHour is and why it exists  
  [docs/overview.md](./docs/overview.md "Project overview and core idea")

Getting started:
- ⚙️ **Installation** — setup and build instructions  
  [docs/installation.md](./docs/installation.md "Installation guide")
- ▶️ **Usage** — how to run the CLI and interpret output  
  [docs/usage.md](./docs/usage.md "CLI usage guide")
- ❓ **FAQ** — common questions and clarifications  
  [docs/faq.md](./docs/faq.md "Frequently asked questions")

How it works:
- 🧱 **Architecture** — system structure and data flow  
  [docs/architecture.md](./docs/architecture.md "System architecture")
- 🧠 **Analysis Logic** — how failure impact is determined  
  [docs/analysis_logic.md](./docs/analysis_logic.md "Failure analysis logic")

Reference:
- 📖 **Glossary** — project-specific terminology  
  [docs/glossary.md](./docs/glossary.md "Terminology reference")
- ⚠️ **Limitations** — explicit and intentional constraints  
  [docs/limitations.md](./docs/limitations.md "Known limitations")

Project & contribution:
- 🗺️ **Roadmap** — current scope and next steps  
  [docs/roadmap.md](./docs/roadmap.md "Project roadmap")
- 🧭 **Execution Plan** — development phases and priorities  
  [docs/execution_plan.md](./docs/execution_plan.md "Execution plan")
- 🔀 **Git Workflow** — contribution process and rules  
  [docs/git_workflow.md](./docs/git_workflow.md "Git workflow")
- 🧑‍💻 **Contributing** — how to contribute  
  [docs/contributing.md](./docs/contributing.md "Contribution guidelines")

📂 Full documentation index:  
[docs/index.md](./docs/index.md "Complete documentation index")

---

## Contributing

Before making any changes, read the Git workflow:  
[git_workflow.md](./git_workflow.md "Detailed Git Workflow docs")

---

## Project Status

Prototype built during a hackathon.
Logic and scope may evolve.

---

## Contributors
Built during the [BeachHack](https://beachhack.in "Beach Hack hackthon website") Hackathon.

<p align="center">
  <a href="https://github.com/Samurai-beachhack/zerohour/graphs/contributors">
    <img
      src="https://contrib.rocks/image?repo=Samurai-beachhack/zerohour&size=80&columns=10&bg=transparent"
      alt="Contributors"
    />
  </a>
</p>


