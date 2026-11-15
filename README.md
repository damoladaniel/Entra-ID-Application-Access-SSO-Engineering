# Entra-ID ApplicationAccess & SSO-Engineering
I wanted to see how IAM works beyond theory, so I onboarded an enterprise app into Entra ID, controlled who gets access through security groups, and used Conditional Access to enforce MFA and other sign-in conditions.

#### Lab Overview
This project demonstrates hands-on Identity & Access Management (IAM) engineering.
I onboarded an enterprise application into Microsoft Entra ID and secured it with role-based access, using group-based authorization and Conditional Access policies.
The lab simulates how organisations bring internal business applications, such as HR systems, finance portals, and SaaS platforms, under central identity control, then restrict access by job function.
It applies Zero Trust principles: no user or device is trusted by default, and every sign-in is verified.
------------------------------------------
### What I built

- Application onboarding: registered the enterprise application in Entra ID and configured single sign-on so users authenticate through the tenant rather than with separate app credentials.
- Role-based access: created security groups mapped to job functions (for example HR, Finance, and IT) and assigned them to the application, so access follows the role instead of the individual.
- Conditional Access: built policies targeting the application that require MFA for every sign-in and block users who aren’t in the authorised groups.
- Least privilege: gave each group only the access its function needs, so joiners, movers, and leavers are handled by changing group membership.
- Testing and validation: signed in as users from different groups to confirm that authorised users got in after MFA and unauthorised users were denied, then checked the sign-in logs to verify the policies were applied.

### Environment
---------------
- Entra ID
- App type: Enterprise Application (OIDC)
- Access Model: Group-based authorization
- Security Controls: Conditional Access & MFA
- Monitoring and Logs: Entra Sign-in Logs

### Architecture
-----------------
<img width="2720" height="1720" alt="entra_id_enterprise_app_access_architecture" src="https://github.com/user-attachments/assets/a7eb208c-7c49-4d6d-8099-4d791cd82a31" />

--------------
## Phase 1 - Creating Identies and Security Groups

#### Step 1 - Create Enterprise Security Groups
Path:
`Microsoft Entra ID → Groups → New group`

Create:
- EnterpriseApp-HR
- EnterpriseApp-IT-Admins
- EnterpriseApp-Guests
----------------------------------
<br></br>
<img width="1943" height="591" alt="Screenshot 2026-11-15 145058" src="https://github.com/user-attachments/assets/68b4d5d5-20c4-412e-902b-d93bf1319218" />
<br></br>

#### Step 2 - Create Test Identities
I created CLoud-Only users representing business roles:
- Daniel Techers
- Katy Dean
- Felipe Guest
- * I set Dynamic User for the groups I created in step 1 so that it the users I created can be automatically assigned to their respective groups
