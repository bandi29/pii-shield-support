🚀 How to Access the App
Once installed from the Atlassian Marketplace, PII Shield integrates seamlessly into your Jira interface:

Open any Jira Issue.

View the Sidebar: Locate the "PII Security Status" panel in the right-hand sidebar.

Real-Time Monitoring: The app automatically monitors the Comments and Activity sections of the issue as they are updated.

🛠️ How it Works
PII Shield scans text in real-time to identify sensitive patterns, including:

Email Addresses (e.g., name@company.com)

Phone Numbers (International and local formats)

Credit Card Patterns

Technical Secrets (API Keys, Tokens, and Secret Keys)

Security Metrics
Redactions Today: Located in the sidebar, this counter displays a running total of all security actions taken across your entire Jira instance within a 24-hour window.

Instance-Wide Protection: This metric allows administrators to monitor real-time security health and demonstrate compliance with data privacy standards (GDPR, CCPA).

🔒 Security Policy & Data Privacy
PII Shield is built with a "Zero-Egress" architecture, meaning your sensitive data never leaves the Atlassian environment.

1. Atlassian Forge Infrastructure
The app is built exclusively on Atlassian Forge. It operates within a multi-tenant, serverless environment managed and secured by Atlassian. By utilizing Forge, PII Shield inherits Atlassian’s enterprise-grade security controls and data isolation.

2. Zero-Egress Architecture
No External Transfer: No end-user data (issue content, comments, or metadata) is ever transmitted to or stored on external servers.

Local Processing: All detection logic runs within the Atlassian Forge FaaS (Function as a Service) environment.

3. Data Storage & Logging
Minimal Storage: We utilize Forge Storage strictly for operational counters (e.g., "Redactions Today").

No PII Logging: We do not log the actual contents of your Jira issues or the PII detected. Once a scan is complete, the data is flushed from memory.

4. Vulnerability Management
We are committed to the security of our tools. If you discover a potential vulnerability, please report it via our Issue Tracker or contact us directly at support@sentientapps.io.

📞 Support & Feedback
We are here to help you maintain a secure Jira environment.

Support Email: support@sentientapps.io

Official Website: sentientapps.io

Bug Reports: Please open an issue on our GitHub Support Repository.

© 2026 Sentient Apps. Built for the Atlassian Marketplace.
