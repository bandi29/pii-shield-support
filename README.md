# PII Shield - User Documentation

**Developed by Sentient Apps**

PII Shield is a privacy-first security tool for Jira that automatically detects and highlights Personally Identifiable Information (PII) within issue comments. Our "Zero-Egress" architecture ensures that your sensitive data never leaves the Atlassian Forge environment.

---

## How to Access the App

Once installed, PII Shield integrates directly into your Jira Issue view.

1. **Open any Jira Issue.**
2. **Look at the Right Sidebar:** You will see a panel titled **"PII Security Status"**.
3. **Activity Feed:** The app automatically monitors the **Comments** section of the issue.

---

## How the App Works

PII Shield scans comments in real-time to identify sensitive patterns, including:

* **Email Addresses** (e.g., name@example.com)
* **Phone Numbers** (International and Local formats)
* **Credit Card Patterns**
* **API Keys and Tokens**

### **Detection & Reporting**

* **Visual Indicators:** When PII is detected, the app highlights the text or provides a warning notification to the administrator.
* **Cumulative Tracking:** The "Redactions Today" badge in the sidebar displays a running total of all security actions taken by the app across your Jira instance to help you track compliance.

---

## Understanding Security Metrics

**Redactions Today:** This counter represents the total number of sensitive data items (PII) identified and secured by PII Shield across your entire Jira instance within the current 24-hour window. This helps administrators monitor real-time security health and demonstrate compliance with data privacy standards.

---

## Privacy & Security

As a Sentient Apps "Zero-Egress" solution:

* **No External Data Transfer:** All detection logic runs locally within Atlassian Forge.
* **No Storage:** We do not store or log the contents of your Jira issues on our own servers.

---

## Support

Welcome to PII Shield Support. Please open an [Issue](https://github.com/bandi29/pii-shield-support/issues) to report bugs or security concerns.

For other technical assistance or feature requests, you may also contact our support team:

**Email:** support@sentientapps.io  
**Website:** [sentientapps.io](https://sentientapps.io)
