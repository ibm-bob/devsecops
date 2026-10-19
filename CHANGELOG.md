# Changelog

All notable changes to the **Bob DevSecOps Premium Add-On** will be documented in this file.

## [1.0.0] — Initial Release

First public release of the Bob DevSecOps Premium Add-On for [IBM Bob](https://bob.ibm.com).

### Highlights

- **Light Security Scan** — AI-driven, 4-stage workflow covering project discovery, attack surface mapping, hypothesis generation, and hypothesis validation.
- **Deep Security Scan** — Experimental per-file security triage pipeline for exhaustive coverage.
- **Supply Chain Analysis** — Dependency risk scoring against CVEs, package popularity, and release age for npm, PyPI, Maven, and Go modules.
- **SAST & Misconfiguration Scanning** — Integration with Trivy, Semgrep (Opengrep), and KICS surfaced directly in Bob's Findings panel.
- **Secret Detection** — Hardcoded credential and API key detection across all source files.
- **AI-Assisted Remediation** — Agent-driven fix loop that patches vulnerable dependencies and verifies the build.
- **Agent Guard** — Automatic pre-write supply chain scan for files Bob's agent is about to modify.
- **Security Dashboard** — Persistent, browsable view of all completed scan results organized by project and branch.
