# Projects with Internee.pk

A central portfolio repository for documenting and showcasing projects completed during the Internee.pk program. Each task has its own directory with a dedicated README, reports, evidence, and configuration/code where appropriate.

## Repository structure

```text
Project-with-Internee.pk/
├── README.md
├── TASK-REPORT-TEMPLATE.md
└── Endpoint-Security-Monitoring/
    ├── README.md
    ├── reports/
    │   └── threat-intelligence-integration.md
    ├── rules/
    │   └── README.md
    └── evidence/
        └── README.md
```

## Projects

| Task | Description | Status |
|---|---|---|
| [Endpoint Security Monitoring](./Endpoint-Security-Monitoring/README.md) | Wazuh endpoint monitoring, Sysmon and Windows Security logs, file integrity monitoring (FIM), and a manually maintained SHA-256 threat-intelligence list with a custom detection rule. | In progress / lab validation completed |

> Update the status above when you have completed and reviewed the task.

## How to add another task

1. Create a new directory at the repository root using a clear name, for example `Network-Traffic-Analysis/`.
2. Add a `README.md` inside it using `TASK-REPORT-TEMPLATE.md` as the starting point.
3. Add task-specific folders only when needed, such as `reports/`, `evidence/`, `configs/`, `scripts/`, or `screenshots/`.
4. Link the new task from the Projects table above.
5. Remove secrets, credentials, private IPs where appropriate, client data, and other sensitive information before publishing.

## Evidence and safety

- Use screenshots that demonstrate your own lab work.
- Redact passwords, tokens, email addresses, public IPs if sensitive, and any personal or client information.
- Do not upload malware samples, private keys, credentials, or confidential logs.
- For security testing, document authorization and keep testing within your own lab or explicitly authorized systems.
