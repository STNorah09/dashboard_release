# Dashboard AIO

> **All-in-One Desktop App** — Electron + React + Vite + TypeScript

Một ứng dụng desktop tích hợp 10 phân hệ phục vụ công việc, học tập và giải trí trong một giao diện duy nhất. Hỗ trợ đa ngôn ngữ (🇻🇳 / 🇺🇸), Dark/Light theme, lưu trữ cục bộ (SQLite via sql.js) và đồng bộ đám mây (Supabase).

---

## 📋 Tính năng chính

### 🏠 Dashboard
- Hiển thị **System Status** theo thời gian thực: Boot time, RAM, Local IP (via `systeminformation`).
- Lời chào thông minh theo buổi trong ngày.
- **Quick Actions**: Quản lý (Thêm / Sửa / Xoá) các widget đường dẫn tiện ích tùy chỉnh.
- Điều hướng nhanh sang các phân hệ khác từ trang chủ.

### 📖 E-Reader (Trình đọc sách)
- Hỗ trợ định dạng: `.txt`, `.docx` (Mammoth), `.epub` (JSZip).
- **Phát hiện thay đổi file gốc**: Tự động nhận diện nếu file nguồn được sửa bên ngoài (ví dụ: từ Word) và hỏi người dùng có muốn đồng bộ không.
- **Xử lý file bị mất hoặc di chuyển**: Cho phép chọn lại đường dẫn file mới.
- **Tùy chỉnh hiển thị**: Theme (Sáng / Tối / Giấy), Cỡ chữ, Font, Lề, Căn lề.
- **Theo dõi tiến độ**: Ước tính thời gian đọc còn lại (theo WPM), Bookmark thông minh.
- **Dịch thuật nhanh**: Popup dịch khi bôi đen văn bản (tích hợp Google Translate API).
- **Tìm kiếm nội dung**: Thanh tìm kiếm với điều hướng kết quả (trước / sau).
- **Bảo vệ mắt**: Hẹn giờ nhắc nghỉ ngơi (Eye Care Timer).
- **Xử lý link**: Click vào link trong nội dung → mở trình duyệt hệ thống (external) hoặc cuộn đến anchor (internal).

### 🎯 Focus Station (Trạm tập trung)
- Hẹn giờ **Pomodoro** với 2 chế độ: Focus 🧠 & Break ☕ (thời gian tùy chỉnh).
- Đặt mục tiêu công việc ngay trong giao diện.
- **Trình phát nhạc Lofi mini**: Hỗ trợ YouTube, SoundCloud (iframe thủ công), và file audio cục bộ.
- Tùy chọn phát nhạc ngầm khi chuyển sang tab khác.
- Hỗ trợ cả Light và Dark theme riêng cho Focus Station.

### 📚 Manga Radar
- Tìm kiếm truyện tranh từ **MangaDex API** và theo dõi chapter mới.
- Lưu danh sách đang theo dõi vào **Supabase** (`manga_tracker` table).
- Cảnh báo nội dung **NSFW / 18+** rõ ràng trước khi chuyển sang MangaDex.
- Hỗ trợ lọc theo ngôn ngữ chapter.

### 💻 Quick Snippets (Quản lý Code)
- Lưu trữ các đoạn code / văn bản thường dùng trên **Supabase** (`quick_snippets` table).
- **Tự động nhận diện ngôn ngữ** (heuristic-based: JS, TS, Python, SQL, Bash, HTML, CSS, JSON, ...).
- Ghim snippet quan trọng, đếm số lần sử dụng (**Usage Tracking** via RPC).
- **Thêm / Sửa / Xóa** snippet qua modal (modal tái sử dụng cho cả Create lẫn Edit).
- Mở **Mini Window** riêng (Electron BrowserWindow) để tiện xem snippet khi đang code.

### 📋 Clipboard Manager
- Tự động ghi nhận lịch sử sao chép (Text & Images) trong nền (polling interval).
- Xem lại và sao chép lại lịch sử dễ dàng.
- Hỗ trợ Cloud Sync (đẩy lên / kéo về Supabase).
- **Keep-Alive**: Component luôn chạy ngầm (không unmount khi chuyển tab) để không bỏ sót clipboard.

### 📓 Tech Journal (Nhật ký kỹ thuật)
- Ghi chép nhật ký công việc, lỗi máy tính, ghi chú kỹ thuật.
- Gắn thẻ (tags), thời gian ghi nhận tự động.
- Hỗ trợ Cloud Sync.

### 🎨 Vibe Board (Bảng vẽ)
- Bảng vẽ vô cực (**Infinite Canvas**) dùng **ReactFlow** để brainstorm, thiết kế ý tưởng.
- Kéo thả các node tự do.
- **Keep-Alive**: Giữ nguyên vị trí canvas khi chuyển sang tab khác.

### 🎓 Study Station
- Tập hợp tài liệu học theo môn:
  - **Math**: Công thức toán học.
  - **Physics**: Công thức vật lý.
  - **Chemistry**: Bảng tuần hoàn, công thức hoá học.
  - **English**: Từ vựng, ngữ pháp, bài tập (dữ liệu lớn ~42KB).

### 🛠️ Mini Tools (Công cụ nhỏ)
- **Quick Note**: Ghi chú nhanh tạm thời.
- **Color Picker**: Chọn màu và sao chép mã HEX / RGB.
- **QR Code Generator**: Tạo QR Code từ văn bản / URL (dùng `qrcode.react`).

---

## ⚙️ Hệ thống & Cấu hình

| Tính năng | Mô tả |
|---|---|
| **Internationalization (i18n)** | Chuyển đổi Tiếng Việt / Tiếng Anh qua Settings (dùng `i18next` + `react-i18next`) |
| **Cloud Sync** | Push / Pull dữ liệu (Clipboard, Journal, ...) lên Supabase. Có thể tắt từng chiều trong Settings |
| **Auto Sync** | Tùy chọn tự động đẩy lên Cloud ngay khi có thay đổi |
| **Local DB** | SQLite chạy trên client (sql.js + WASM) cho tốc độ truy xuất nhanh, không cần kết nối mạng |
| **Themes** | Dark / Light mode toàn hệ thống (lưu vào `localStorage`) |
| **Keep-Alive Rendering** | Các component quan trọng (Clipboard, VibeBoard) luôn được render ngầm, chỉ ẩn/hiện bằng `display: none` |
| **Error Boundary** | Bắt lỗi runtime ở cấp độ component, tránh crash toàn bộ app |
| **Custom Dialog** | Hệ thống dialog/confirm tùy chỉnh qua `DialogProvider` context |

---

## 🚀 Cài đặt và Chạy

### Yêu cầu
- **Node.js** 18+
- **npm** 9+

### Cài đặt dependencies
```bash
npm install
```

### Chạy ở chế độ Development (Electron)
```bash
npm run electron:dev
```
> Lệnh này dùng `concurrently` để chạy song song Vite dev server và Electron process.

### Chạy ở chế độ Web (Browser Only)
```bash
npm run dev
```

### Build ứng dụng (Production)
```bash
npm run build:all
```
> Kết quả build được xuất ra thư mục `release/` dưới dạng file `.exe` (NSIS installer cho Windows).

---

## 🛠️ Công nghệ sử dụng

| Nhóm | Thư viện / Công cụ |
|---|---|
| **Core** | React 18, TypeScript 5, Vite 7 |
| **Desktop** | Electron 40, electron-builder |
| **Styling** | Vanilla CSS với CSS Custom Properties (biến theme) |
| **Icons** | Lucide React |
| **i18n** | i18next, react-i18next |
| **Cloud DB** | Supabase (`@supabase/supabase-js`) |
| **Local DB** | sql.js (SQLite via WASM) |
| **Media** | react-player v3 (YouTube, SoundCloud fallback iframe, local audio) |
| **Canvas** | ReactFlow 11 |
| **File Parsing** | Mammoth (`.docx`), JSZip (`.epub`) |
| **Utilities** | Fuse.js (fuzzy search), qrcode.react, react-markdown, systeminformation |

---

## 📁 Cấu trúc dự án

```
project1/
├── electron/             # Electron main process (main.ts)
├── public/               # Static assets (sql-wasm, icons)
├── src/
│   ├── components/
│   │   ├── Dashboard/
│   │   ├── EReader/
│   │   ├── FocusStation/
│   │   ├── Manga/
│   │   ├── Snippets/
│   │   ├── ClipboardManager/
│   │   ├── TechJournal/
│   │   ├── VibeBoard/
│   │   ├── Study/
│   │   ├── Tools/
│   │   └── Shared/       # Dùng chung: CustomDialog, LanguageSwitcher, ...
│   ├── hooks/            # Custom React hooks
│   ├── i18n/             # Cấu hình i18next + locales (en.json, vi.json)
│   ├── services/         # SyncService, Supabase client
│   ├── db.ts             # Khởi tạo và thao tác SQLite local
│   ├── utils.ts          # Các hàm tiện ích dùng chung
│   └── App.tsx           # Root component, routing & layout
├── supabase_quick_snippets.sql  # Schema SQL cho bảng quick_snippets
└── package.json
```

---

*© Copyright Norah — made with vibe coding in big 26*
