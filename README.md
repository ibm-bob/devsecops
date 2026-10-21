# IBM Bob Premium Package for DevSecOps

**IBM Bob Premium Package for DevSecOps** extends [IBM Bob](https://bob.ibm.com) with AI-powered security workflows — scan source code and dependencies, detect secrets, map attack surfaces, fix vulnerabilities, and author Ansible and Terraform with AI, all from inside Bob.

## What's included

| Capability | Description |
|---|---|
| Scan all code | Run SAST and supply chain scans across your repository; all issues surface in Bob Findings |
| Fix supply chain vulnerabilities | Guided workflow that patches all vulnerable dependencies and verifies the build |
| Attack-surface scan | Map your application's attack surface, derive and validate evidence-backed security findings |
| File-sweep scan | Inspect every source file and verify each possible issue through successive passes |
| Ansible automation | Develop, review, and refactor playbooks and roles following Ansible best practices |
| Terraform | Develop, review, and refactor Terraform HCL configurations with `terraform test` validation |
| Security dashboard | Summary of all issues identified by scanning your code |

## Getting Started

1. Install [IBM Bob](https://bob.ibm.com).
2. Subscribe to IBM Bob Premium Package for DevSecOps.
3. Open your project in Bob and click **Open Welcome Page** to launch any workflow or scan.

You can also start workflows directly from the Bob prompt:

```
/light-security-scan   — attack-surface scan (recommended starting point)
/deep-security-scan    — file-sweep scan (thorough, higher token cost)
/ansible-automation    — Ansible skill
/terraform-this        — Terraform skill
```

## Requirements

- [IBM Bob](https://bob.ibm.com)
- IBM Bob Premium Package for DevSecOps subscription

## FAQ

**Does this extension work by itself?**
No. It extends [IBM Bob](https://bob.ibm.com) and requires it as a dependency.

**What languages and package managers are supported?**
- SAST: JavaScript, TypeScript, Python, Java, Go, Ruby, C/C++, Terraform, Kubernetes, Dockerfile, Ansible, and more (via Trivy, Semgrep, and KICS).
- Supply chain: npm/Yarn, PyPI, Maven/Gradle, Go modules.
- Secrets: any text file in the repository.

**Do I need to install Trivy, Semgrep, or KICS?**
Not by default — scans are routed to a hosted backend. Set `bobDevSecOps.security.scannersUseLocal: true` to run scanners locally, in which case they must be installed and available on your `PATH`.

**Can I pause and resume a scan?**
Yes. Press **Stop** during the attack-surface scan, then reopen the task from history and click **Resume scan**. Pauses expire after seven days.

**Where are scan results stored?**
Locally under `~/.bob/security-watch/findings/v1/`, organized by project and branch, retained for 90 days.

**Does the scanner modify my source code?**
No. Scan workflows are read-only. Only the Fix Supply Chain Vulnerabilities workflow modifies files, and only after your confirmation.

## Feedback and Support

- Issues: https://github.com/IBM/ibm-bob/issues
- Source: https://github.com/IBM/ibm-bob-devsecops

## License

See [`LICENSE`](LICENSE).
