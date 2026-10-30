# PII Shield for Jira — Privacy Policy

_Last updated: October 30, 2026 (app version 3.6)_

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
attachments (`.txt`, `.log`, `.csv`, `.json`), and Word, Excel and PowerPoint attachments (DOCX,
XLSX, PPTX), which are rewritten with the values masked. PDF attachments are scanned only to flag
that they contain personal data; they are not changed. The text in images (PNG and JPEG
attachments, and images inside Office and PDF files) is read by a text-recognition engine bundled
in the App and running inside Forge, to flag personal data or, if an admin chooses, to black it
out. Masked copies of images carry no metadata (such as camera details or location), and masked
Office copies have their author properties emptied.

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
- **Logs.** The App's Forge logs contain issue keys, comment, worklog and attachment IDs,
  counts, data types (such as `EMAIL`), masked file names and error codes — never the original
  values. They stay in Atlassian and reach SentientApps only if a site admin allows log sharing.

The App stores no user profile data (names, email addresses or avatars of Jira users), apart
from any email addresses an administrator chooses to add to the allow list. The names shown in
the audit log are looked up from Jira when an administrator views or exports it, and are not
stored.

**Logs, analytics and custom metrics sharing.** When an app is installed, Atlassian lets a site
admin choose whether to share the app's logs, analytics and custom metrics with its developer.
These switches and their defaults belong to Atlassian. The App works fully with all of them off,
sends no analytics and records no custom metrics.

## 3. Emails
If an administrator turns on **Customer emails for public comments**, the App asks Jira to
email the request's reporter and participants a public comment after it has been masked. The
email holds only the masked text and is sent by Jira through its own notification service,
inside Atlassian; the App never sends email itself.

## 4. Data in transit
All traffic is between the App's Forge functions and Atlassian's own APIs, over TLS, inside
Atlassian's network. **No data is transmitted to SentientApps or any third party.**

## 5. Encryption
- **In transit:** TLS, within the Atlassian platform.
- **At rest:** AES-256-GCM for vaulted values, on top of Atlassian's own encryption of Forge
  storage.

## 6. Subprocessors
The App uses **no third-party subprocessors** — no external AI services, no external APIs, and
no cloud accounts operated by SentientApps. It relies solely on the Atlassian Forge platform.

## 7. Data retention & deletion
- **Deleted issues:** when an issue is deleted, its stored values are erased. Tokens that were
  copied into other issues can then no longer be revealed.
- **Closed accounts:** account IDs in the audit log are reported weekly through Atlassian's
  personal data reporting API, and the ID of any closed account is erased from the audit log.
- **Uninstall:** all App data for your site is removed when the App is uninstalled, in line
  with Atlassian's data-lifecycle handling for Forge apps.

## 8. Known limits
- Jira's issue History, and the emails Jira sends when an issue is created, commented on or given
  an attachment, keep the original text, because Jira writes them before any app can act (the
  **Customer emails** setting in section 3 covers public comments). No app can edit or remove
  History entries. Atlassian AI features such as Rovo follow Jira's
  permissions; an organization that requires AI features never to draw on original values can
  turn them off for Jira in Atlassian Administration.
- The App's own masking edits don't send update emails (version 3.1 and later). One exception:
  Jira can't rename a file, so when a file name holds personal data the App uploads a copy under a
  masked name and deletes the original, and Jira's update email lists the deleted original by its
  name. Jira offers apps no way to make that change silently.
- PDF attachments are flagged but not changed. Text recognition can miss very small or faint text.
  Files over 10 MB, password-protected files and images the App can't read are listed for an
  admin to review rather than checked.
- Web links fire no Jira event, so they are checked every 5 minutes rather than within seconds.

## 9. Contact
Questions or data requests: **support@sentientapps.io**

---
_This document describes the App's data handling for transparency. Organizations should have
their own legal counsel review it before relying on it for compliance purposes._
