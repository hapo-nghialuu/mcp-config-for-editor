# Hướng dẫn cấu hình Figma MCP cho Windsurf

Đây là hướng dẫn từng bước để cấu hình Figma Context MCP (Model Context Protocol) trong Windsurf.

---

## 1. Tải về Figma Context MCP

Clone hoặc tải mã nguồn từ repository GitHub:
[https://github.com/GLips/Figma-Context-MCP](https://github.com/GLips/Figma-Context-MCP)

## 2. Lấy Figma API Key

- Truy cập vào trang cài đặt của Figma để tạo một **Personal Access Token**.
- Link truy cập: [https://www.figma.com/developers/api#access-tokens](https://www.figma.com/developers/api#access-tokens)
- Lưu lại API key này để sử dụng ở bước tiếp theo.

## 3. Cấu hình MCP Server trong Windsurf

- Mở file cấu hình MCP của Windsurf. Thông thường, bạn có thể tìm thấy tùy chọn này trong phần cài đặt (Settings) hoặc bạn cần phải tạo/chỉnh sửa một file JSON cấu hình trong thư mục cài đặt của Windsurf.

## 4. Thêm cấu hình Figma MCP Server

Thêm đoạn mã JSON sau vào file cấu hình MCP của bạn.

**Lưu ý:**

- Thay thế `/đường_dẫn_đến_thư_mục_figma_context_vừa_clone/` bằng đường dẫn tuyệt đối đến thư mục bạn vừa tải về ở Bước 1.
- Thay thế `YOUR_FIGMA_API_KEY` bằng API key bạn đã lấy ở Bước 2.

```json
{
  "mcpServers": {
    "Framelink Figma MCP": {
      "command": "node",
      "args": [
        "/đường_dẫn_đến_thư_mục_figma_context_vừa_clone/dist/cli.js",
        "--figma-api-key=YOUR_FIGMA_API_KEY",
        "--stdio"
      ],
      "env": {
        "FIGMA_API_KEY": "YOUR_FIGMA_API_KEY"
      }
    }
  }
}
```

## 5. Kích hoạt và thử nghiệm

- Lưu lại file cấu hình.
- Khởi động lại Windsurf (nếu cần) để áp dụng thay đổi.
- Bây giờ bạn có thể bắt đầu sử dụng 

# Let's Code
