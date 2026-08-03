# Changelog

## [2026.8.3] - 2026-08-03

### Added
- **History panel**: 请求自动记录，表格化列表展示，双击回填完整请求（auth、params、headers、body、响应）。
- **Examples tab**: 表格化 Example 列表，内联改名/删除/搜索，一键填充。
- **All Endpoints tab**: JCheckBox 列表、行号导航、导出、自动加载。
- **i18n**: 19 个新文案翻译成 9 种语言（JA/KO/DE/ES/FR/PT/RU/TR/VI）。

### Changed
- **语言切换**: Properties-based I18n，切换语言后面板立即重载。

### Fixed
- **History 回填**: 同步更新 endpointState/currentContext、清空替换 params/headers、环境匹配。
- **i18n**: 页签名称、列头、tooltip、环境显示的本地化问题。
- **Headers 空行** 残留问题。

---

## [2026.7.14] - 2026-07-14

### Added
- **flexmark Markdown→HTML converter**: Replaced hand-rolled regex parser with flexmark 0.64.8 for correct CommonMark/GFM rendering.
- **Right-click YAML context menu**: Export Markdown/HTML API Doc from `.yml`/`.yaml` file right-click.
- **Shared export utility**: Tool window button and right-click menu share the same export logic.
- **Enum anchor links**: Enum fields in data structure tables link to their detail rows.
- **Type alias normalization**: `int`→`integer`, `float`/`double`→`number`, `bool`→`boolean`, `str`→`string`.
- **Full i18n for API Document Export**: 24 new i18n keys covering all table headers, constraints, auth types, and labels.

### Changed
- **Response data structure**: "Required" column removed (request body structure keeps it).
- **Test Report TOC**: Shows `[METHOD] /path` format.
- **Select All/Deselect All label**: Shows visible count when search filter is active.

### Fixed
- **Plugin load error**: Removed invalid `<tags>` element from `plugin.xml`.
- **EDT threading**: Actions now declare `ActionUpdateThread.BGT`.
- **Right-click menu enabled**: Fixed grayed-out menu for YAML files.

---

## [2026.7.3] - 2026-07-06

### Added
- **API Document Export**: Export OpenAPI/YAML documentation as Markdown or HTML from the tool window or right-click menu.
- **Export Dialog**: Select endpoints with search/filter, set document title.
- **Markdown/HTML Export**: Structured output with TOC, tables, code blocks, schema details.
- **Settings**: Configurable content sections in Settings → Tools → APICue.
- **i18n**: Chinese and English support.

---

## [1.0.7] - 2026-07-03

### Fixed
- **Deprecated API removed**: Replaced `PluginManager.getPlugin(PluginId)` with a compile-time version constant.

---

## [1.0.6] - 2026-06-24

### Fixed
- **Internal API → Public API**: Replaced `PluginManagerCore.getPlugin(PluginId)` with `PluginManager.getPlugin(PluginId)`.
- **Deprecated API migration**: Replaced old `addBrowseFolderListener` overload with `addBrowseFolderListener(TextBrowseFolderListener)`.

---

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
