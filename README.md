# PII Shield – User Documentation & Security Policy

**Developed by Sentient Apps** *Empowering Jira Admins with privacy-first automated security.*

---

## 🛡️ Overview
**PII Shield** is a dedicated privacy tool for Jira Cloud that automatically identifies Personally Identifiable Information (PII) within issue comments and descriptions. Designed for high-compliance environments, it helps prevent accidental data leaks (like emails, phone numbers, and API keys) before they become a security liability.

## 🚀 How to Access the App
Once installed from the Atlassian Marketplace, PII Shield integrates seamlessly into your Jira interface:
1. **Open any Jira Issue.**
2. **View the Sidebar:** Locate the **"PII Security Status"** panel in the right-hand sidebar.
3. **Real-Time Monitoring:** The app automatically monitors the **Comments** and **Activity** sections of the issue as they are updated.

## 🛠️ How it Works
PII Shield scans text in real-time to identify sensitive patterns, including:
* **Email Addresses** (e.g., name@company.com)
* **Phone Numbers** (International and local formats)
* **Credit Card Patterns**
* **Technical Secrets** (API Keys, Tokens, and Secret Keys)

### Understanding Security Metrics
* **Redactions Today:** Located in the sidebar, this counter displays a running total of all security actions taken across your entire Jira instance within a 24-hour window.
* **Instance-Wide Protection:** This metric allows administrators to monitor real-time security health and demonstrate compliance with data privacy standards (GDPR, CCPA).

---

## 🔒 Security Policy
The following sections outline our commitment to data protection and our "Zero-Egress" architecture.

### Atlassian Forge Infrastructure
PII Shield is built exclusively on the **Atlassian Forge** development platform. The app operates within a multi-tenant, serverless environment managed and secured by Atlassian. By utilizing Forge, PII Shield inherits Atlassian’s enterprise-grade security controls, including built-in authentication, scoped permissions, and data isolation.

### Zero-Egress Architecture
Our app is designed with a **Zero-Egress** philosophy:
* **No External Data Transfer:** No end-user data—including Jira issue content, comments, or metadata—is ever transmitted to or stored on external servers.
* **Local Processing:** All detection logic runs locally within the Atlassian Forge FaaS (Function as a Service) environment.

### Data Storage & Retention
* **Minimal Operational Data:** We utilize **Forge Storage** strictly for anonymized security counters (e.g., "Redactions Today"). 
* **No PII Logging:** We do not store or log the actual contents of your Jira issues or the PII detected. Once a scan is complete, the data is flushed from temporary memory.

### Vulnerability Reporting
We take security seriously. If you discover a potential vulnerability, please report it immediately via our [Issue Tracker](https://github.com/bandi29/pii-shield-support/issues) or by emailing **support@sentientapps.io**. We aim to acknowledge all security reports within 24 business hours.

---

## 📞 Support & Feedback
* **Support Email:** [support@sentientapps.io](mailto:support@sentientapps.io)
* **Official Website:** [sentientapps.io](https://sentientapps.io)
* **Bug Reports:** Please open an issue on our [GitHub Support Repository](https://github.com/bandi29/pii-shield-support).

---
*© 2026 Sentient Apps. Built for the Atlassian Marketplace.*
