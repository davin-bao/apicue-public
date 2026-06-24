# Changelog

## [1.0.5] - 2026-06-24

### Changed
- **IDE compatibility**: Set `until-build` to `*` (wildcard) — plugin now supports all future IDE versions (tested up to 2026.1).

### Fixed
- **Deprecated API migration**: Replaced `JBUI.scale(float)` with `JBUIScale.scale(float)` (2 occurrences) and `ComponentWithBrowseButton.getButton()` with `addActionListener()` (1 occurrence) to eliminate all scheduled-for-removal API usages.

---

## [1.0.4] - 2026-06-20

### Fixed
- **Save/load examples now uses Gson for proper JSON serialization**, fixing all encoding issues with special characters in request body, headers, and response data.

---

## [1.0.3] - 2026-06-15

### Fixed
- **DELETE requests now send body correctly**: `DELETE` requests with a JSON array body (e.g. batch file deletion) were silently having their body dropped because OkHttp's `builder.delete()` (no-arg) never includes a body. Changed to `builder.method("DELETE", body)` so the body is actually sent.
- **Request body array type now sends correctly**: When the OpenAPI schema defines `requestBody` as `type: array`, the generated example JSON array is now properly sent in the HTTP request instead of being treated as an empty body.

---

## [1.0.2] - 2026-06-05

### Added
- **Export Test Report**: New export button in the tool window toolbar. Export saved examples as HTML or Markdown reports with customizable title, field selection, and custom HTML templates.
- **Export Dialog**: Tabbed interface (**By Time** / **By Path**) to browse and select examples.
- **HTML Report**: Built-in styled template with dark code blocks, table of contents, and support for custom templates.
- **Markdown Report**: Clean Markdown output for integration with documentation tools.
- **Configurable Fields**: Choose which sections to include: Environment, Parameters, Request Headers, Request Body, Response Headers, Response Body, and Table of Contents.
- **Settings**: Export format, field checkboxes, and custom template path configurable in **Settings → Tools → APICue**.

### Fixed
- **History record selection now updates header labels** correctly when loading saved examples.
- **Status label now displays** `已填充: [METHOD] /path` after filling from a history record.

---

## [1.0.1] - 2026-06-04

### Fixed
- **Environment selection per-file path**: Each YAML file now correctly remembers its last-selected server URL independently.
- **Multi-project state isolation**: Each IDEA project window maintains its own independent panel state, preventing conflicts when multiple projects are open simultaneously.

### Improved
- **Manual server selection persistence**: User's manual server choice is immediately persisted and preserved when switching between operations.

---

## [1.0.0] - 2026-05-15

### Added
- **OpenAPI 3.0 YAML parsing**: Full YAML parser with `$ref` cross-file resolution, caching, and circular-reference detection.
- **Gutter icon triggers**: Green ▶ run buttons on every `get:`, `post:`, `put:`, `delete:`, and `patch:` operation.
- **Dedicated ToolWindow panel**: Right-side "APICue Tester" tool window with environment selector, auth panel, request editor (Params / Headers / Body), and response viewer.
- **Security scheme auto-discovery**: Auto-generates Bearer JWT, Basic Auth, and API Key headers from `components.securitySchemes`.
- **Token management**: Per-environment token storage via IDE's secure storage.
- **Smart parameter pre-fill**: Auto-fills from `example`, `default`, and schema property values.
- **Save & Load examples**: Write request/response payloads back to YAML as OpenAPI examples.
- **Multi-environment server selection**: Last-selected URL remembered per-project.
- **Internationalization**: English and Chinese UI, auto-detects IDE language setting.
