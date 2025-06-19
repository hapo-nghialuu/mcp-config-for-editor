# Hướng dẫn cấu hình Figma MCP cho Augment Code

Đây là hướng dẫn từng bước để cấu hình Figma Context MCP (Model Context Protocol) trong Augment Code.

---

## 1. Tải về Figma Context MCP

Clone hoặc tải mã nguồn từ repository GitHub:
[https://github.com/GLips/Figma-Context-MCP](https://github.com/GLips/Figma-Context-MCP)

```bash
git clone https://github.com/GLips/Figma-Context-MCP.git figma-mcp
cd figma-mcp
```

## 2. Cài đặt và build project

Cài đặt dependencies và build project:

```bash
npm install
npm run build
```

## 3. Lấy Figma API Key

- Truy cập vào trang cài đặt của Figma để tạo một **Personal Access Token**.
- Link truy cập: [https://www.figma.com/developers/api#access-tokens](https://www.figma.com/developers/api#access-tokens)
- Lưu lại API key này để sử dụng ở bước tiếp theo.

## 4. Cấu hình MCP Server trong Augment Code

### Phương pháp 1: Sử dụng Augment Settings Panel (Khuyến nghị)

- Mở VS Code với extension Augment Code đã cài đặt
- Click vào biểu tượng **gear (⚙️)** ở góc trên bên phải của Augment panel
- Tìm phần **"MCP servers"**
- Click nút **"+"** để thêm server mới

### Phương pháp 2: Chỉnh sửa settings.json

- Press **Cmd/Ctrl + Shift + P**
- Hoặc vào hamburger menu trong Augment panel
- Chọn **"Edit Settings"**
- Under Advanced, click **"Edit in settings.json"**

## 5. Thêm cấu hình Figma MCP Server

### Nếu sử dụng Settings Panel:

Điền thông tin sau:
- **Name**: `Framelink Figma MCP`
- **Command**: `node /đường_dẫn_đến_thư_mục_figma_context_vừa_clone/dist/cli.js --figma-api-key=YOUR_FIGMA_API_KEY --stdio`

### Nếu sử dụng settings.json:

Thêm đoạn mã JSON sau vào file settings.json:

**Lưu ý:**

- Thay thế `/đường_dẫn_đến_thư_mục_figma_context_vừa_clone/` bằng đường dẫn tuyệt đối đến thư mục bạn vừa tải về ở Bước 1.
- Thay thế `YOUR_FIGMA_API_KEY` bằng API key bạn đã lấy ở Bước 3.

```json
{
  "augment.advanced": {
    "mcpServers": [
      {
        "name": "Framelink Figma MCP",
        "command": "node",
        "args": [
          "/đường_dẫn_đến_thư_mục_figma_context_vừa_clone/dist/cli.js",
          "--figma-api-key=YOUR_FIGMA_API_KEY",
          "--stdio"
        ]
      }
    ]
  }
}
```

## 6. Ví dụ cấu hình cụ thể

Giả sử bạn đã clone project vào thư mục `/Users/username/figma-mcp` và có API key `figd_abc123xyz`, cấu hình sẽ như sau:

```json
{
  "augment.advanced": {
    "mcpServers": [
      {
        "name": "Framelink Figma MCP",
        "command": "node",
        "args": [
          "/Users/username/figma-mcp/dist/cli.js",
          "--figma-api-key=figd_abc123xyz",
          "--stdio"
        ]
      }
    ]
  }
}
```

## 7. Kích hoạt và thử nghiệm

- Lưu lại file cấu hình
- **Khởi động lại VS Code** để áp dụng thay đổi
- Mở Augment Agent trong VS Code
- Thử nghiệm bằng cách paste một Figma link vào chat:

```
Hãy phân tích design này: https://www.figma.com/file/ABC123/My-Design?node-id=1%3A2
```

## 8. Xác minh cấu hình thành công

Bạn sẽ biết cấu hình thành công khi:

- Augment Agent có thể truy cập và phân tích Figma files
- Không có lỗi kết nối MCP server
- AI có thể trả lời chi tiết về layout, colors, typography từ Figma design

## 9. Troubleshooting

### Lỗi thường gặp:

**"Command not found" hoặc "Cannot find module":**
- Kiểm tra đường dẫn đến `cli.js` có chính xác không
- Đảm bảo đã chạy `npm run build` thành công

**"Invalid API key":**
- Kiểm tra lại Figma API key
- Đảm bảo API key có quyền truy cập vào file Figma

**"MCP server not responding":**
- Restart VS Code
- Kiểm tra syntax JSON trong settings.json
- Kiểm tra logs trong VS Code Developer Console

### Test thủ công:

Để kiểm tra MCP server hoạt động độc lập:

```bash
cd /đường_dẫn_đến_thư_mục_figma_context_vừa_clone
node dist/cli.js --figma-api-key=YOUR_API_KEY --stdio
```

---

**Chúc bạn sử dụng thành công Figma MCP với Augment Code!** 🎉
