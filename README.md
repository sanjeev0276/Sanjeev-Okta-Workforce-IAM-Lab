# Okta-Workforce-IAM-Lab
![Okta](https://img.shields.io/badge/Okta-IAM-007DC1?style=for-the-badge&logo=okta&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Integration-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SAML](https://img.shields.io/badge/SAML%202.0-SSO-FF6B00?style=for-the-badge)
![MFA](https://img.shields.io/badge/Adaptive%20MFA-Zero%20Trust-00A86B?style=for-the-badge)
![RBAC](https://img.shields.io/badge/RBAC-Least%20Privilege-0A2A5A?style=for-the-badge&logo=shield&logoColor=white)
![JML](https://img.shields.io/badge/JML-Joiner%20Mover%20Leaver-1A5D1A?style=for-the-badge&logo=workos&logoColor=white)
![Governance](https://img.shields.io/badge/Access%20Review-Governance-8B0000?style=for-the-badge&logo=security&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**Author:** Sanjeev Shrestha | Dallas–Fort Worth Area, TX (Shrestha Technologies)  
**Target Roles:** IAM Engineer / Identity Engineer / Okta Administrator / Entra ID Engineer (2027)  
**Certification Focus:** Preparing for Okta Certified Professional (OCP)  
**Environment:** Okta Developer Tenant (*.okta.com - redacted) 

## 5 Labs Architecture Overview
 ![Architecture_Overview](Overall_Architecture_Diagram.png)


## Quick Navigation and Lab Execution Status
<a id="lab-execution-status"></a>
| Lab       | Focus Area                                | Status    | Jump to Lab                                                                  |
|-----------|-------------------------------------------|-----------|------------------------------------------------------------------------------|
| **Lab 1** | RBAC Model | Completed | [Go to Lab 1](#lab-1-RBAC-Model)                       |
| **Lab 2** | SAML SSO Integration    | Completed | [Go to Lab 2](#lab-2-SAML-SSO-Integration) |
| **Lab 3** | MFA Policy | Completed | [Go to Lab 3](#lab-3-MFA-Policy)               |
| **Lab 4** | JML Lifecycle          | Completed | [Go to Lab 4](#lab-4-JML-Lifecycle)                        |
| **Lab 5** | Access Governance        | Completed | [Go to Lab 5](#lab-5-Access-Governance)        |


---
## Executive Summary and Business Impact

Implemented an end-to-end IAM environment using Okta, RBAC, SAML 2.0 federation, Adaptive MFA, and automated Joiner-Mover-Leaver lifecycle with access governance across five hands-on labs.

* **RBAC Model (Lab 1):** Core Okta Developer Tenant *.okta.com, Groups Finance-Team, HR-Team, IT-Admins, Contractors, Finance-Portal-Temporary-Access, Principle Least Privilege Access, no direct app assignments.
* **SAML SSO Integration (Lab 2):** SAML 2.0 federation IdP Okta, SP Apps Finance Portal, HR Portal, IT Admin Portal, SAML ACS URL, Single Sign-On via group assignment.
* **MFA Policy (Lab 3):** High Risk Admin Access Policy Applies to IT-Admins Group, Password + Okta Verify, Step-up Auth, DENY on policy violation, Zero Trust for admin.
* **JML Lifecycle (Lab 4):** Joiner Department=Finance→Finance-Team→Finance Portal, Mover Finance→HR→HR-Team→HR Portal old revoked new granted, Leaver Deactivated→No apps, Groups kept for audit.
* **Access Governance (Lab 5):** Exception Access Daniel Reed HR→Finance-Portal-Temporary-Access→Finance Portal, Access Review Matrix Omar Keep, Sarah Keep, Alex Keep with review, Mark Remove when ends, Applications tab shows source for RBAC audit.
* **Users Managed:** 7 Okta users, 5 Groups, 3 SAML Apps, 4 Group Rules (Assign Finance Users, Assign HR Users, Assign IT Admins, Assign Contractors), 1 High Risk Admin MFA Policy

---

## Key Skills Demonstrated

* RBAC Model
* SAML SSO Integration
* MFA Policy
* JML Lifecycle
* Access Governance
  
## Technologies Used
| Category | Technologies |
|-----------|-------------|
| Identity Platform | Okta Workforce Identity Cloud |
| Authentication | MFA, Okta Verify |
| Federation | SAML 2.0, Identity Federation, Single Sign-On (SSO) |
| Authorization | RBAC, Group-Based Access Control |
| Lifecycle | JML Simulation, Okta Profile Attributes, Group Rules |
| Governance | Access Governance, Access Reviews |
| Security Models | Least Privilege, Zero Trust |
| IAM Concepts | Provisioning, Deprovisioning, Access Certification |

  

## Detailed Lab Implementations and Visual Proof

<a id="lab-1-RBAC-Model"></a>
### Lab 1: RBAC Model
**Key Learnings and Takeaways:**
Set up role-based access in Okta where users get app access through their department group, not individually. Example: HR-Team group -> HR Portal.
1) More secure by default — Users only get what their role needs (least privilege), and we can review access by group, not person by person.
2) Much faster and easier operations — Joiner / Mover / Leaver is just adding or removing someone from a group. No need to touch every app. This process is easier and faster.
3) Cleaner and Scalable — Handles JML cleanly without leaving behind extra access. Helps the environment scale faster.
   
<details>
<summary>📸 <b>Click to view Lab 1 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture_Diagram](Lab%201%20-%20RBAC%20Model/Screenshots/Architecture_Diagram.png)

#### Administration and Configuration Captures
* **People:**  
  ![Organization Contact](Lab%201%20-%20RBAC%20Model/Screenshots/People.png)
* **Groups:**  
  ![People](Lab%201%20-%20RBAC%20Model/Screenshots/Groups.png)
* **Applications:**  
  ![Custom Profile Attributes](Lab%201%20-%20RBAC%20Model/Screenshots/Applications.png)
* **Application People Example:**  
  ![Groups](Lab%201%20-%20RBAC%20Model/Screenshots/Application_People.png)
* **Application Group Example:**  
  ![Group Rules](Lab%201%20-%20RBAC%20Model/Screenshots/Application_Group.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**

<a id="lab-2-SAML-SSO-Integration"></a>
### Lab 2: SAML SSO Integration
**Key Learnings and Takeaways:**
* SAML is IdP trusting SP: Okta (IdP) sends a login proof to the test app (SP). Alex Chen gets access because he's in IT-Admins group - Alex Chen → IT-Admins → App. That's how all work apps work.
* 4 fields must be exact: ACS URL (where to send login), Entity ID (app's ID), Name ID = Email, Username = Email. One typo and SSO fails.
* Assign via groups: Assigned app to IT-Admins group, not directly to Alex. Easily manageable and scalable.

<details>
<summary>📸 <b>Click to view Lab 2 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture Diagram](Lab%202%20-%20SAML%20SSO%20Integration/Screenshots/Architecture_Diagram.png)

#### SSO Integration 

* **SAML App IT Admin Groups:**  
  ![SAML_App_IT_Admins_Group](Lab%202%20-%20SAML%20SSO%20Integration/Screenshots/SAML_App_IT_Admins_Group.png)
* **IT Admins Alex Chen:**  
  ![IT_Admins_Alex_Chen](Lab%202%20-%20SAML%20SSO%20Integration/Screenshots/IT_Admins_Alex_Chen.png)
* **SAML SSO Integration:**  
  ![SAML_SSO_Integration](Lab%202%20-%20SAML%20SSO%20Integration/Screenshots/SAML_SSO_Integration.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**
<a id="lab-3-MFA-Policy"></a>
### Lab 3: MFA Policy

**Key Learnings and Takeaways:**
* Privileged apps need stronger login: IT Admin Portal is high-risk, so it needs Password + Okta Verify MFA for IT-Admins group, not just password like normal apps.
* 2 rules matter: Rule 1 = IF IT-Admins THEN Password + Another Factor, Rule 2 = Catch-all Deny for everyone else. Without catch-all, anyone can get in.
* Assign policy to app, not to user: Assigned High Risk Admin Access Policy directly to IT Admin Portal app in Sign On > User authentication, so Alex Chen gets MFA prompt when he logs in.

<details>
<summary>📸 <b>Click to view Lab 3 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture Diagram](Lab%203%20-%20MFA%20Policy/Screenshots/Architecture_Diagram.png)

#### MFA Policy
* **IT Admins Rule Details (High Risk Admin Access Policy):**  
  ![IT_Admins_Rule_Details](Lab%203%20-%20MFA%20Policy/Screenshots/IT_Admins_Rule_Details.png)
* **App Assigned to Policy:**  
  ![App_Assigned_to_Policy](Lab%203%20-%20MFA%20Policy/Screenshots/App_Assigned_to_Policy.png)
* **IT Admins Alex Chen:**  
  ![IT_Admins_Alex_Chen](Lab%203%20-%20MFA%20Policy/Screenshots/IT_Admins_Alex_Chen.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**

<a id="lab-4-JML-Lifecycle"></a>
### Lab 4: JML Lifecycle

**Key Learnings and Takeaways:**
* Group Rules automate JML: Department = Finance → Rule If Finance Then Finance-Team auto-assigns group and app. No manual work. This lab simulates an HR-driven identity lifecycle using Okta profile attributes and group rules. A real implementation would integrate an authoritative HR system.
* Mover removes old access: Changed Department Finance→HR → Finance-Team auto-removed, HR-Team auto-added. Old app revoked, new app granted. Prevents extra access.
* Leaver removes apps, keeps groups for audit: Deactivate = No apps assigned. HR-Team stays in Groups tab for audit history. Real flow: Deactivate now, Delete after 30 days.

<details>
<summary>📸 <b>Click to view Lab 4 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture Diagram](Lab%204%20-%20JML%20Lifecycle/Screenshots/Architecture_Diagram.png)

#### JML Lifecycle Proof
* **Daniel Reed Joiner Finance:**  
  ![Daniel_Reed_Joiner_Finance](Lab%204%20-%20JML%20Lifecycle/Screenshots/Daniel_Reed_Joiner_Finance.png)  

* **Daniel Reed Mover HR:**  
 ![Daniel_Reed_Mover_HR](Lab%204%20-%20JML%20Lifecycle/Screenshots/Daniel_Reed_Mover_HR.png)  

* **Daniel Reed Leaver Deactivated:**  
  ![Daniel_Reed_Leaver_Deactivated](Lab%204%20-%20JML%20Lifecycle/Screenshots/Daniel_Reed_Leaver_Deactivated.png)  


</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**

<a id="lab-5-Access-Governance"></a>
### Lab 5: Access Governance

**Key Learnings and Takeaways:**
* Temp group, not permanent team - Daniel HR needs Finance temporary - Created Finance-Portal-Temporary-Access group for Finance Portal, not Finance-Team - Prevents SoD HR+Finance
* Applications tab shows source - My Apps shows HR + Finance, but Applications tab shows Finance via temp group and HR via HR-Team - Auditors check this - RBAC
* Temp access must be removed - Lab 5 manual - No auto-remove - Prod needs Workflows for auto-revoke - Manual causes orphaned access

<details>
<summary>📸 <b>Click to view Lab 5 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture Diagram](Lab%205%20-%20Access%20Governance/Screenshots/Architecture_Diagram.png)

#### Exception Access Proof
* **Daniel Reed Exception Access - My Apps:**  
  ![Daniel_Reed_Exception_Access](Lab%205%20-%20Access%20Governance/Screenshots/Daniel_Reed_Exception_Access.png)

* **Daniel Reed Temp Access - Applications Assignment via Temp Group:**  
  ![Daniel_Reed_Temp_Access_Groups](Lab%205%20-%20Access%20Governance/Screenshots/Daniel_Reed_Temp_Access_Groups.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**

## Production Considerations

This lab simulates IAM concepts using an Okta Developer Tenant.
Enterprise implementations would typically include:
- Active Directory Integration
- SCIM Provisioning
- HR Source Systems
- Automated Access Reviews
- Okta Workflows
- SIEM Monitoring

## Original Repository & Credits
This hands-on lab series was adapted and built upon the foundational framework provided by [SuhaibAN/okta-workforce-iam-lab](https://github.com/SuhaibAN/okta-workforce-iam-lab). Full original references can be found in [REFERENCE.md](REFERENCE.md).

