# 🔒 Security Policy

**Live Music World®** is a **client‑side web application** – it runs entirely in your browser.  
There is **no backend server**, no database, no user accounts, and no data is collected or stored.

Despite its simplicity, security still matters. This page explains:

- What security means for this project
- How to report a vulnerability
- What to expect after reporting

---

## 📌 Scope – What Is Covered

The project consists of a single `index.html` file with:

- HTML, CSS, and JavaScript (all inline)
- External resources: Font Awesome 6 CDN, Google Fonts CDN
- Radio stream URLs (third‑party)
- A mailto: link for station suggestions

**Security issues in scope:**
- Cross‑Site Scripting (XSS) vulnerabilities
- Injection attacks through the mailto: link or audio source
- Malicious manipulation of stream URLs
- Broken or unsafe external resource loading (mixed content, etc.)

**Out of scope:**
- Vulnerabilities in the **browser** itself
- Security of the **radio streams** (those are hosted by third parties)
- Attacks that require physical access to the user’s device
- Social engineering or phishing (the project does not collect data)

---

## 🚨 Reporting a Security Vulnerability

If you believe you have found a security issue in Live Music World®, please **do not** post it publicly.

Instead:

1. **Send an email** to: `dengluffy1@gmail.com`
2. Use the subject line: `[Security] Live Music World® – Brief description`
3. Include:
   - A clear description of the issue
   - Steps to reproduce (browser, OS, any special conditions)
   - The potential impact
   - (Optional) a suggested fix

You may also open a **private issue** if the repository supports that feature (e.g., GitHub’s “Report a vulnerability”).

---

## 🔐 Responsible Disclosure

I ask that you:

- **Give reasonable time** (at least 7 days) to address the issue before disclosing it publicly.
- **Do not exploit** the vulnerability beyond what is necessary to demonstrate it.
- **Do not use** the vulnerability to harm users or the project.

I will:
- Acknowledge receipt of your report within **48 hours**.
- Investigate and confirm the issue.
- Provide a fix in the next release (if applicable).
- Credit you for the discovery (unless you prefer to remain anonymous).

---

## 🧪 Current Security Notes

As of the latest release:

- **No inline event handlers** that could be abused (all event listeners are added via `addEventListener` in JavaScript).
- **All external resources** use HTTPS (Google Fonts, Font Awesome, radio streams).
- **Mailto link** is constructed safely using `encodeURIComponent` – no raw user input is inserted into the `href`.
- **Stream URLs** are hardcoded – they are not user‑supplied, so no injection risk.
- **Language switching** updates the DOM using `innerText` and `textContent` (safe), not `innerHTML` with unsanitised data.
- **Translations** are hardcoded in the `translations` object – no external JSON loaded.

Despite these precautions, third‑party stream URLs could theoretically change to serve malicious content (e.g., a stream that injects JavaScript). That risk exists for **any** web radio player. Users should always keep their browsers updated.

---

## 🔄 Reporting a Broken Stream (Not a Security Issue)

If a radio station stops playing, that is **not** a security vulnerability.  
Please use the built‑in **“Suggest a Radio Station”** button or email `dengluffy1@gmail.com` with subject `[Stream] Broken – [Station Name]`.

---

## 📅 Updates to This Policy

This security policy may be updated as the project evolves.  
The latest version will always be available in the repository under `SECURITY.md`.

---

## 🙏 Thank You

Your help keeps Live Music World® safe for everyone who uses it personally and non‑commercially.

---

*Live Music World® – security through simplicity, fixed through community.*
