# Endpoint Security Monitoring

**Program:** Internee.pk  
**Status:** Lab validation completed; final review/documentation in progress  
**Primary platform:** Wazuh  
**Endpoint:** Windows VM with Wazuh agent and Sysmon  
**Manager:** Wazuh 4.14.9 on Ubuntu Server 24.04.5 LTS

## Objective

Implement endpoint monitoring to collect Windows endpoint telemetry, monitor file changes, and raise alerts for a controlled threat-intelligence matching test.

## Lab architecture

- **Wazuh manager/dashboard:** Ubuntu Server VM
- **Endpoint:** Windows VM with Wazuh agent
- **Telemetry:** Windows Security events and Sysmon events
- **File integrity monitoring:** Monitored lab directory
- **Threat-intelligence test:** Local SHA-256 indicator list and custom Wazuh rule

## Implemented components

1. Wazuh manager and dashboard deployment.
2. Windows Wazuh agent enrollment and connectivity verification.
3. Sysmon installation and event collection.
4. Windows Security event collection.
5. File Integrity Monitoring (FIM) validation.
6. Manual SHA-256 indicator list and custom rule validation.

## Documentation

- [Threat Intelligence Integration with Wazuh](./reports/threat-intelligence-integration.md)
- [Custom rules folder notes](./rules/README.md)
- [Evidence folder notes](./evidence/README.md)


## Important scope limitation

The threat-intelligence test uses a manually maintained local indicator list and a harmless test file/hash. It demonstrates the configured matching workflow; it does **not** represent an automated MalwareBazaar feed integration or prove detection of every real-world malware sample.

## Folder guide

- `reports/` — detailed task reports
- `rules/` — custom detection rules or safe examples
- `evidence/` — sanitized screenshots and supporting proof

## References

- [Wazuh documentation](https://documentation.wazuh.com/)
- [Sysmon documentation](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- [MalwareBazaar](https://bazaar.abuse.ch/)
