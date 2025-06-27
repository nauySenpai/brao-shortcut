# Discord Selfbot với Shortcuts 🚀

Một selfbot Discord mạnh mẽ hỗ trợ **2 loại shortcuts**:
- **Full Shortcuts**: Thay thế toàn bộ tin nhắn
- **Partial Shortcuts**: Thay thế một phần tin nhắn (như `.wsel` → `.waifu-select`)

## 🚀 Cài đặt nhanh

1. **Cài đặt Node.js** (phiên bản 16+)
2. **Clone/Download** project này
3. **Cài dependencies**:
```bash
npm install
```
4. **Cấu hình token** trong `config.json`
5. **Chạy bot**:
```bash
npm start
```

## ⚙️ Cấu hình

### 1. 🔑 Lấy Discord Token
1. Mở **Discord Web** (discord.com)
2. Nhấn **F12** → tab **Network**
3. Gửi tin nhắn bất kỳ
4. Tìm request **"messages"**
5. Copy giá trị **"authorization"** trong Headers

### 2. 📝 File config.json
```json
{
  "token": "YOUR_DISCORD_ACCOUNT_TOKEN_HERE",
  "settings": {
    "deleteOriginalMessage": false,
    "delay": 200,
    "caseSensitive": true
  }
}
```

**Giải thích:**
- `token`: Token Discord của bạn
- `deleteOriginalMessage`: Xóa tin nhắn gốc (true/false)
- `delay`: Độ trễ trước khi gửi (milliseconds)
- `caseSensitive`: Phân biệt hoa/thường (true/false)

### 3. 🎯 File shortcut.json

#### Cách 1: Format đơn giản (sử dụng setting global)
```json
{
  "shortcuts": {
    ".g": ".gold",
    ".p": ".profile"
  },
  "partialShortcuts": {
    ".wsel": ".waifu-select"
  }
}
```

#### Cách 2: Format chi tiết (tùy chỉnh từng shortcut)
```json
{
  "shortcuts": {
    ".wlist": {
      "message": ".waifu-list",
      "deleteOriginal": true
    },
    ".slist": {
      "message": "Danh sách shortcuts...",
      "deleteOriginal": false
    }
  },
  "partialShortcuts": {
    ".wsel": {
      "replacement": ".waifu-select",
      "deleteOriginal": true
    },
    ".g": {
      "replacement": ".gold",
      "deleteOriginal": false
    }
  }
}
```

**Giải thích:**
- `deleteOriginal: true` - Xóa tin nhắn gốc
- `deleteOriginal: false` - Giữ lại tin nhắn gốc
- Nếu không có `deleteOriginal`, sẽ dùng setting từ `config.json`

## 🎮 Cách sử dụng

### 📌 Full Shortcuts (Thay thế toàn bộ)
- Gõ **chính xác** từ khóa
- Ví dụ:
  - Gõ: `.g` → Bot gửi: `.gold`
  - Gõ: `.p` → Bot gửi: `.profile`
  - Gõ: `.g abc` → **Không hoạt động**

### 🔥 Partial Shortcuts (Thay thế một phần)
- Thay thế từ khóa **shortcut**, giữ nguyên phần còn lại (placeholder)
- Ví dụ:
  - Gõ: `.wsel 123` → Bot gửi: `.waifu-select 123`
  - Gõ: `.wsel abc def` → Bot gửi: `.waifu-select abc def`
  - Gõ: `hello .wsel world` → **Không hoạt động**

## 🔥 Tính năng nổi bật

- ✅ **2 loại shortcuts**: Full + Partial
- ✅ **Thông minh**: Partial shortcuts được ưu tiên
- ✅ **An toàn**: Ngăn chặn vòng lặp vô hạn
- ✅ **Tùy chỉnh**: Độ trễ, phân biệt hoa/thường
- ✅ **Log chi tiết**: Theo dõi hoạt động real-time
- ✅ **Regex safe**: Xử lý ký tự đặc biệt an toàn

## 📊 Ví dụ thực tế

```bash
# Chạy bot
npm start

# Console sẽ hiển thị:
✅ Selfbot đã sẵn sàng! Đăng nhập với tài khoản: YourName#1234
📝 Đã tải 3 full shortcuts
📝 Đã tải 1 partial shortcuts
🔥 Bot đang hoạt động...

📋 Danh sách full shortcuts:
   .g → .gold
   .p → .profile
   .wlist → .waifu-list

📋 Danh sách partial shortcuts:
   .wsel → .waifu-select
```

## 🎯 Thêm shortcuts mới

### Full Shortcuts
```json
"shortcuts": {
  ".g": ".gold",
  ".new": "Tin nhắn mới của tôi!"
}
```

### Partial Shortcuts
```json
"partialShortcuts": {
  ".wsel": ".waifu-select",
  ".ws": ".waifu-stats",
  ".wd": ".waifu-divorce"
}
```

## ⚠️ Lưu ý quan trọng

**Chúng tôi sử dụng MIT License.** Tức chúng tôi không chịu trách nhiệm cho bất kỳ lỗi hay bất kì rủi ro nào cho tài khoản của bạn khi sử dụng bot này.

## 🔧 Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| Bot không hoạt động | Kiểm tra token trong `config.json` |
| Shortcuts không work | Đảm bảo syntax đúng trong `shortcut.json` |
| Bị loop tin nhắn | Kiểm tra logic ngăn chặn vòng lặp |
| Lỗi permission | Token có thể bị expire, lấy token mới |

---

**Made with ❤️ / copyright @duxg.fun / @brao bot development**
