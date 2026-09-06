# PII Shield for Jira — Privacy Policy

_Last updated: September 5, 2026_

PII Shield for Jira ("the App"), provided by SentientApps, is built to remove sensitive
data from Jira **without ever taking custody of it**. The App runs **100% natively on
Atlassian Forge** and introduces **no external servers, no external databases, and no
third-party subprocessors**.

## 1. Where processing happens
All PII detection and redaction runs **inside the Atlassian Forge runtime**. Jira content is
processed in memory by the App's Forge functions. The App declares **no external egress** in
its manifest, and the Forge platform enforces this — so your content **never leaves the
Atlassian trust boundary** during processing.

## 2. What is stored, and where
All App data is stored **within Atlassian**, using native Forge storage — the Forge
Key-Value Store (`@forge/kvs`) and Forge SQL. **No external database is used.**

- **Encrypted vault.** So that an authorized administrator can reverse a redaction during a
  compliance investigation, the original detected value is encrypted with **AES-256-GCM** and
  stored as **ciphertext**, keyed to its redaction token. **Plaintext personal data is never
  stored** — only ciphertext, which only an administrator with the appropriate role can
  unmask via the Vault Inspector.
- **Metadata & audit.** Redaction counts and an audit trail (event type, token, issue key,
  timestamp, actor) are stored in Forge storage / Forge SQL to provide security metrics and
  compliance evidence. These records contain **no plaintext personal data**.

## 3. Data in transit
All traffic is between the App's Forge functions and Atlassian's own APIs, over TLS, inside
Atlassian's network. **No data is transmitted to SentientApps or any third party.**

## 4. Encryption
- **In transit:** TLS, within the Atlassian platform.
- **At rest:** AES-256-GCM for vaulted values, on top of Atlassian's own encryption of Forge
  storage.

## 5. Subprocessors
The App uses **no third-party subprocessors** — no external AI services, no external APIs, and
no cloud accounts operated by SentientApps. It relies solely on the Atlassian Forge platform.

## 6. Data retention & deletion
Vaulted ciphertext, tokens, settings, and audit records live in the App's Forge storage for
your site and are removed when the App is uninstalled, in line with Atlassian's data-lifecycle
handling for Forge apps.

## 7. Contact
Questions or data requests: **apps@sentientapps.io**

---
_This document describes the App's data handling for transparency. Organizations should have
their own legal counsel review it before relying on it for compliance purposes._
