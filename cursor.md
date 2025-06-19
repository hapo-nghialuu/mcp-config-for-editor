# Hướng dẫn cấu hình Figma MCP cho Cursor

Đây là hướng dẫn từng bước để cấu hình Figma Context MCP (Model Context Protocol) trong Cursor.

---

### 1. Tải về Figma Context MCP

Clone hoặc tải mã nguồn từ repository GitHub:
[https://github.com/GLips/Figma-Context-MCP](https://github.com/GLips/Figma-Context-MCP)

### 2. Lấy Figma API Key

- Truy cập vào trang cài đặt của Figma để tạo một **Personal Access Token**.
- Link truy cập: [https://www.figma.com/developers/api#access-tokens](https://www.figma.com/developers/api#access-tokens)
- Lưu lại API key này để sử dụng ở bước tiếp theo.

### 3. Tạo MCP Server mới trong Cursor

- Mở **Settings** của Cursor.
- Điều hướng đến mục **Tools & Integrations**.
- Nhấp vào **New MCP Server**. Thao tác này sẽ mở một file `mcp.json`.

### 4. Cấu hình file `mcp.json`

Chỉnh sửa nội dung file `mcp.json` vừa được mở ra với cấu hình sau.

**Lưu ý:**
- Thay thế `/đường_dẫn_đến_thư_mục_cha_của_figma_context_vừa_clone/` bằng đường dẫn tuyệt đối đến thư mục bạn vừa tải về ở Bước 1.
- Thay thế `your_figma_api_key` bằng API key bạn đã lấy ở Bước 2.

```json
{
  "mcpServers": {
    "Framelink Figma MCP": {
      "command": "node",
      "args": [
        "/đường_dẫn_đến_thư_mục_cha_của_figma_context_vừa_clone/figma-mcp/dist/cli.js",
        "--figma-api-key=FIGMA_API_KEY",
        "--stdio"
      ],
      "env": {
        "FIGMA_API_KEY": "your_figma_api_key"
      }
    }
  }
}
```

### 5. Kích hoạt và thử nghiệm

- Lưu file `mcp.json`.
- Quay lại mục **Tools & Integrations** trong **Settings**.
- Kích hoạt (active) MCP server bạn vừa tạo.
- Bây giờ bạn có thể bắt đầu sử dụng được rồi.

# Let's Code!!!
