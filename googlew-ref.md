# Google Workspace Admin Quick Reference

A quick reference guide for common Google Workspace admin tasks. I put this together while studying for Google Workspace Administrator certification — it covers the tasks that come up most often in a helpdesk role.

If you are coming from a Microsoft 365 background like me, the last section maps the equivalent admin tasks between the two platforms.

---

## User management

**Create a new user**
Admin Console > Directory > Users > Add new user
Fill in first name, last name, and primary email. The email format is set by your domain (e.g. name@company.com). Assign an organisational unit to control what policies apply to the user.

**Reset a password**
Admin Console > Directory > Users > click the user > Security > Password > Reset password
You can auto-generate or set a specific temporary password. Tick "Require password change at next sign-in" — always do this when resetting for someone else.

**Suspend an account (offboarding)**
Admin Console > Directory > Users > click the user > More options > Suspend user
Suspension stops access immediately but keeps the account and data. Do not delete until you have confirmed all data has been transferred or backed up.

**Transfer Drive files before deletion**
Admin Console > Directory > Users > click the user > Transfer data
Choose a destination account to receive their Drive files. Do this before deletion — it cannot be done after.

---

## Groups and distribution lists

**Create a group**
Admin Console > Directory > Groups > Create group
Groups serve as distribution lists (email to the group goes to all members) and as access control for shared Drives and apps.

**Add a user to a group**
Admin Console > Directory > Groups > click the group > Members > Add members
Users, other groups, or service accounts can all be members.

---

## Device management

**View enrolled devices**
Admin Console > Devices > Overview
Shows mobile devices (Android and iOS), Chrome devices, and company-owned devices enrolled in advanced management.

**Remote wipe a mobile device**
Admin Console > Devices > Mobile and Endpoints > click the device > Wipe device
Use Account wipe to remove only the work profile (leaves personal data intact on BYOD devices). Use Device wipe to wipe the entire device. Confirm with the user before doing a device wipe.

**Enforce screen lock and encryption on mobile**
Admin Console > Devices > Mobile and Endpoints > Settings > Universal > General
Set minimum password length and screen lock timeout. Encryption is enforced by default on modern Android and iOS devices.

---

## Security settings

**Enable 2-Step Verification (2SV) enforcement**
Admin Console > Security > Authentication > 2-step verification
Set enforcement to On for all users. Set the grace period to give users time to enrol before being locked out (7 days is reasonable).

**Review login activity for suspicious access**
Admin Console > Reporting > Audit and investigation > Login log events
Filter by "Failed login" or "Suspicious login" events. Look for logins from unexpected countries or at unusual times.

**Set up alerts for suspicious activity**
Admin Console > Reporting > Manage alerts
Enable alerts for: User suspended, Admin privilege granted, Suspicious login activity, Government-backed attack warning.

---

## Google Workspace vs Microsoft 365 — admin comparison

| Task | Google Workspace | Microsoft 365 |
|------|-----------------|---------------|
| User management | Admin Console > Directory | Azure Active Directory / Entra ID |
| Email admin | Gmail settings in Admin Console | Exchange Admin Center |
| File storage | Google Drive | OneDrive / SharePoint |
| Device management | Admin Console > Devices | Microsoft Intune |
| MDM (advanced) | JAMF integration | Intune |
| MFA | 2-Step Verification | Microsoft Authenticator / Conditional Access |
| Groups | Google Groups | Microsoft 365 Groups / Distribution Lists |
| Audit logs | Admin Console > Reporting | Microsoft Purview / Unified Audit Log |
| Password reset | Admin Console > Users | Azure AD / Self-service password reset |
| App management | Google Workspace Marketplace | Microsoft AppSource |
