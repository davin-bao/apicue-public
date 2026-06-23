# APICue — 从 OpenAPI YAML 文件直接测试 API

**在 IDE 中直接从 OpenAPI 3.0 YAML 定义测试你的 REST API。**

APICue 是一款 IntelliJ IDEA 插件，弥合了 API 规范与 API 测试之间的鸿沟。无需维护单独的 `.http` 文件，也无需切换到 Postman 等外部工具，你可以在 YAML 编辑器中直接发送请求、查看响应并迭代你的 API 设计。

> ⚠️ **APICue 是一款商业插件**，通过 JetBrains Marketplace 分发。本仓库包含文档、使用指南和公开资料。

---

## ✨ 功能特性

### ▶ 一键测试 — 编辑器图标触发
在每个 OpenAPI YAML 文件的 `get:`、`post:`、`put:`、`delete:` 和 `patch:` 操作旁显示绿色运行按钮。点击即可打开测试面板。

### 🖥 专属工具窗口
右侧工具窗口提供完整的测试界面：环境选择器、认证配置、请求编辑器（参数 / 请求头 / 请求体 三个标签页）以及分栏响应查看器。保持上下文不中断——无需弹出窗口或对话框。

### 🔐 安全方案自动发现
自动读取 OpenAPI 规范中的 `components.securitySchemes` 和 `security` 要求，生成正确的认证请求头（Bearer JWT、Basic Auth、header/query/cookie 中的 API Key）并自动填入。

### 🌍 多环境服务器选择
支持每个 YAML 文件配置多个 `servers`。最后选择的 URL 按文件记忆，切换 YAML 文件时自动恢复上次选择。

### 📋 智能参数预填
查询参数、请求头和请求体从 `example`、`default` 和 schema 属性值中自动预填——遵循明确的优先级规则。

### 📝 保存与加载示例
将有效的请求参数和响应数据回写到 YAML 文件作为 OpenAPI `example`。之后可重新加载以实现可复现的测试。

### 🔑 令牌管理
通过内置的令牌管理器按环境管理令牌（JWT、API Key 等）。令牌使用 IDE 的密码安全机制安全存储。

### 🔗 $Ref 跨文件引用解析
完整解析跨 YAML 文件的 `$ref` 引用（如 `$ref: 'model.yml#/components/schemas/User'`），支持缓存和循环引用检测。

### 📄 导出测试报告
将保存的示例导出为结构化的 HTML 或 Markdown 报告，支持自定义模板，适合分享、文档或复盘。

### 🌐 国际化（i18n）
支持英文和中文界面，自动匹配 IDE 语言设置。

---

## 📸 截图

| 主测试面板 | 响应查看器 |
|---|---|
| ![主面板](screenshots/1.png) | ![响应查看器](screenshots/2.png) |

---

## 🚀 快速开始

1. **安装**插件：从 JetBrains Marketplace 安装（设置 → 插件 → Marketplace → 搜索 "APICue"）
2. **打开**任意 OpenAPI 3.0 YAML 文件
3. **点击**路径操作旁的 ▶ 图标
4. **选择**目标服务器环境，查看/编辑参数，配置认证
5. **点击**"发送请求"并实时查看响应

---

## 📦 系统要求

- **IntelliJ IDEA** 2024.1+（Ultimate 或 Community）
- **OpenAPI** 3.0 YAML 文件

### 内置依赖
| 库 | 版本 | 用途 |
|---------|---------|------|
| OkHttp | 4.12 | HTTP 客户端 |
| SnakeYAML | 2.2 | YAML 解析 |
| Kotlinx Coroutines | — | 异步请求处理 |

---

## 📚 文档目录

- [快速开始指南](docs/quickstart.md)
- [功能详解](docs/features.md)
- [常见问题](docs/faq.md)
- [更新日志](CHANGELOG.md)

---

## 🏷 Marketplace 信息

- **分类**: Web Services / REST · Tools / Integration
- **标签**: `OpenAPI` · `REST API` · `YAML` · `API Testing` · `Swagger`
- **兼容**: IntelliJ IDEA 2024.1+

---

## 📄 许可证

本仓库中的文档和资料使用 MIT 许可证。APICue 插件本身是商业产品，通过 JetBrains Marketplace 分发，使用独立的许可协议。

---

## 📬 联系方式

- **网站**: [https://www.apicue.com](https://www.apicue.com)
- **邮箱**: [api-cue@gmail.com](mailto:api-cue@gmail.com)
