# Privacy Policy

**Last updated: 2025-03-12**

APICue Development Team ("we", "our", or "us") operates the APICue plugin for JetBrains IDEs (the "Plugin"). This Privacy Policy explains how we collect, use, store, and disclose information when you use the Plugin.

By installing and using the Plugin, you agree to the practices described in this Privacy Policy. If you do not agree, please do not install or use the Plugin.

---

## 1. Information We Collect

### 1.1 Information You Provide

When you use the Plugin, you may voluntarily provide the following information:

- **API Request Data**: URLs, headers, query parameters, request bodies, and authentication tokens (e.g., Bearer JWT, API Keys, Basic Auth credentials) that you enter into the Plugin's interface.
- **Saved Examples**: Request and response payloads that you choose to save as test examples via the Plugin's save/load functionality.
- **Environment Settings**: Server URLs and environment-specific configurations that you configure within the Plugin.

### 1.2 Automatically Collected Information

The Plugin itself **does not** automatically collect any telemetry, usage statistics, crash reports, or personally identifiable information. However, the JetBrains IDE platform and JetBrains Marketplace may collect certain usage information as described in their respective privacy policies.

### 1.3 Third-Party Data Processing

The Plugin uses the following third-party components, each of which may process data according to their own policies:

| Component | Purpose | Data Processed |
|-----------|---------|----------------|
| **OkHttp** (4.12.0) | HTTP client for sending API requests | All request/response data transmitted to target servers |
| **JetBrains Marketplace** | Plugin distribution and licensing | License keys, IDE version, purchase information |

---

## 2. How We Use Your Information

The Plugin processes information **exclusively on your local machine** for the following purposes:

- **Executing API Requests**: To send HTTP requests to the server URLs you specify and display responses.
- **Storing Configuration**: To persist authentication tokens, environment settings, and saved examples using your IDE's local storage mechanism (`PropertiesComponent`).
- **Providing Plugin Functionality**: To pre-fill parameters, resolve `$ref` references, and generate test reports as described in the Plugin documentation.

**We do not:**
- Collect, transmit, or store your API request data on any remote server operated by us.
- Use your data for training machine learning models.
- Share your data with third parties (except as necessary to deliver the request to the target API server you specify).
- Log or retain your request history beyond what you explicitly save as examples.

---

## 3. Data Storage and Security

### 3.1 Local Storage

All data processed by the Plugin is stored locally on your machine:

- **Authentication Tokens**: Stored using the JetBrains IDE's `PropertiesComponent` mechanism, persisted in the IDE configuration directory on your local file system.
- **Saved Examples**: Stored as JSON files either in the Plugin's global config directory or within your project directory (as configured in the Plugin settings).
- **Environment Settings**: Stored locally within your IDE's configuration.

> ⚠️ **Important**: Authentication tokens are stored in plain text within the IDE's configuration directory. We recommend treating them with the same level of care as your IDE settings and other credentials on your machine.

### 3.2 Data in Transit

When you send an API request through the Plugin, the data is transmitted directly from your IDE to the target server you specify. The Plugin does not route your traffic through any intermediary server. Encryption (HTTPS) depends on the target server's protocol configuration.

### 3.3 Security Measures

We follow industry best practices to secure the Plugin's codebase, including regular security reviews and dependency updates. However, no software is completely immune to security risks. You are responsible for:
- Securing access to your local machine and IDE.
- Managing and rotating authentication tokens appropriately.
- Ensuring that target API servers use secure connections (HTTPS) when handling sensitive data.

---

## 4. Data Sharing and Disclosure

### 4.1 With Third Parties

We do not sell, trade, or rent your personal information to third parties. Data may be disclosed only in the following circumstances:

- **As Required by Law**: If compelled by a valid legal process (subpoena, court order, or applicable law), we may disclose information to the extent required.
- **Protection of Rights**: To enforce our rights, protect our property, or ensure the safety of our users.

### 4.2 API Target Servers

When you send a request through the Plugin, the data you provide (URL, headers, parameters, body) is transmitted to the target API server you have configured. The processing of that data by the target server is governed by that server's own privacy policy. We are not responsible for the data handling practices of third-party API servers.

---

## 5. Data Retention and Deletion

### 5.1 Your Control

You have full control over data stored by the Plugin:

- **Authentication Tokens**: Can be viewed, modified, or deleted at any time via the Plugin's Auth tab or Token Manager interface.
- **Saved Examples**: Can be deleted individually through the Plugin's load/delete interface, or by removing the corresponding JSON files from your file system.
- **All Local Data**: Can be removed by uninstalling the Plugin and deleting its configuration directory.

### 5.2 Uninstallation

When you uninstall the Plugin:
- The Plugin's files are removed from your IDE.
- Token data stored via `PropertiesComponent` may remain in the IDE configuration directory. You can manually clear this by deleting the relevant IDE configuration files.
- Saved examples stored in the project directory (if configured) will remain as part of your project. Delete them manually if desired.

### 5.3 No Server-Side Data

Since we do not operate any server that collects data from the Plugin, there is no server-side data to retain or delete.

---

## 6. Children's Privacy

The Plugin is not directed at individuals under the age of 13 (or the applicable age of consent in your jurisdiction). We do not knowingly collect personal information from children. If you believe a child has provided us with personal data, please contact us, and we will take steps to investigate and address the issue.

---

## 7. International Users

### 7.1 Governing Law

This Privacy Policy shall be governed by and construed in accordance with the laws of the **People's Republic of China**, without regard to its conflict of law provisions.

### 7.2 Cross-Border Data Transfers

The Plugin operates locally on your machine. To the extent that any data transmission occurs (e.g., API requests sent to servers in other jurisdictions), such transmission is initiated and controlled by you. We do not transfer your data across borders for our own purposes.

### 7.3 GDPR, CCPA, and Other Regulations

If you are located in the European Economic Area (EEA), the United Kingdom, California, or other jurisdictions with specific data protection regulations:

- **Data Controller**: APICue Development Team (contact details below) acts as the data controller for the limited processing described in this policy.
- **Legal Basis**: Our processing is based on your consent (when you enter and send data) and our legitimate interest in providing the Plugin's functionality.
- **Your Rights**: You have the right to access, correct, delete, or port your data. Since all data resides on your local machine, you can exercise these rights directly through the Plugin interface or by managing the local files.
- **CCPA**: As we do not sell personal information, the CCPA's right to opt out of sale does not apply.

---

## 8. Changes to This Privacy Policy

We may update this Privacy Policy from time to time to reflect changes in our practices, legal requirements, or the Plugin's functionality. Updates will be posted at:

- **Website**: [https://www.apicue.com/privacy](https://www.apicue.com/privacy) (or successor URL)
- **Repository**: The policy is maintained in the Plugin's documentation repository

We encourage you to review this Privacy Policy periodically. Material changes will be communicated via the Plugin's description on JetBrains Marketplace or through the Plugin's update channel. Your continued use of the Plugin after changes take effect constitutes your acceptance of the updated policy.

---

## 9. Contact Us

If you have any questions, concerns, or requests regarding this Privacy Policy or our data practices, please contact us:

| Method | Details |
|--------|---------|
| **Email** | [api-cue@gmail.com](mailto:api-cue@gmail.com) |
| **Website** | [https://www.apicue.com](https://www.apicue.com) |
| **Plugin Marketplace** | [JetBrains Marketplace — APICue](https://plugins.jetbrains.com/plugin/32438-apicue) |

We will acknowledge receipt of your inquiry within **48 hours** and respond as promptly as possible.

---

## 10. Related Documents

- [Plugin License Agreement (EULA)](../LICENSE)
- [Security Policy](../SECURITY.md)
- [Frequently Asked Questions](faq.md)

---

*APICue Development Team*  
*Email: api-cue@gmail.com*  
*Website: https://www.apicue.com/*
