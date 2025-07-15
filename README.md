# CodeGlide GitHub Action

Generate MCP (Model Context Protocol) servers from your API source code using CodeGlide. 

## Usage

```yaml
- name: CodeGlide MCP Generator
  uses: CodeGlide/codeglide-mcpgen@v1.0.0
  with:
    input_directory: '.'  # Optional, defaults to root directory
```
**Sample Workflow:**  [docs/workflow.yml](https://github.com/CodeGlide/codeglide-mcpgen/blob/main/docs/sample-workflow.yml) 

## Output

- **Artifact**: `generated-mcp` containing MCP server

## Features

- Generates Swagger specifications from source code
- Creates MCP servers in seconds
- Flexible input directory (defaults to root)
- Output artifact upload

