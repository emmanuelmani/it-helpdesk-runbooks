# IT Offboarding Checklist

When someone leaves, the IT side needs to happen on the same day — not a week later. A delay in revoking access is a security risk. This checklist covers everything that needs to happen when an employee exits.

The principle is: access should be removed before the person leaves, not after.

---

## On the last working day — immediate actions

**Account suspension**
- [ ] Suspend Google Workspace or Active Directory account — do not delete yet
- [ ] Revoke all active sessions (force sign-out from all devices)
- [ ] Disable MFA devices associated with the account
- [ ] Revoke VPN access
- [ ] Remove from all Slack channels and deactivate Slack account
- [ ] Suspend access to password manager — export shared credentials first if relevant
- [ ] Revoke GitHub access and remove from organisation repositories
- [ ] Remove from Asana, Jira, Notion, or any other project tools
- [ ] Revoke any admin or elevated privileges immediately

**Device recovery**
- [ ] Confirm device return date and method (in-person or shipping)
- [ ] If remote: arrange secure shipping of device
- [ ] Once device received: wipe device before re-imaging
- [ ] Remove device from MDM enrolment
- [ ] Update asset inventory to show device as unassigned

---

## Within 48 hours

**Email and data**
- [ ] Set out-of-office reply on their email pointing to relevant team contact
- [ ] Forward any time-sensitive emails to their manager
- [ ] Transfer ownership of any shared Google Drive files to their manager
- [ ] Export any data that the business needs to retain before account deletion
- [ ] Check if they owned any shared calendars or distribution groups — reassign ownership

**Access audit**
- [ ] Review the user's access history for any unusual activity before departure
- [ ] Check if they had access to any external systems (AWS, Stripe, third-party APIs) — revoke those separately as they will not be handled by the main directory
- [ ] Remove their email from any external mailing lists or vendor portals they were subscribed to on behalf of the company

---

## Within 30 days

- [ ] Permanently delete the user account after confirming all data has been backed up or transferred
- [ ] Remove device from all software licence counts
- [ ] Update IT asset register to reflect equipment returned or disposed of
- [ ] Close the offboarding ticket and log completion date

---

## Things that get missed most often

**Third-party SaaS tools** — These are the ones that slip through. Someone might have set up accounts on Loom, Notion, Figma, Miro, or other tools independently. Check with the manager whether the person used any tools outside the core stack.

**Shared accounts** — If the person had access to any shared team accounts (social media, vendor portals), change those passwords immediately even if the account itself is shared.

**Personal devices** — If the person had corporate email or MDM on a personal phone, remote wipe the work profile on that device.
