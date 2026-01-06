# Test Scripts – Fieldwork Phase

This file contains fieldwork test scripts and procedures used to validate the effectiveness of internal security controls. Each script is tied to a NIST Cybersecurity Framework (CSF) function and specific audit objectives.

## Test 1: Validate Multi-Factor Authentication (MFA)

NIST Function: Protect

Control Objective: Ensure MFA is enabled for administrative access

Test Command (AWS):
Use AWS CLI to list MFA devices assigned to an admin user. Example command:
aws iam list-mfa-devices --user-name admin_user

Expected Result: At least one MFA device is associated with the account

## Test 2: Confirm Password Policy Settings

NIST Function: Protect

Control Objective: Verify compliance with password complexity and expiration rules

Test Command (Linux):
View password policy settings using the command:
cat /etc/login.defs | grep PASS

Expected Result: PASS_MAX_DAYS, PASS_MIN_DAYS, and PASS_MIN_LEN reflect policy requirements

## Test 3: Scan for Open Ports on Internal Server

NIST Function: Detect

Control Objective: Ensure only approved ports are open on critical infrastructure

Test Command (Nmap):
Run an internal port scan with:
nmap -Pn -p- 10.0.0.25

Expected Result: Only documented/authorized ports are open

## Test 4: Review User Authentication Logs

NIST Function: Detect

Control Objective: Identify anomalies or brute-force attempts

Test Command (Linux):
Review failed login attempts by running:
grep "Failed password" /var/log/auth.log

Expected Result: No excessive failed logins or repeated attempts from unknown IPs

## Test 5: Check Role-Based Access Control (RBAC) Assignments

NIST Function: Protect

Control Objective: Validate that user access aligns with job roles

Test Command (Azure AD):
Use Azure CLI to list user group memberships:
az ad user get-member-groups --id user@company.com

Expected Result: User is only in groups or roles necessary for their job function

## Test 6: Backup Validation

NIST Function: Recover

Control Objective: Ensure backups are recent, successful, and restorable

Test Procedure:

Access backup logs (Veeam, AWS Backup, Azure Recovery Services)

Check timestamp of last successful backup

Perform test restore in a staging environment

Expected Result: Backup is recent and restoration completes without error

## Test 7: Endpoint Protection Status

NIST Function: Protect / Detect

Control Objective: Ensure anti-malware is running and updated

Test Command (Windows):
Run PowerShell:
Get-MpComputerStatus

Expected Result: Real-time protection is on and definitions are up to date

## Test 8: Patch Compliance Check

NIST Function: Protect

Control Objective: Confirm systems are updated with latest security patches

Test Command (Linux):
To list available updates:
sudo apt list --upgradable

Expected Result: No critical patches should be pending

## Test 9: Configuration Drift Detection

NIST Function: Detect

Control Objective: Identify unauthorized or unexpected system changes

Test Tools:
Use osquery, Tripwire, AWS Config, or similar tools to detect configuration drift

Expected Result: No unexpected deviations from the approved baseline

## Test 10: Log Retention & Integrity

NIST Function: Detect

Control Objective: Verify logs are collected, protected, and retained

Test Procedure:

Ensure logs are forwarded to a SIEM (e.g., Splunk, ELK)

Validate log rotation and tamper-proof configuration

Expected Result: Logs are available, complete, and protected from modification

## Summary

Each test helps validate the effectiveness of internal security controls. Results feed into the audit findings and remediation planning.

Next: Compile audit findings and risk ratings in 04-findings-report.