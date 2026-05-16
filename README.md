# WN11-00-000115 — Telnet Client STIG Remediation Lab

## Overview

This lab demonstrates the full vulnerability management and remediation lifecycle for the following Windows 11 STIG:

**WN11-00-000115 — The Telnet Client must not be installed on the system**

The lab includes:
- Baseline compliance validation
- Vulnerability introduction
- Tenable compliance detection
- Manual GUI remediation
- PowerShell validation
- Final compliance verification

---

## Environment

- Windows 11 VM
- Tenable Compliance Scanning
- PowerShell
- Windows Features GUI
- Azure Bastion

---

## STIG Information

### STIG ID

WN11-00-000115

### Requirement

The Telnet Client must not be installed on the system.

Telnet is considered insecure because it transmits communications in plaintext and may expose credentials or sensitive system activity.

---

# Phase 1 — Baseline Compliance Validation

An initial Tenable compliance scan confirmed that the system was compliant before introducing the vulnerability.

### Result

Passed

<img width="1064" height="40" alt="01_Baseline_Compliant_STIG_TelnetClient_Passed" src="https://github.com/user-attachments/assets/1393a059-b242-415c-bc22-34ded82ed991" />


---

# Phase 2 — Local Validation of Current State

PowerShell was used to verify that the Telnet Client feature was disabled.

## Command

```powershell
Get-WindowsOptionalFeature -Online -FeatureName TelnetClient
```

## Validation Result

```powershell
State : Disabled
```

<img width="1150" height="466" alt="02_TelnetClient_Manual_Remediation_Validation" src="https://github.com/user-attachments/assets/bd9dd5ff-493c-4540-bdb8-5067ad3235c4" />


---

# Phase 3 — Vulnerability Introduction

The Telnet Client feature was intentionally enabled using PowerShell to simulate a compliance failure.

## Command

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName TelnetClient
```

This intentionally created a non-compliant state.

<img width="1376" height="488" alt="03_TelnetClient_Vulnerability_Introduced_PowerShell" src="https://github.com/user-attachments/assets/133ead8e-e335-495b-bbef-f07b93594455" />


---

# Phase 4 — Tenable Detection

A new Tenable compliance scan was launched after enabling Telnet Client.

Tenable successfully detected the STIG violation.

## Result

Failed

<img width="1043" height="40" alt="04_Tenable_STIG_Failed_TelnetClient" src="https://github.com/user-attachments/assets/bcd70271-433c-4a02-b6a1-9ec547f0450a" />


---

# Phase 5 — Manual GUI Remediation

The vulnerability was manually remediated through Windows Features.

## Steps

1. Opened "Turn Windows features on or off"
2. Located "Telnet Client"
3. Unchecked the feature
4. Applied changes

<img width="878" height="448" alt="05_Manual_GUI_Remediation_TelnetClient" src="https://github.com/user-attachments/assets/001429d1-6c41-4653-9ebd-4918a318679d" />


---

# Phase 6 — PowerShell Validation

PowerShell was used again to validate the remediation.

## Command

```powershell
Get-WindowsOptionalFeature -Online -FeatureName TelnetClient
```

## Validation Result

```powershell
State : Disabled
```

<img width="878" height="448" alt="06_Manual_Remediation_Validation_PowerShell" src="https://github.com/user-attachments/assets/ae543291-5126-46da-a465-1f01d0ac5642" />


---

# Phase 7 — Final Compliance Validation

A final Tenable compliance scan confirmed that the system returned to a compliant state.

## Result

Passed

<img width="1012" height="39" alt="07_Tenable_Compliance_Validation_Passed" src="https://github.com/user-attachments/assets/7084df46-ce8e-41f8-9274-198d5aeee7a1" />


---

# Skills Demonstrated

- Vulnerability Management
- STIG Compliance Auditing
- Windows 11 Hardening
- Tenable Compliance Scanning
- Manual Remediation
- PowerShell Validation
- Compliance Verification
- Endpoint Security
- Security Documentation

---

# Conclusion

This lab demonstrated a complete STIG remediation workflow using Windows 11 and Tenable compliance scanning.

The process included:
- Establishing a compliant baseline
- Introducing a vulnerability
- Detecting the finding with Tenable
- Performing manual remediation
- Validating remediation locally
- Confirming compliance restoration through rescanning

This project provided hands-on experience with compliance auditing, remediation workflows, and endpoint hardening practices commonly used in enterprise cybersecurity environments.
