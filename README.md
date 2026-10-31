# Sanjeev-Okta-Workforce-IAM-Lab

Hands-on Okta Workforce Identity and Access Management lab covering SAML SSO, RBAC, MFA, JML, group rules, access reviews, and exception access.

## Project Overview

This project simulates a workforce IAM environment for a mock Canadian financial services company.

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

A mock company, MapleTech Financial, was created with users across HR, Finance, IT, and Contractor teams.

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
