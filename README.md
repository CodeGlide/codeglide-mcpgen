# CodeGlide GitHub Action

Generate MCP (Model Context Protocol) servers from your API source code using CodeGlide. 

## Usage

```yaml
- name: Generate MCP Server
  uses: CodeGlide/codeglide-mcpgen@v1.0.0
  with:
    input_directory: '.'  # Optional, defaults to root directory
```

## Output

- **Artifact**: `generated-mcp` containing MCP server

## Features

- Generates Swagger specifications from source code
- Creates MCP servers in seconds
- Flexible input directory (defaults to root)
- Output artifact upload

---
