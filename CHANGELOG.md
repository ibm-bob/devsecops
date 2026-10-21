# Changelog

All notable changes to the **IBM Bob Premium Package for DevSecOps** will be documented in this file.

## [1.0.0] — Initial Release

First public release of IBM Bob Premium Package for DevSecOps for [IBM Bob](https://bob.ibm.com).

### Highlights

- **Scan all code** — Run SAST and supply chain scans across your repository using Trivy, Opengrep, and KICS; all issues surface in Bob Findings.
- **Fix supply chain vulnerabilities** — Agent-driven fix loop that patches vulnerable dependencies and verifies the build.
- **Attack-surface scan** — AI-driven workflow that maps your application's attack surface and validates evidence-backed security findings across the full repository or only what changed.
- **File-sweep scan** — Experimental per-file security triage pipeline; inspects every source file and verifies each possible issue through successive passes.
- **Ansible automation** — Develop, review, and refactor playbooks, roles, and collections following Ansible best practices, validated by lint and idempotence checks.
- **Terraform** — Develop, review, and refactor Terraform HCL configurations following HashiCorp best practices, validated by `terraform test` and mock providers.
- **Security dashboard** — Persistent, browsable view of all completed scan results organized by project and branch.
