# PII Shield for Jira — Privacy Policy

_Last updated: October 28, 2026 (app version 3.3)_

PII Shield for Jira ("the App"), provided by SentientApps, is built to remove sensitive
data from Jira **without ever taking custody of it**. The App runs **100% natively on
Atlassian Forge** and introduces **no external servers, no external databases, and no
third-party subprocessors**.

## 1. Where processing happens
All PII detection and masking runs **inside the Atlassian Forge runtime**. Jira content is
processed in memory by the App's Forge functions. The App declares **no external egress** in
its manifest, and the Forge platform enforces this — so your content **never leaves the
Atlassian trust boundary** during processing.

The App reads issue summaries, descriptions, the Environment field, labels, custom fields,
request-form answers, comments, worklog comments, web links, attachment file names and text
attachments (`.txt`, `.log`, `.csv`, `.json`). PDF and Office attachments (PDF, DOCX, XLSX,
PPTX) are scanned only to flag that they contain personal data; they are not changed.

## 2. What is stored, and where
All App data is stored **within Atlassian**, using native Forge storage — the Forge
Key-Value Store (`@forge/kvs`) and Forge SQL. **No external database is used.**

- **Encrypted vault.** So that a masked value can be revealed during an investigation, the
  original detected value is encrypted with **AES-256-GCM** and stored as **ciphertext**,
  keyed to its token. **Plaintext personal data is never stored.** Values can be revealed
  only by Jira administrators and by the groups or project roles an administrator allows;
  every reveal is logged. Each site has its own 256-bit encryption key, generated on the site
  when first needed and kept in Forge's secret storage inside Atlassian.
- **Settings and rules.** Detection settings, your allow list of email addresses and domains,
  the groups and project roles allowed to reveal values, and custom detection rules.
- **Operational data.** The masking status of each issue, a list of items that couldn't be
  masked automatically (for admin review), Backlog Sweep progress, and daily redaction counts
  by data type. None of these contain the masked values.
- **Audit log.** Event type, issue, token, time and the Atlassian account ID of the person
  who acted (for example, who revealed a value). It contains no plaintext masked values and is
  kept until the App is uninstalled.

The App stores no user profile data (names, email addresses or avatars of Jira users), apart
from any email addresses an administrator chooses to add to the allow list.

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
- **Deleted issues:** when an issue is deleted, its stored values are erased. Tokens that were
  copied into other issues can then no longer be revealed.
- **Closed accounts:** account IDs in the audit log are reported weekly through Atlassian's
  personal data reporting API, and the ID of any closed account is erased from the audit log.
- **Uninstall:** all App data for your site is removed when the App is uninstalled, in line
  with Atlassian's data-lifecycle handling for Forge apps.

## 7. Known limits
- Jira's issue History, and the emails Jira sends when an issue is created, commented on or given
  an attachment, keep the original text, because Jira writes them before any app can act.
- The App's own masking edits don't send update emails (version 3.1 and later). One exception:
  Jira can't rename a file, so when a file name holds personal data the App uploads a copy under a
  masked name and deletes the original, and Jira's update email lists the deleted original by its
  name. Jira offers apps no way to make that change silently.
- PDF and Office attachments are flagged but not changed.
- Web links fire no Jira event, so they are checked every 5 minutes rather than within seconds.

## 8. Contact
Questions or data requests: **support@sentientapps.io**

---
_This document describes the App's data handling for transparency. Organizations should have
their own legal counsel review it before relying on it for compliance purposes._
