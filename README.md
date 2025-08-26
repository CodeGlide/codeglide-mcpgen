# CodeGlide GitHub Action

Generate MCP (Model Context Protocol) servers from your API source code using CodeGlide. 

## Usage

```yaml
- name: CodeGlide MCP Generator
  uses: CodeGlide/codeglide-mcpgen@v1.0.9
  with:
    input_directory: ${{ inputs.input_directory }}
    custom_headers: ${{ inputs.custom_headers }}
    create_pr: ${{ inputs.create_pr }}
    create_branch_and_commit: ${{ inputs.create_branch_and_commit }}

```
**Sample Workflow:**  [docs/workflow.yml](https://github.com/CodeGlide/codeglide-mcpgen/blob/main/docs/sample-commit-workflow.yml) 

**Marketplace Listing:** https://github.com/marketplace/actions/codeglide-mcp-generator

## Output

- **Artifact**: `generated-mcp` containing MCP server

## Features

- Generates Swagger specifications from source code
- Creates MCP servers in seconds
- Flexible input directory (defaults to root)
- Output artifact upload

