# Getting Started with CodeGlide

This guide will help you generate your MCP server using CodeGlide in just a few minutes.

## Prerequisites

- Git repository with API source code

## Step 1: Prepare Your API Source Code

Ensure your repository contains:

- API endpoint definitions
- Route handlers
- API documentation (optional but helpful)

## Step 2: Use Codeglide GitHub Actions 

Marketplace listing: https://github.com/marketplace/actions/codeglide-mcp-generator

#### 1. Create Workflow File

Create `.github/workflows/codeglide-generate-mcp.yml` in your repository:

```yaml
name: Generate MCP Server

on:
  workflow_dispatch:
    inputs:
      input_directory:
        description: 'Directory containing API source code (relative to repo root)'
        required: false
        type: string
        default: '.'

jobs:
  generate-mcp:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repository
      uses: actions/checkout@v4
      
    - name: Generate MCP Server
      uses: CodeGlide/codeglide-mcpgen@v1.0.0
      with:
        input_directory: ${{ inputs.input_directory || '.' }}
```

#### 2. Run the Workflow

1. Go to your repository on GitHub
2. Click **Actions** tab
3. Select **Generate MCP Server** workflow
4. Configure inputs (or use defaults)
5. Click **Run workflow**

#### 3. Download Generated MCP Server

1. Wait for workflow completion (usually 2-5 minutes)
2. Click on the completed workflow run
3. Download the **generated-mcp** artifact
4. Extract and explore your MCP server!

### Key Components

#### 1. MCP Tools (`tools/` directory)
Each API endpoint becomes an MCP tool that AI agents can call:

#### 2. Configuration (`config/`)
```go
type Config struct {
    ServerName    string `json:"server_name"`
    ServerVersion string `json:"server_version"`
    BaseURL       string `json:"base_url"`
    AuthMethod    string `json:"auth_method"`
}
```

#### 3. Models (`models/`)
Auto-generated data structures based on your API schemas.

## Step 4: Test Your MCP Server

### 1. Run the Server Locally

```bash
cd generated-mcp
go run main.go
```

### 2. Connect with MCP Client

Use any MCP-compatible client to test:

```bash
# Example using Claude Desktop/cursor/...
# Add to your MCP configuration:
{
  "servers": {
    "your-api": {
      "command": "go",
      "args": ["run", "/path/to/generated-mcp/main.go"]
    }
  }
}
```

### 3. Test Tool Calls

Your AI agent can now call your API functions:

```
User: List all users from the API

AI: I'll call the get_users tool to retrieve the user list.
[Tool calls the generated MCP server]
Here are the users from your API: ...
```

## Need Help?

- **Issues**: [Report bugs](https://github.com/CodeGlide/codeglide-mcpgen/issues)
- **Questions**: [GitHub Discussions](https://github.com/CodeGlide/codeglide-mcpgen/discussions)

---
