# Frequently Asked Questions

## General

### What is APICue?
APICue is an IntelliJ IDEA plugin that lets you test REST APIs directly from OpenAPI 3.0 YAML files. It reads your API specification and provides a full testing interface within the IDE.

### Is APICue free?
APICue is a commercial plugin available on JetBrains Marketplace. Check the Marketplace page for current pricing.

### Which IntelliJ products are supported?
APICue supports IntelliJ IDEA 2024.1+ (both Ultimate and Community editions). It requires the YAML plugin (`org.jetbrains.plugins.yaml`), which is bundled with IntelliJ IDEA.

### Does APICue support OpenAPI 2.0 (Swagger)?
Currently, APICue only supports OpenAPI 3.0 YAML files. OpenAPI 2.0 (Swagger) support may be added in a future release.

---

## Installation

### How do I install APICue?
Go to **Settings/Preferences → Plugins → Marketplace**, search for "APICue", and click Install. Restart your IDE after installation.

### Can I install it offline?
Yes. Download the plugin ZIP from JetBrains Marketplace, then go to **Settings → Plugins → ⚙ → Install Plugin from Disk**.

### Why don't I see the plugin in the Marketplace?
Make sure you're searching in the **Marketplace** tab (not Installed), and that you're running IntelliJ IDEA 2024.1 or later.

---

## Usage

### Gutter icons not showing?
- Ensure your file has a `.yaml` or `.yml` extension
- Verify your YAML file follows the OpenAPI 3.0 structure with valid `paths` and HTTP methods
- Make sure the YAML plugin is enabled in your IDE
- Try reopening the file or restarting the IDE

### Request fails with connection error?
- Check your internet connection
- Verify the server URL is correct and accessible
- If using a local server, ensure it's running
- Check if your proxy/firewall is blocking the connection
- For HTTPS endpoints, verify SSL certificate validity

### Tokens not persisting?
- Tokens are stored per environment — make sure you've selected the correct environment
- Check that you clicked the 💾 save button after entering the token
- Try clearing and re-entering the token

### Parsing errors in YAML?
- Validate your YAML file with an external validator (e.g., [swagger.io](https://editor.swagger.io/))
- Check for common issues like incorrect indentation or missing required fields
- Ensure all `$ref` references point to existing files and paths
- Check for circular references in your schema definitions

### Body not sent on DELETE requests?
APICue 1.0.3+ correctly sends body on DELETE requests. If you're on an older version, update the plugin.

### Array type request body not working?
APICue 1.0.3+ correctly handles `type: array` request bodies. Update to the latest version if you encounter this issue.

---

## Data & Privacy

### Where are my tokens stored?
Tokens are stored using your IDE's `PropertiesComponent` mechanism, which persists data in the IDEA configuration directory. Tokens are stored in plain text within the IDE's config — treat them with the same care as your IDE settings.

### Are my requests logged?
APICue does not log or transmit your request data anywhere. All request handling is local within your IDE.

### Can I export my test data?
Yes. APICue supports saving request/response examples back to your YAML files and exporting test reports as HTML or Markdown files.

---

## Technical

### What HTTP library does APICue use?
APICue uses **OkHttp 4.12** for all HTTP communication.

### Does APICue support proxy settings?
APICue uses your system's default proxy settings via OkHttp. Configure your proxy in IntelliJ IDEA's **Settings → Appearance & Behavior → System Settings → HTTP Proxy**.

### Does APICue support authentication?
Yes. APICue auto-discovers security schemes from your OpenAPI spec and supports Bearer JWT, Basic Auth, API Key (header/query/cookie), and OAuth2/OpenID Connect tokens.

### Can I customize the HTML report template?
Yes. In **Settings → Tools → APICue**, switch from "Built-in" to "Custom" and provide a local file path. The template uses `{{title}}`, `{{generatedAt}}`, `{{count}}`, `{{toc}}`, and `{{content}}` placeholders.

---

## Troubleshooting

### Plugin doesn't work after update?
Try restarting your IDE. If the issue persists, go to **Settings → Plugins**, disable and re-enable APICue.

### How to report a bug?
Open an issue on GitHub or contact us via email. Include:
- APICue version
- IntelliJ IDEA version
- Steps to reproduce
- Expected vs actual behavior

### How to request a feature?
Feature requests are welcome! Contact us at [api-cue@gmail.com](mailto:api-cue@gmail.com) with your suggestion.
