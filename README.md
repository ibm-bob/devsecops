# IBM Bob Premium Package for DevSecOps

Bring enterprise DevSecOps directly into Bob. **IBM Bob Premium Package for DevSecOps** extends [IBM Bob](https://bob.ibm.com) with AI-assisted security workflows surfaced natively in Bob chat — scan source code for vulnerabilities, analyze supply chain risks, detect secrets and misconfigurations, remediate findings with agent-driven fix loops, and monitor your project's security posture — all without leaving Bob.

<details>
<summary>Table of Contents</summary>

- [Workflows at a Glance](#workflows-at-a-glance)
- [Why Bob Premium Package for DevSecOps](#why-bob-premium-package-for-devsecops)
- [Key Capabilities](#key-capabilities)
    - [Supply Chain Analysis](#supply-chain-analysis)
    - [SAST and Misconfiguration Scanning](#sast-and-misconfiguration-scanning)
    - [Secret Detection](#secret-detection)
    - [Light Security Scan](#light-security-scan)
    - [Deep Security Scan](#deep-security-scan)
    - [AI-Assisted Remediation](#ai-assisted-remediation)
    - [Ansible Automation](#ansible-automation)
    - [Terraform IaC](#terraform-iac)
- [Getting Started](#getting-started)
- [Requirements](#requirements)
- [Screenshots](#screenshots)
- [FAQ](#faq)
- [Feedback and Support](#feedback-and-support)
- [License](#license)

</details>

## Workflows at a Glance

| Workflow                                                                 | What it does                                                                                    |
| ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| [**Supply Chain Analysis**](#supply-chain-analysis)                      | Score dependencies against CVEs, popularity, and release age across npm, PyPI, Maven, and Go    |
| [**SAST & Misconfiguration Scanning**](#sast-and-misconfiguration-scanning) | Run Trivy, Semgrep, and KICS against source, IaC, and container definitions                  |
| [**Secret Detection**](#secret-detection)                                | Detect hardcoded credentials, API keys, and secrets before they reach production                |
| [**Light Security Scan**](#light-security-scan)                          | 4-stage AI-driven scan: discover project, map attack surface, generate and validate hypotheses  |
| [**Deep Security Scan**](#deep-security-scan)                            | Per-file pipeline with multi-round triage; experimental and cost-intensive                      |
| [**AI-Assisted Remediation**](#ai-assisted-remediation)                  | Agent-driven fix loop that patches vulnerable dependencies and verifies the build               |
| [**Ansible Automation**](#ansible-automation)                            | Write, validate, and convert Ansible playbooks and roles with Bob as an AI pair programmer      |
| [**Terraform IaC**](#terraform-iac)                                      | Scan Terraform configurations for misconfigurations and policy violations using KICS            |

![DevSecOps workflows in chat][screens-flows]

[screens-flows]: ./assets/screenshots/flows.png "DevSecOps workflows in chat"

## Why Bob Premium Package for DevSecOps

Securing applications is more than running a scanner. It requires understanding the attack surface of each project, reasoning about real exploitability, prioritizing findings by risk, and applying fixes that do not break the build. Generic scanners report noise; manual triage is slow; CVE feeds alone do not tell you which findings matter.

Bob Premium Package for DevSecOps brings that expertise directly into Bob as guided, multi-step workflows. Each workflow encodes proven security engineering practices into discrete, repeatable steps that run inside the editor where the code lives — combining static tools, supply chain data, and AI reasoning into a single, coherent experience.

## Key Capabilities

### Supply Chain Analysis

Scores project dependencies against vulnerability databases, package popularity, and release age to surface risky packages before they reach production.

The scanner:

1. **Parses manifests** — reads `package.json`, `requirements.txt`, `pom.xml`, `build.gradle`, `go.mod`, and other dependency files.
2. **Queries CVE data** — checks each dependency against known CVEs with CVSS scores and affected version ranges.
3. **Scores packages** — combines vulnerability data, download popularity, and time since last release into a per-package risk score.
4. **Surfaces findings** — results appear in Bob's Findings panel with severity, fix guidance, and a **Fix with Bob** action.
5. **Agent fix loop** — a Bob workflow updates or replaces vulnerable packages and verifies the project still builds and tests pass.

Supports npm, PyPI, Maven, and Go modules. Runs automatically when a manifest file is saved and on workspace open.

### SAST and Misconfiguration Scanning

Integrates industry-standard static analysis and infrastructure-as-code scanners with Bob's Findings panel.

- **Trivy** — comprehensive scanner for vulnerabilities, misconfigurations, and secrets in source, containers, and IaC.
- **Semgrep (Opengrep)** — fast, rule-based static analysis for code patterns and known vulnerability classes.
- **KICS** — infrastructure-as-code scanner for Terraform, Kubernetes, Dockerfile, and Ansible misconfigurations.

Scans run automatically on file save and can be triggered manually. All findings are colour-coded by severity and link to the exact source location. **Agent Guard** intercepts files that Bob's agent is about to write and scans them for newly introduced issues before the change lands.

### Secret Detection

Detects hardcoded credentials, API keys, tokens, and other secrets in source code.

- Runs as part of Trivy's `secret` scan type.
- Built-in regex patterns catch common patterns (passwords in config, AWS keys, private keys, connection strings).
- Findings include the exact file and line, a sanitized preview, and remediation guidance.
- Works alongside `.gitignore` exclusions to avoid scanning vendored or generated files.

### Light Security Scan

An agent-driven, 4-stage security scan that examines source code and saves findings for review in the Security Dashboard.

The workflow:

1. **Getting started and repository selection** — when the workspace contains multiple Git repositories, you choose which one to scan; a single repository is selected automatically.
2. **Discover project** — the AI subagent reads the codebase and produces a structured project summary covering tech stack, entry points, trust boundaries, and data flows. Results are cached per project fingerprint.
3. **Map attack surface** — a higher-capability subagent identifies attack vectors, privilege boundaries, external interfaces, and security-relevant data handling.
4. **Generate security hypotheses** — the AI produces a prioritized set of security hypotheses: specific, testable claims about potential vulnerabilities.
5. **Validate hypotheses** — up to four validators run concurrently, each examining evidence for one hypothesis and producing structured findings with source locations, severity, confidence, and remediation steps.

Each completed scan stores findings under `~/.bob/security-watch/findings/v1/`, isolated by project and branch. Scans can be paused and resumed; completed validations are reused when inputs and extension version match.

### Deep Security Scan

An experimental per-file pipeline that inventories every file in the repository and then applies multi-round security triage to each one. More thorough than the light scan but significantly more expensive in tokens and time.

Start with `/deep-security-scan` in a fresh Bob task.

### AI-Assisted Remediation

Launches a Bob subtask that resolves security findings found by the scanner.

The agent:

1. **Reads the finding** — understands the affected package, CVE, and severity.
2. **Identifies the fix** — determines whether to upgrade, replace, or patch the dependency.
3. **Applies the change** — modifies the manifest and lockfile.
4. **Verifies the build** — runs the project's build and test commands to confirm nothing is broken.
5. **Reports the outcome** — summarizes what changed, which CVEs were resolved, and any remaining issues.

### Ansible Automation

Write, validate, and convert Ansible playbooks and roles with Bob as an AI pair programmer. Coming soon.

### Terraform IaC

Scan Terraform configurations for misconfigurations and policy violations. Coming soon.

---

## Getting Started

1. Install [IBM Bob](https://bob.ibm.com).
2. Subscribe to IBM Bob Premium Package for DevSecOps.
3. Open your project or workspace in Bob.
4. Click **Start Workflow**, or type any of the workflow names below in the Bob prompt to launch it directly:
   - `Light Security Scan`
   - `Deep Security Scan`
   - `Supply Chain Analysis`
   - `SAST Scan`
   - `Secret Detection`

> **Tip:** You can also launch scans instantly using slash commands:
> - `/light-security-scan` — start a fresh light scan in the current workspace.
> - `/deep-security-scan` — start a deep per-file scan.

## Requirements

- [IBM Bob](https://bob.ibm.com)
- IBM Bob Premium Package for DevSecOps subscription

## Screenshots

![Security findings in the Findings panel][screens-findings]

[screens-findings]: ./assets/screenshots/findings-panel.png "Security findings in the Findings panel"

![Security Dashboard showing scan results][screens-dashboard]

[screens-dashboard]: ./assets/screenshots/security-dashboard.png "Security Dashboard showing scan results"

![Agent-driven remediation in chat][screens-remediation]

[screens-remediation]: ./assets/screenshots/remediation.png "Agent-driven remediation in chat"

## FAQ

### Does this extension work by itself?

No. This add-on extends [IBM Bob](https://bob.ibm.com) and requires it as a dependency.

### What languages and ecosystems are supported?

The scanners cover a broad range of languages and ecosystems:

- **SAST**: any language supported by Trivy, Semgrep, and KICS (JavaScript, TypeScript, Python, Java, Go, Ruby, C/C++, Terraform, Kubernetes, Dockerfile, Ansible, and more).
- **Supply chain**: npm/Yarn, PyPI, Maven/Gradle, Go modules.
- **Secrets**: any text file in the repository.

### Do I need to install Trivy, Semgrep, or KICS separately?

Not for the hosted backend. By default the extension routes scan requests to a hosted backend that runs the scanners. Set `bobDevSecOps.security.scannersUseLocal: true` in settings to run scanners locally, in which case they must be installed and available in your `PATH`.

### Can I pause and resume a scan?

Yes, for the light security scan. Press **Stop** during any stage after Getting started. The chat will say `Scan paused. Reopen this task to resume.` To resume, switch to another task and then reopen the paused one from history, then click **Resume scan** on the card. Pauses expire after seven days.

### Where are scan results stored?

Completed scan findings are stored locally under `~/.bob/security-watch/findings/v1/`, organized by project and branch. They are retained for 90 days. The Security Dashboard reads these files directly.

### Does the scanner modify my source code?

No. The light and deep scan workflows are read-only. They use an immutable Git snapshot of your repository and never write to the workspace. Only the AI-Assisted Remediation workflow modifies files, and only after your confirmation.

## Feedback and Support

- Issues: https://github.com/IBM/ibm-bob/issues
- Source: https://github.com/IBM/ibm-bob-devsecops

## License

See [`LICENSE`](LICENSE).
