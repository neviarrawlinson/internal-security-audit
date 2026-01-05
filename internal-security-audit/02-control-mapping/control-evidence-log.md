# Control Evidence Log

This log documents the audit team's review of specific controls mapped in the NIST CSF. It includes references to documentation, system screenshots, interviews, and testing activities. This serves as traceable evidence for audit conclusions and findings.

| Control ID | NIST Function | Description | Evidence Source | Status | Notes |
|------------|----------------|-------------|------------------|--------|-------|
| AC-2       | Protect        | Account Management | Active Directory config export | ✅ Pass | MFA enforced, accounts reviewed quarterly |
| CM-6       | Protect        | Configuration Management | Change logs, Jira tickets | ❌ Fail | No documented baseline configuration |
| IR-4       | Respond        | Incident Handling | IR Playbook v2.1, On-call schedule | ✅ Pass | Incident response tested quarterly |
| SI-4       | Detect         | Monitoring and Logging | Log aggregation config, Splunk dashboards | ⚠️ Partial | Logs collected but no alerting enabled |
| RA-5       | Identify       | Vulnerability Scanning | Nessus scan results, patch reports | ✅ Pass | Weekly scans, patch SLAs met |

Legend: ✅ Pass | ❌ Fail | ⚠️ Partial

---

_Next: Begin hands-on validation in [03-fieldwork](../03-fieldwork/)._
