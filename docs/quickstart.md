# Quick Start Guide

This guide walks you through testing your first API endpoint with APICue.

## Prerequisites

- IntelliJ IDEA 2024.1+ (Ultimate or Community)
- An OpenAPI 3.0 YAML file (`.yaml` or `.yml`)

## Step 1: Install APICue

1. Open IntelliJ IDEA
2. Go to **Settings/Preferences → Plugins → Marketplace**
3. Search for **"APICue"**
4. Click **Install**
5. Restart your IDE

Alternatively, download the plugin from the [JetBrains Marketplace page](https://plugins.jetbrains.com/) and install via **Settings → Plugins → ⚙ → Install Plugin from Disk**.

## Step 2: Open an OpenAPI YAML File

Open any OpenAPI 3.0 YAML file in your project. APICue automatically detects OpenAPI files and activates when a YAML file is opened.

### Minimal OpenAPI Example

```yaml
openapi: "3.0.3"
info:
  title: Pet Store API
  version: "1.0"
servers:
  - url: https://api.example.com/v1
    description: Production
paths:
  /pets:
    get:
      summary: List all pets
      operationId: listPets
      parameters:
        - name: limit
          in: query
          schema:
            type: integer
          example: 20
      responses:
        "200":
          description: A list of pets
```

## Step 3: Click the ▶ Gutter Icon

Look at the left gutter of your YAML editor. Green ▶ run icons appear next to each HTTP method (`get:`, `post:`, `put:`, `delete:`, `patch:`).

Click a ▶ icon to open the **APICue Tester** tool window on the right side of your IDE.

## Step 4: Configure Your Request

The APICue Tester panel opens with three main sections:

### Top — Header Bar
- **Server selector**: Choose the target server URL (from your OpenAPI `servers` list)
- **Send Request** button: Execute the HTTP request
- **Save as Example** button: Save current request/response as an OpenAPI example
- **Load Example** dropdown: Load a previously saved example

### Middle — Request Editor (4 Tabs)
| Tab | Description |
|-----|-------------|
| **Auth** | Configure authentication (auto-detected from OpenAPI security schemes) |
| **Params** | View and edit query parameters (pre-filled from schema) |
| **Headers** | View and edit HTTP headers (auto-generated auth headers + Content-Type) |
| **Body** | Edit JSON request body (for POST, PUT, PATCH) |

### Bottom — Result Panel
After sending a request, the bottom panel shows:
- **Left (Request Info)**: URL, headers, and body that were sent
- **Right (Response Info)**: Status code, duration, response headers, and response body

## Step 5: Send Your First Request

1. **Select** your target server from the dropdown
2. **Review** the pre-filled parameters (adjust if needed)
3. **Configure** authentication if required
4. Click **Send Request**

The response appears instantly in the bottom panel with:
- HTTP status code and description
- Response duration in milliseconds
- Response headers
- Syntax-highlighted response body

## Next Steps

- [Explore all features](features.md)
- [Read the FAQ](faq.md)
- Check the [Changelog](../CHANGELOG.md) for version history
