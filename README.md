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
/attack-surface-scan              — map attack surface and validate security findings
/file-sweep-scan                  — per-file scan, thorough but higher token cost
/supply-chain-fix-vulnerabilities — fix all supply chain vulnerabilities
/ansible-automation               — Ansible skill
/terraform-this                   — Terraform skill
```

## Requirements

- [IBM Bob](https://bob.ibm.com)
- IBM Bob Premium Package for DevSecOps subscription


## Feedback and Support

- Issues: https://github.com/IBM/ibm-bob/issues
- Source: https://github.com/IBM/ibm-bob-devsecops

## License

See [`LICENSE`](LICENSE).
