# New Starter IT Onboarding Checklist

This is the checklist I work through when a new employee joins. The goal is simple: by the time they sit down on day one, everything should already be working. No one should spend their first morning waiting for IT.

---

## Before the start date

**Accounts and access**
- [ ] Create user account in Google Workspace / Active Directory
- [ ] Assign appropriate licence (Google Workspace, Microsoft 365, etc.)
- [ ] Add user to relevant groups and distribution lists
- [ ] Set up email account and confirm it is active
- [ ] Enrol device in MDM (JAMF for Mac, Intune for Windows)
- [ ] Create account in password manager (1Password / Bitwarden)
- [ ] Add to Slack workspace and relevant channels
- [ ] Set up GitHub / Asana / Jira access based on role
- [ ] Configure MFA on all accounts before day one — not after

**Device preparation**
- [ ] Image or configure device with required OS version
- [ ] Apply all pending OS and security updates
- [ ] Install required applications for the role
- [ ] Confirm device is enrolled in MDM and showing compliant
- [ ] Test VPN access from outside the office network
- [ ] Confirm device encryption is enabled (FileVault on Mac, BitLocker on Windows)

**Documentation**
- [ ] Send welcome email with first-day instructions before they arrive
- [ ] Include IT contact details and how to raise a support ticket
- [ ] Include links to any self-service IT guides

---

## Day one

**When the new starter arrives or connects remotely**
- [ ] Walk through initial login and confirm credentials work
- [ ] Confirm MFA is set up and working on their phone
- [ ] Connect to VPN and confirm access to internal resources
- [ ] Open password manager and confirm they can log in
- [ ] Check Slack is set up and they can see the right channels
- [ ] Verify email is routing correctly — send a test message
- [ ] Confirm they have access to the tools they need for their role
- [ ] Run through how to raise a helpdesk ticket for future issues

**Before you close the ticket**
- [ ] Ask them to try logging out and back in on each key system
- [ ] Confirm they have saved their recovery codes for MFA
- [ ] Log the completed onboarding ticket with all accounts created

---

## Common issues on day one

**MFA not working** — Check the time sync on their phone. Authenticator apps fail if the device clock is out by more than 30 seconds. On iPhone: Settings > General > Date and Time > Set Automatically. On Android: Settings > General Management > Date and Time > Automatic.

**VPN not connecting** — Check the VPN client is installed and updated. Confirm they are using the correct server address. Check their account has VPN access assigned in the directory.

**Email not receiving** — Check the licence is assigned. Check the account is not in a paused or suspended state. Check spam filters are not blocking legitimate senders.

**Device not showing in MDM** — Re-enrol the device. On Mac: go to System Settings > Privacy and Security > Profiles and check the MDM profile is installed. On Windows: go to Settings > Accounts > Access work or school and check the account is connected.
