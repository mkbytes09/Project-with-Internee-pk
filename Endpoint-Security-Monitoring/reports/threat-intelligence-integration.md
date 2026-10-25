# Threat Intelligence Integration with Wazuh

**Program:** Internee.pk  
**Task:** Endpoint Security Monitoring  
**Status:** Controlled lab validation completed  
**Wazuh version:** 4.14.9  
**Manager OS:** Ubuntu Server 24.04.5 LTS  
**Endpoint:** Windows VM with Wazuh agent and Sysmon

## 1. Objective

Configure Wazuh to compare file hashes observed by File Integrity Monitoring (FIM) against a local SHA-256 indicator list and generate a high-severity alert when a matching indicator is observed.

## 2. Scope and safety

All validation was performed in a controlled lab. A harmless test file and its hash were used to test the matching workflow. No malware sample was downloaded or executed.

This implementation uses a manually maintained local indicator list. It is not an automated MalwareBazaar feed or a complete malware-detection solution.

## 3. Components

- Wazuh manager and dashboard
- Windows Wazuh agent
- File Integrity Monitoring (FIM)
- Local SHA-256 indicator list: `/var/ossec/etc/lists/malware-sha256`
- Custom Wazuh rules: `/var/ossec/etc/rules/local_rules.xml`
- Custom rule ID: `100500`

## 4. Implementation summary

### 4.1 Create the local indicator list

A local list was created at:

```text
/var/ossec/etc/lists/malware-sha256
```

The list stores SHA-256 values with labels. Only use indicators from sources you trust, and record the source and date collected in your own working notes. Do not include a malware binary in this repository.

### 4.2 Register the list

The list was registered in the Wazuh configuration so the rule engine could reference it. Configuration changes should be made carefully, preserving existing configuration sections and avoiding duplicate top-level elements.

### 4.3 Add a custom detection rule

A custom rule with ID `100500` was added to match a FIM file-addition event against the local hash list. The rule is configured to emit a high-severity alert and label it with threat-intelligence-related groups.

Before publishing your actual configuration, review it for internal details and confirm that the syntax is compatible with the Wazuh version in use.

### 4.4 Validate the rule

The Wazuh analysis configuration was tested and the manager restarted. The Events view was then searched for rule ID `100500`. The controlled test produced an alert associated with the custom rule.

## 5. Results

| Validation | Result |
|---|---|
| Wazuh manager configuration test | Passed according to the local validation performed |
| Wazuh manager service | Running after restart |
| FIM event collection | Verified |
| Custom rule `100500` alert | Observed in Wazuh Events |
| Real malware execution | Not performed |

## 6. Evidence to attach

Place sanitized screenshots in the task's `evidence/` directory and link them below. Use filenames that describe what each screenshot proves.

- `../evidence/01-wazuh-agent-active.png` — Active Windows agent
- `../evidence/02-sysmon-event.png` — Sysmon event visible in Wazuh
- `../evidence/03-fim-sha256-event.png` — FIM event with a SHA-256 field

## 7. Limitations

- Indicators are maintained manually; feed updates are not automated.
- A matching test hash validates the configured workflow, not the detection of every malware family.
- Detection depends on the FIM event type, field mapping, rule logic, and indicator-list format.
- A production deployment would require a controlled update process, indicator provenance and expiration, testing for false positives, and monitoring of rule performance.

## 8. Future improvements

1. Automate indicator updates only after validating the source and format.
2. Add documented tests for file additions and modifications.
3. Test known benign hashes and controlled matching/non-matching cases.
4. Record indicator source, date collected, confidence, and expiration where applicable.
5. Review alert quality and tune the rule to reduce false positives.

## 9. Conclusion

This lab connected Wazuh FIM telemetry with a local SHA-256 indicator list and demonstrated an alerting workflow using a custom rule. The result is a foundation for further threat-intelligence enrichment, not a complete or automated malware-detection service.

## References

- [Wazuh documentation](https://documentation.wazuh.com/)
- [Wazuh ruleset documentation](https://documentation.wazuh.com/current/user-manual/ruleset/index.html)
- [MalwareBazaar](https://bazaar.abuse.ch/)
