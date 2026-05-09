# example-javascript-npm

> Find vulnerabilities, trace reachability, and audit open-source risk in your **JavaScript** project.

## About

This repository is a [Bomly](https://bomly.dev) example project for **JavaScript** with **npm**.
Use it to try every Bomly feature — from basic SCA scans to vulnerability audits, reachability analysis, dependency tracing, and policy-driven CI gates.

## Dependency manifests

| File | Role |
|------|------|
| `package.json` | Dependency manifest |
| `package-lock.json` | Dependency manifest |

## Try it with Bomly

### 1. Discover all dependencies

Map your full dependency graph — direct and transitive:

```bash
bomly scan --url https://github.com/bomly-dev/example-javascript-npm
```

### 2. Find vulnerabilities

Enrich packages with CVE data and surface real findings:

```bash
bomly scan --url https://github.com/bomly-dev/example-javascript-npm --enrich --audit
```

### 3. Confirm reachability

Cut alert noise: Bomly traces your call graph to prove which vulnerable code paths
your app actually reaches at runtime.

```bash
bomly scan --url https://github.com/bomly-dev/example-javascript-npm --enrich --reachability
```

### 4. Trace why a dependency exists

Understand every path that pulls `lodash` into your graph:

```bash
bomly explain lodash --url https://github.com/bomly-dev/example-javascript-npm
```

### 5. See what changed between releases

Compare dependency graphs across any two refs — commits, branches, or tags:

```bash
bomly diff \
  --url https://github.com/bomly-dev/example-javascript-npm \
  --base v0.9.0 --head v1.0.0 \
  --enrich
```

### 6. Add a security gate to CI

Fail your pipeline automatically when high-severity vulnerabilities are introduced:

```yaml
# .github/workflows/bomly.yml
name: Bomly Security Scan
on: [push, pull_request]

jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Scan with Bomly
        run: |
          curl -sSfL https://bomly.dev/install.sh | sh
          bomly scan --enrich --audit --fail-on high
```

Made with [Bomly](https://bomly.dev) — open-source SCA for every ecosystem.
