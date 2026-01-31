# Usage

This document describes how to run ZeroHour from the CLI.

---

## Basic Usage

Analyze the current directory:

```bash
./zerohour analyze
```

## Analyze a Specific Directory

```bash
./zerohour analyze -C path/to/project
```

## Output Modes

Plain output (no boxed UI):

```bash
./zerohour analyze --no-box
```
## Result Limits

Default behavior:

* Outputs Top 10 issues

Planned / Experimental

```bash
./zerohour analyze --top 10
./zerohour analyze --all
```
* --top <n>: limit output to top n prioritized issues
* --all: output full prioritized list instead of Top 10

## Fix Suggestions

Planned / Experimental

```bash
./zerohour analyze --fix
```
* Generates AI-assisted remediation suggestions
* Fixes are advisory and require human review

## Output Formats

Planned / Experimental

```bash
./zerohour analyze --json
```

* Outputs structured JSON instead of human-readable text
* Intended for automation and integrations

## SDK Usage

Planned / Experimental

```bash
./zerohour analyze --sdk
```

* Executes analysis through the ZeroHour SDK
* Intended for CI/CD and embedded workflows

## Common Alternatives

```bash
npm run analyze
npx zerohour analyze
npm link && zerohour analyze

```

## Notes

* Experimental flags may change or be removed
* Stable behavior is limited to default CLI usage
* Use experimental features with caution
