# Feature Details

## 1. Gutter Icon Triggers

APICue adds green ▶ run buttons to the left gutter of your YAML editor for every OpenAPI path operation. Clicking one opens the APICue Tester tool window pre-configured for that operation.

**Supported methods**: `GET`, `POST`, `PUT`, `DELETE`, `PATCH`

The gutter icon is context-aware — it only appears on YAML files that contain valid OpenAPI 3.0 path definitions, and only on lines that are actual HTTP method keys.

---

## 2. APICue Tester ToolWindow

### Top — Header Bar
| Element | Description |
|---------|-------------|
| **Method + Path** | Shows the current operation (e.g., `[GET] /api/pets`) |
| **Server Selector** | Dropdown to choose the target server URL from the YAML file's `servers` block |
| **Send Request** | Executes the HTTP request |
| **Save as Example** | Saves current parameters + response back to the YAML file as an OpenAPI example |
| **Load Example** | Dropdown to select and load a previously saved example |
| **Export Report** | Opens the export dialog to generate HTML/Markdown reports |

### Middle — Request Editor (4 Tabs)

#### Auth Tab
- **Auto-discovers** security schemes from `components.securitySchemes` and `security` requirements
- Displays each required auth scheme with a text area and save button
- **Supported auth types**:

| OpenAPI Type | Generated Header |
|---|---|
| `http` / `bearer` | `Authorization: Bearer {token}` |
| `http` / `basic` | `Authorization: Basic {token}` |
| `apiKey` / `in: header` | `{name}: {token}` |
| `apiKey` / `in: query` | Added to query parameters |
| `apiKey` / `in: cookie` | `Cookie: {name}={token}` |
| `oauth2` / `openIdConnect` | `Authorization: Bearer {token}` |

- Shows "No authentication required" for endpoints without security requirements
- Supports `{{variable}}` syntax in token fields for dynamic values

#### Params Tab
- Table of query parameters extracted from `parameters[in=query]`
- Each row: Name | Value | Required | In
- Pre-filled from `example` → `default` → schema property default values
- `+` / `-` buttons to add or remove rows
- Also handles path parameters (`in=path`), header parameters (`in=header`), and cookie parameters (`in=cookie`)

#### Headers Tab
- Table of HTTP headers
- Auto-generated headers from security schemes (Authorization, etc.)
- `Content-Type: application/json` auto-added when request body is present
- Pre-filled from `parameters[in=header]` definitions
- Editable and extendable

#### Body Tab
- JSON request body editor (for POST, PUT, PATCH)
- Pre-filled from `requestBody.content.application/json.schema` with priority:
  1. Schema-level `example` (highest priority)
  2. Schema property-level `example` values
  3. Schema `default` values
  4. Type-based defaults (empty object `{}`, `""`, `0`, `false`)
- **Format JSON** button to beautify the editor content
- Syntax highlighting
- Supports `multipart/form-data` with file upload fields

### Bottom — Result Panel

| Split | Content |
|-------|---------|
| **Left (Request Info)** | Full URL, sent headers, sent body (syntax highlighted) |
| **Right (Response Info)** | Status code + description, duration (ms), response headers, response body (syntax highlighted, collapsible) |

---

## 3. Save & Load Examples

**Save** — Click the 💾 button to save the current request parameters and response payload back to the OpenAPI YAML file as an `example` field.

**Load** — Use the history dropdown to select and load a previously saved example. All parameters, headers, body, and auth configuration are restored to the panel.

---

## 4. Token Management

Access the Token Manager via the Token Management button in the Auth tab.

- **Store tokens** per environment (production, staging, etc.)
- **Supported token types**: JWT, API Key, Basic Auth credentials
- **Secure storage**: Tokens are persisted using the IDE's `PropertiesComponent` with per-environment keys
- **Auto-fill**: Detected security schemes automatically load the appropriate token

---

## 5. Settings Panel

Configure APICue via **Settings → Tools → APICue**:

| Setting | Description |
|---------|-------------|
| **Export Format** | Choose HTML or Markdown as default export format |
| **Export Fields** | Select which sections to include in reports |
| **Custom Template** | Provide a local file path for custom HTML report templates |

---

## 6. $ref Cross-File Resolution

APICue fully resolves `$ref` references across YAML files:

```yaml
$ref: 'models/User.yml#/components/schemas/User'
$ref: '#/components/schemas/Order'
$ref: '../common/Pagination.yml'
```

**Features**:
- Cross-file resolution with relative and absolute paths
- Caching for performance
- Circular-reference detection to prevent infinite loops

---

## 7. Internationalization (i18n)

APICue supports:
- **English** — Default UI language
- **Chinese (中文)** — Full Chinese localization

The plugin automatically matches your IDE's language setting. No manual configuration needed.

---

## 8. Export Test Report

Saved test examples can be exported as structured reports.

**How to Export**:
1. Click the 📤 (Export) button in the APICue Tester toolbar
2. Select examples in the dialog (by time or by path)
3. Set a report title
4. Choose save location

**Output Formats**:
| Format | Use Case |
|--------|----------|
| **HTML** | Self-contained styled page with syntax-highlighted code blocks, collapsible sections, and table of contents. Supports custom templates. |
| **Markdown** | Plain-text format suitable for version control, code review comments, or pasting into docs/wiki. |

**Configurable Fields**:
`Environment` · `Parameters` · `Request Headers` · `Request Body` · `Response Headers` · `Response Body` · `Table of Contents`

> `Method` and `Path` are always included regardless of field selection.
