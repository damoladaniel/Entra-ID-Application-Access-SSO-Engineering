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
I created Cloud-Only users representing business roles:
- Daniel Techers
- Katy Dean
- Felipe Guest
- I set Dynamic User for the groups I created in step 1 so that it the users I created can be automatically assigned to their respective groups

<br></br>
<img width="1608" height="756" alt="image" src="https://github.com/user-attachments/assets/f580f720-d7c3-4cc2-bde9-f3a7c75d47b6" />
<br></br>

## Phase 2 - Application Onboarding
### Step 3 - Register the application
Path: `Microsoft Entra ID → App registrations → New registration`

Application Name:

`Enterprise HR Applcation`

<img width="1529" height="761" alt="image" src="https://github.com/user-attachments/assets/62948977-fe6d-470f-a93f-774bc6935c9d" />

<br></br>

<img width="2176" height="865" alt="Screenshot 2026-11-15 151952" src="https://github.com/user-attachments/assets/168b5f9a-3e5d-4702-a54b-d414232ebd80" />

-------------------

### Step 4 - Enterprise Application Verification

Path:
`Microsoft Entra ID - Enterprise Applications - Enterprise HR App`

<img width="1541" height="844" alt="Screenshot 2026-11-15 152153" src="https://github.com/user-attachments/assets/83008e1d-a465-4ea5-9416-c49f75c5ed73" />
<br></br>
<img width="1697" height="821" alt="Screenshot 2026-11-15 152230" src="https://github.com/user-attachments/assets/7f1c1da2-3c05-4bd7-ba4e-ed149db601c2" />

## Phase 3- App Authorization & Security
### Step 5 - Enforcing Assignments

Path:
`Enterprise application → Properties`

<img width="1204" height="785" alt="Screenshot 2026-11-15 152259" src="https://github.com/user-attachments/assets/71709409-3dbd-4b17-b634-129ed8f5648c" />
<br></br>
<img width="1697" height="821" alt="Screenshot 2026-11-15 152230" src="https://github.com/user-attachments/assets/7f1c1da2-3c05-4bd7-ba4e-ed149db601c2" />

### Step 6 Adding Groups to the Application

Assigned:

Group: `Enterprise -HR-Users`

<br></br>

<img width="2543" height="614" alt="Screenshot 2026-11-15 152446" src="https://github.com/user-attachments/assets/e7e48e23-f052-439b-ac8e-de2350dfcf5f" />
<br></br>
<img width="2519" height="855" alt="Screenshot 2026-11-15 152416" src="https://github.com/user-attachments/assets/cf739b6d-e9c7-4d1c-8530-2bb405a94ac4" />

## Phase 4 - Applying Conditional Access 
### Step 7 - Applying MFA policy to the application

<br></br>

`Microsoft Entra ID → Protection → Conditional Access → New policy`

Policy:
`Conditional Access for HR Application`

Configuration:

- Users: EnterpriseApp-HR
- Cloud apps: Enterprise HR Applcation
- Grant: Require multi-factor authentication
- 

<br></br>

----------------------
  
<img width="2323" height="875" alt="Screenshot 2026-11-15 152516" src="https://github.com/user-attachments/assets/65161fd1-9018-47ec-829b-7894cc604b03" />

----------------

<img width="1439" height="861" alt="Screenshot 2026-11-15 152533" src="https://github.com/user-attachments/assets/cb29cf86-2877-40d3-b58b-70c4fdb9913e" />

