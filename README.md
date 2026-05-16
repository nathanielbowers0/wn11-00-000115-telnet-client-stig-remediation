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

<img width="1000" alt="Baseline Compliance" src="PASTE_GITHUB_LINK_HERE" />

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

<img width="1000" alt="Local Validation" src="PASTE_GITHUB_LINK_HERE" />

---

# Phase 3 — Vulnerability Introduction

The Telnet Client feature was intentionally enabled using PowerShell to simulate a compliance failure.

## Command

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName TelnetClient
```

This intentionally created a non-compliant state.

<img width="1000" alt="Vulnerability Introduced" src="PASTE_GITHUB_LINK_HERE" />

---

# Phase 4 — Tenable Detection

A new Tenable compliance scan was launched after enabling Telnet Client.

Tenable successfully detected the STIG violation.

## Result

Failed

<img width="1000" alt="Tenable Failed Scan" src="PASTE_GITHUB_LINK_HERE" />

---

# Phase 5 — Manual GUI Remediation

The vulnerability was manually remediated through Windows Features.

## Steps

1. Opened "Turn Windows features on or off"
2. Located "Telnet Client"
3. Unchecked the feature
4. Applied changes

<img width="1000" alt="GUI Remediation" src="PASTE_GITHUB_LINK_HERE" />

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

<img width="1000" alt="Remediation Validation" src="PASTE_GITHUB_LINK_HERE" />

---

# Phase 7 — Final Compliance Validation

A final Tenable compliance scan confirmed that the system returned to a compliant state.

## Result

Passed

<img width="1000" alt="Final Compliance Validation" src="PASTE_GITHUB_LINK_HERE" />

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
