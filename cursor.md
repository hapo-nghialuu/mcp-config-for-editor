# Config cho Cursor

## STEP 1: Clone/Download Figma Context MCP

Clone hoặc download theo link: [https://github.com/GLips/Figma-Context-MCP](https://github.com/GLips/Figma-Context-MCP)


## STEP 2: Lấy Figma API key

Nếu chưa có FIGMA_API_KEY thì truy cập link sau để lấy api key.
[https://www.figma.com/developers/api#access-tokens](https://www.figma.com/developers/api#access-tokens)

## STEP 3: Create new MCP server

Vào Cursor settings → Tools & Intergrations → New MCP Server

## STEP 4: Edit file mcp.json vừa được mở ra theo config

```json
{
  "mcpServers": {
    "Framelink Figma MCP": {
      "command": "node",
      "args": ["/đường_dẫn_đến_thư_mục_cha_của_figma_context_vừa_clone/figma-mcp/dist/cli.js", "--figma-api-key=FIGMA_API_KEY", "--stdio"],
      "env": {
        "FIGMA_API_KEY": "your_figma_api_key"
      }
    }
  }
}
```

## STEP 5: Active MCP server và thử nghiệm thôi