# Entra-ID ApplicationAccess & SSO-Engineering
I wanted to see how IAM works beyond theory, so I onboarded an enterprise app into Entra ID, controlled who gets access through security groups, and used Conditional Access to enforce MFA and other sign-in conditions.

#### Lab Overview
This project demonstrates hands-on Identity & Access Management (IAM) engineering. I onboarded an enterprise application into Microsoft Entra ID and secured it with role-based access, using group-based authorization and Conditional Access policies.
The lab simulates how organisations bring internal business applications, such as HR systems, finance portals, and SaaS platforms, under central identity control, then restrict access by job function.
It applies Zero Trust principles: no user or device is trusted by default, and every sign-in is verified.
------------------------------------------
### What I built

-##### Application onboarding: registered the enterprise application in Entra ID and configured single sign-on so users authenticate through the tenant rather than with separate app credentials.
-##### Role-based access: created security groups mapped to job functions (for example HR, Finance, and IT) and assigned them to the application, so access follows the role instead of the individual.
-##### Conditional Access: built policies targeting the application that require MFA for every sign-in and block users who aren’t in the authorised groups.
-##### Least privilege: gave each group only the access its function needs, so joiners, movers, and leavers are handled by changing group membership.
-##### Testing and validation: signed in as users from different groups to confirm that authorised users got in after MFA and unauthorised users were denied, then checked the sign-in logs to verify the policies were applied.
