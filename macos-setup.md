# macOS Setup Guide

This is a setup guide for configuring a new Mac for a corporate environment. It covers the steps from first boot through to a fully configured, MDM-enrolled, security-compliant device ready for a new employee.

I wrote this from personal experience with macOS and from understanding how MDM enrolment works across platforms (my enterprise background is Intune on Windows, but the concepts carry across to JAMF on Mac).

---

## First boot

When you power on a new Mac for the first time, you will go through Apple's Setup Assistant. Key decisions at this stage:

**Do not sign in with a personal Apple ID** — create a local account first. In a corporate environment, the Apple ID situation should be managed by the company's MDM policy, not set up ad-hoc.

**Enable FileVault** — Apple will offer this during setup. Always enable it. FileVault encrypts the entire disk, which is required for most corporate security policies. If it was not enabled at setup, go to System Settings > Privacy and Security > FileVault and turn it on. It runs in the background and does not affect performance noticeably.

**Do not skip software updates** — before doing anything else, go to System Settings > General > Software Update and install all available updates. This takes time but should not be skipped.

---

## MDM enrolment (JAMF)

If the company uses JAMF for device management, enrolment typically happens one of two ways:

**Automated Device Enrolment (ADE)** — if the Mac was purchased through Apple Business Manager and linked to your JAMF instance, it will prompt for MDM enrolment automatically during Setup Assistant. Follow the prompts — the MDM profile will install and JAMF will push required applications automatically.

**Manual enrolment** — go to the company's JAMF enrolment URL (provided by IT), sign in with corporate credentials, and follow the steps to install the MDM profile. Once installed, go to System Settings > Privacy and Security > Profiles to confirm the MDM profile is there.

**Confirming enrolment** — in JAMF, the device should appear in the device list within a few minutes of enrolment. Check that the device shows as supervised and that the correct policies are applying.

---

## Core applications to install

**Security tools**
- Company endpoint protection (CrowdStrike, SentinelOne, or similar — installed via MDM)
- VPN client (GlobalProtect, Cisco Secure Client, or similar)
- 1Password or company password manager

**Productivity**
- Google Chrome (if the company uses Google Workspace)
- Slack
- Zoom or Google Meet

**For development or technical roles**
- Homebrew (package manager): install from brew.sh
- Git: comes with Xcode Command Line Tools — run `git --version` in Terminal to trigger the install prompt

---

## macOS system preferences to configure for corporate use

**Security settings**
- System Settings > Lock Screen: set to require password immediately after sleep
- System Settings > Privacy and Security: review which apps have access to camera, microphone, and screen recording — remove anything that does not need it
- System Settings > Sharing: turn off everything that is not needed (AirDrop should be set to Contacts Only, not Everyone)

**Updates**
- System Settings > General > Software Update > Automatic Updates: enable all options

**Accessibility**
- System Settings > Keyboard > Keyboard Shortcuts > Screenshots: useful to know Cmd+Shift+4 for area screenshots and Cmd+Shift+5 for screen recording

---

## Common macOS troubleshooting

**App will not open — "cannot be opened because the developer cannot be verified"**
Go to System Settings > Privacy and Security and scroll down to find the blocked app with an option to open it anyway. This happens with apps downloaded outside the App Store and is not a sign of a problem.

**Mac running slow after an update**
This is normal for 24–48 hours after a major update while Spotlight re-indexes and system processes complete. If it persists, check Activity Monitor for any process using excessive CPU or memory.

**VPN disconnecting frequently**
Check the VPN client version is up to date. Check that the Mac's sleep settings are not suspending the network connection — System Settings > Battery > Options > Enable Power Nap should be turned off if VPN drops during sleep.

**Can't connect to company Wi-Fi**
Forget the network and reconnect. If using 802.1x certificate-based authentication, confirm the certificate is installed in Keychain Access.
