# Sanjeev-Okta-Workforce-IAM-Lab

![Okta](https://img.shields.io/badge/Okta-IAM-007DC1?style=for-the-badge&logo=okta&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-Automation-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Integration-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SAML](https://img.shields.io/badge/SAML%202.0-SSO-FF6B00?style=for-the-badge)
![MFA](https://img.shields.io/badge/Adaptive%20MFA-Zero%20Trust-00A86B?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**Author:** Sanjeev Shrestha | Dallas–Fort Worth Area, TX (Shrestha Financial)  
**Target Roles:** IAM Engineer / Identity Engineer / Okta Administrator / Entra ID Engineer (2027)  
**Certification Focus:** Preparing for Okta Certified Professional (OCP)  
**Environment:** Okta Developer Tenant (*.okta.com - redacted) 

## Project Overview

This project simulates a workforce IAM environment for a mock Dallas based financial services company.

The goal is to demonstrate practical IAM administration and governance skills using Okta, including:

- User and group administration
- Role-Based Access Control (RBAC)
- SAML 2.0 Single Sign-On
- Real SAML federation testing
- MFA and app sign-in policies
- Joiner, Mover, Leaver lifecycle
- Attribute-based group rules
- Access reviews
- Temporary exception access

## Architecture Diagram

[View IAM architecture diagram](diagrams/iam-architecture.md)

## Lab Scenario

A mock company, Shrestha Financial, was created with users across HR, Finance, IT, and Contractor teams.

Access was assigned using Okta groups instead of direct user assignment.

## Access Model

| User | Group | Application |
|---|---|---|
| Omar Hassan | HR-Team | HR Portal |
| Sarah Miller | Finance-Team | Finance Portal |
| Alex Chen | IT-Admins | IT Admin Portal |
| Mark Wilson | Contractors | Contractor Portal |

## Key Labs

### 1. RBAC Model

Configured users, groups, and applications using group-based access assignment.

[View RBAC documentation](docs/rbac-model.md)

### 2. SAML SSO Integration

Configured and tested a real SAML 2.0 integration using Okta as the Identity Provider and a public test Service Provider.

[View SAML SSO documentation](docs/saml-sso-integration.md)

### 3. MFA Policy

Created an app sign-in policy requiring stronger authentication for privileged admin access.

[View MFA policy documentation](docs/mfa-policy.md)

### 4. JML Lifecycle

Simulated joiner, mover, and leaver workflows using users, groups, department attributes, and account deactivation.

[View JML documentation](docs/jml-lifecycle.md)

### 5. Access Governance

Simulated access reviews, privileged access review, contractor access control, and temporary exception access.

[View access governance documentation](docs/access-governance.md)

## Tools and Concepts Used

- Okta Workforce Identity
- SAML 2.0
- Okta Group Rules
- Okta Authentication Policies
- RBAC
- MFA
- JML lifecycle
- Access reviews
- Exception access
- Least privilege
- Identity governance concepts

## Project Outcome

This lab demonstrates practical IAM skills across authentication, authorization, lifecycle management, access governance, and SSO federation.
## Original Repository & Credits
This hands-on lab series was adapted and built upon the foundational framework provided by [SuhaibAN/okta-workforce-iam-lab] (https://github.com/SuhaibAN/okta-workforce-iam-lab). Full original references can be found in [REFERENCE.md](REFERENCE.md).
