# Coding Agent Sandbox Policy

Policy-as-code for AI coding agents touching files, networks, and secrets.

> Version: 1.0.0 | License: MIT | Status: production-oriented v1 foundation

## Problem

Coding agents interact with legacy IDEs, terminals, package managers, and secrets that were not designed for autonomous behavior.

## What this project solves

A sandbox policy checker that validates file write roots, network rules, secret exposure controls, and command approval boundaries.

Coding Agent Sandbox Policy ships as a small, dependency-free CLI and library. It validates a domain-specific JSON packet, emits actionable findings, and gives contributors a concrete surface for adding adapters, richer checks, schemas, and integrations.

## Who it is for

Developer tools teams, security engineers, open-source maintainers.

## Quick start

```bash
npm test
npm start -- sample
```

Analyze your own packet:

```bash
coding-agent-sandbox-policy ./packet.json
```

Or pipe JSON:

```bash
cat packet.json | node src/cli.js
```

## Example packet

```json
{
  "sandbox": {
    "writableRoots": [
      "./src"
    ],
    "network": "restricted"
  },
  "secrets": {
    "envAllowed": false,
    "vaultProxy": true
  },
  "commands": {
    "destructiveRequireApproval": true,
    "packageInstallRequireApproval": true
  }
}
```

## Library usage

```js
const { analyze } = require("./src/index.js");

const report = analyze({
  "sandbox": {
    "writableRoots": [
      "./src"
    ],
    "network": "restricted"
  },
  "secrets": {
    "envAllowed": false,
    "vaultProxy": true
  },
  "commands": {
    "destructiveRequireApproval": true,
    "packageInstallRequireApproval": true
  }
});
console.log(report.summary);
```

## v1 behavior

- Validates required fields for the domain packet.
- Scores readiness from 0 to 100.
- Reports missing or weak governance evidence.
- Suggests next actions and contributor extension points.
- Runs fully offline with no API keys and no network access.

## Contribution map

Good first contributions:

- Add IDE adapters.
- Add policy test suites.
- Add command risk classifiers.
- Add secret scanners.

Larger contributions:

- Add a JSON Schema and compatibility tests.
- Build import/export adapters for popular AI frameworks.
- Add real-world fixtures from public, non-sensitive examples.
- Improve scoring with transparent, documented heuristics.

## Project principles

- Human agency over blind automation.
- Open standards over vendor lock-in.
- Auditable decisions over hidden magic.
- Privacy and safety as design constraints, not release notes.

## GitHub Pages

The marketing site lives in `site/index.html`. Enable GitHub Pages from the `site` folder or use the included Pages workflow after publishing.

## Security

This project does not process secrets by default. If you build adapters that touch production systems, keep least privilege, explicit consent, and auditable logs in the design.
