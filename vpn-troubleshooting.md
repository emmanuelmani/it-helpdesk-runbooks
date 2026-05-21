# VPN Troubleshooting Guide

VPN issues are one of the most common helpdesk tickets, especially in remote-first teams. This guide covers the most common problems and how to resolve them — on both Windows and macOS.

The structure is: symptom first, then cause, then fix. This is how I write all troubleshooting guides because it matches how a user describes their problem.

---

## Cannot connect at all

**Symptom**: VPN client opens but connection fails immediately or hangs indefinitely.

**Check 1 — Internet connectivity**
Confirm the user has a working internet connection without the VPN. Open a browser and go to google.com. If that does not load, the problem is the internet connection, not the VPN.

**Check 2 — VPN client version**
Outdated VPN clients frequently stop working after server-side updates. Check the installed version against the current version on the company intranet or vendor website. Uninstall and reinstall if out of date.

**Check 3 — Correct server address**
Confirm the user is entering the correct VPN server address. This is the most common cause of failure when the client was recently reinstalled or set up on a new device. Check the IT documentation for the correct address.

**Check 4 — Firewall or antivirus blocking the connection**
Corporate endpoint protection or a home router firewall can block VPN traffic. Temporarily disable the local firewall and try again. If it connects, add the VPN client as an exception in the firewall settings.

**Check 5 — Port blocking by the network**
Some networks (hotels, cafes, some mobile networks) block the ports VPN clients use. Try connecting on a different network such as a mobile hotspot.

---

## Connects but drops after a few minutes

**Symptom**: VPN connects successfully but disconnects after 5–20 minutes without warning.

**Cause**: Usually a sleep or power-saving setting on the device is suspending the network adapter.

**Fix on macOS**:
System Settings > Battery > Options > uncheck "Enable Power Nap" and set "Prevent automatic sleeping" to On when plugged in.

**Fix on Windows**:
Device Manager > Network Adapters > right-click the network adapter > Properties > Power Management > uncheck "Allow the computer to turn off this device to save power."

**Secondary cause**: VPN session timeout set too short on the server side. If the above does not fix it, raise it with the infrastructure or network team — the session timeout may need to be extended.

---

## Connected but cannot access internal resources

**Symptom**: VPN shows as connected but internal websites, shared drives, or internal tools do not load.

**Check 1 — Split tunnelling configuration**
If the VPN uses split tunnelling, only specific traffic is routed through the VPN. Confirm the resources you are trying to reach are in the split tunnel include list. This is a configuration issue on the VPN server side.

**Check 2 — DNS resolution**
Open a terminal or command prompt and run:
```
nslookup internal-resource-name
```
If it returns an external IP instead of an internal one, the DNS is not pointing to the internal DNS server. Check the VPN client DNS settings.

**Check 3 — Ping the internal resource**
```
ping internal-server-name
```
If ping works but the web interface does not load, the issue is the application, not the VPN connection itself.

---

## Certificate error on connection

**Symptom**: VPN client shows a certificate warning or "untrusted certificate" error.

**Cause**: The device does not have the company's root certificate installed, or the certificate has expired.

**Fix**: Install the company root certificate. On macOS, double-click the certificate file and add it to the System keychain, then set it to "Always Trust." On Windows, run `certmgr.msc` and import the certificate into Trusted Root Certification Authorities.

If the certificate has genuinely expired, this needs to be renewed on the VPN server — escalate to the network or infrastructure team.

---

## VPN works on some networks but not others

**Symptom**: VPN connects fine at home but not at a specific office, hotel, or coffee shop.

**Cause**: The other network is blocking VPN traffic. Common culprits are hotels and some corporate guest Wi-Fi networks.

**Fix**: Use a mobile hotspot instead. If this is a regular location, ask the network administrator for that site to whitelist the VPN ports (typically UDP 500 and 4500 for IKEv2, or TCP 443 for SSL-based VPNs).
