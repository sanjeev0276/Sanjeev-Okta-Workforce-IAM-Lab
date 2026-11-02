# Sanjeev-Okta-Workforce-IAM-Lab
![Okta](https://img.shields.io/badge/Okta-IAM-007DC1?style=for-the-badge&logo=okta&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-Automation-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Integration-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SAML](https://img.shields.io/badge/SAML%202.0-SSO-FF6B00?style=for-the-badge)
![MFA](https://img.shields.io/badge/Adaptive%20MFA-Zero%20Trust-00A86B?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**Author:** Sanjeev Shrestha | Dallas–Fort Worth Area, TX (Shrestha Technologies)  
**Target Roles:** IAM Engineer / Identity Engineer / Okta Administrator / Entra ID Engineer (2027)  
**Certification Focus:** Preparing for Okta Certified Professional (OCP)  
**Environment:** Okta Developer Tenant (*.okta.com - redacted) 

## 5 Labs Architecture Overview
RBAC Model → SML SSO Integration → MFO Policy → Access Governance
 ![Architecture_Overview](Overall_Architecture.png)


## Quick Navigation and Lab Execution Status
<a id="lab-execution-status"></a>
| Lab       | Focus Area                                | Status    | Jump to Lab                                                                  |
|-----------|-------------------------------------------|-----------|------------------------------------------------------------------------------|
| **Lab 1** | RBAC Model | Completed | [Go to Lab 1](#lab-1-RBAC-Model)                       |
| **Lab 2** | SML SSO Integration    | Completed | [Go to Lab 2](#lab-2-SML-SSO-Integration) |
| **Lab 3** | MFA Policy | Completed | [Go to Lab 3](#lab-3-MFA-Policy)               |
| **Lab 4** | JML Lifecycle          | Completed | [Go to Lab 4](#lab-4-JML-Lifecycle)                        |
| **Lab 5** | Access Governance        | Completed | [Go to Lab 5](#lab-5-Access-Governance)        |


---
## Executive Summary and Business Impact

Implemented an end-to-end IAM environment using Okta, Active Directory, SAML federation, Adaptive MFA, RBAC, and automated Joiner-Mover-Leaver lifecycle processes across six hands-on labs.

* **Tenant Foundation (Lab 1):** Core Okta tenant `*.okta.com - redacted`, custom profile attributes, Groups RBAC, Global Session + Auth + Enrollment Policies.
* **Access Governance (Lab 3+4):** Group-based provisioning, access-sprawl audit via System Log `application.user_membership.add`, least-privilege via group app assignments for Slack, Workspace, SharePoint.
* **Lifecycle Automation (Lab 2+6):** AD `allenlab.local` as source with DelAuth + Full/Incremental Import via AD Agent, JML automation with PowerShell + CSV batch `jml-batch.csv`, Unassigned → Confirm → Active/Deactivated.
* **Centralized Auth (Lab 4):** SAML 2.0 federation with attribute mapping across Slack, Google Workspace, SharePoint.
* **Zero Trust (Lab 5):** Network Zones Trusted/Untrusted IP, Adaptive Sign-On + Step-Up High Assurance for SharePoint, Passwordless Okta Verify Push with Number Matching.
* **Users Managed:** 20+ AD users, 6 Groups, 3 SAML Apps, 22 MFA policies

---

## Key Skills Demonstrated

* RBAC Model
* SAML SSO Integration
* MFA Policy
* JML Lifecycle
* Access Governance

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

<a id="lab-2-SML-SSO-Integration"></a>
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
![Architecture Diagram](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Architecture_Diagram.png)

#### RBAC & Deprovisioning Proof
* **Group Sync Verification:**  
  ![Okta Group Sync](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Okta_Group_Sync.png)
* **Full Reconciliation Import:**  
  ![Full Import](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Full_Import.png)
* **Lifecycle Deactivation (AD side):**  
  ![Sarah Disabled AD](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Sarah_Disabled_AD.png)
* **Lifecycle Deactivation (Okta side):**  
  ![Sarah Deactivated Okta](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Sarah_Deactivated_Okta.png)
* **Access Sprawl Investigation and Audit Report:**  
  ![Access Sprawl Investigation](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Access_Sprawl_Investigation.png)  
  ![Access Sprawl Report](Lab%203%20-%20Okta%20RBAC%20Design%20and%20Implementation/Screenshots/Access_Sprawl_Report.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**

<a id="lab-4-JML-Lifecycle"></a>
### Lab 4: JML Lifecycle

**Key Learnings and Takeaways:**
* Configured custom SAML 2.0 integrations with multiple Service Providers (Slack, Google Workspace, SharePoint).
* Applied least-privilege entitlements through group memberships rather than direct assignments. Verified user access segregation across distinct user profiles in Incognito test sessions.

<details>
<summary>📸 <b>Click to view Lab 4 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture Diagram](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Architecture_Diagram.png)

#### SAML Integration Proof
* **Custom SAML Configuration:**  
  ![SAML Creation 1](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Slack_SP_Shrestha_Technology_1.png)  
  ![SAML Creation 2](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Slack_SP_Shrestha_Technology_2.png)  
  ![SAML Creation 3](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Slack_SP_Shrestha_Technology_3.png)
* **Group-Based Application Assignments:**  
  ![Group Based App Access 1](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Group_Based_App_Access_1.png)  
  ![Group Based App Access 2](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Group_Based_App_Access_2.png)
* **Least Privilege Access Verification:**  
  * *Finance User (John Smith - Limited Access):*  
    ![John App Access](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/John_App_Access.png)
  * *HR & Cloud Admin (Lisa Park - Extended Access):*  
    ![Lisa App Access](Lab%204%20-%20Okta%20SAML%202.0%20Application%20Integration/Screenshots/Lisa_App_Access.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**

<a id="lab-5-Access-Governance"></a>
### Lab 5: Access Governance

**Key Learnings and Takeaways:**
* Defined trusted vs. untrusted IP Network Zones. Constructed Adaptive Sign-On Rules to require MFA or block access based on client network context.
* Enforced step-up authentication policies on high-value resources (e.g., SharePoint) to challenge active sessions upon accessing sensitive data.

<details>
<summary>📸 <b>Click to view Lab 5 Diagrams and Screenshots</b></summary>

<br>

#### Architecture Diagram
![Architecture Diagram](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Architecture_Diagram.png)

#### MFA & Policy Verification
* **Authenticator Enrollment & Passwordless Setup:**  
  ![Enroll Okta Verify](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Enroll_Okta_Verify.png)  
  ![Passwordless Enrollment](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Passwordless_Enrollment_1.png)
* **Network Zones & Adaptive Rules:**  
  ![Network Zones](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Network_Zones.png)  
  ![Adaptive Policy Outside Network](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Risk_Based_Adaptive_MFA_Policy_OutsideNetwork.png)  
  ![Adaptive Policy Corporate Network](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Risk_Based_Adaptive_MFA_Policy_Corporate.png)
* **Step-Up Authentication Engine:**  
  ![Step Up Policy](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Step_Up_Authentication_Policy.png)  
  ![Step Up Rule](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Step_Up_Authentication_Rule.png)  
  ![Step Up High Assurance](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Step_Up_Authentication_High_Assurance_Policy.png)
* **User Authentication Testing:**  
  ![John Smith Access](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/John_Smith_Access.png)  
  ![Jane Doe Access](Lab%205%20-%20Okta%20MFA%20and%20Adaptive%20Authentication/Screenshots/Jane_Doe_Access.png)

</details>

---
**[↑ Back to Lab Execution Status](#lab-execution-status)**


## Original Repository & Credits
This hands-on lab series was adapted and built upon the foundational framework provided by [SuhaibAN/okta-workforce-iam-lab] (https://github.com/SuhaibAN/okta-workforce-iam-lab). Full original references can be found in [REFERENCE.md](REFERENCE.md).

