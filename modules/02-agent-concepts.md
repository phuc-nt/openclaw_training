# Module 2: Hiểu Cách Agent Hoạt Động

> **Đối tượng**: Cả team (Admin + User)
> **Thời lượng**: 2 giờ
> **Mục tiêu**: Hiểu đủ để biết tại sao agent làm đúng/sai, và cách yêu cầu Agent làm đúng hơn

---

## 2.1 Agent là gì — Giải thích không kỹ thuật

Agent OpenClaw = **nhân viên ảo** nhận lệnh qua Telegram, có thể:
- Trả lời câu hỏi
- Tìm kiếm thông tin trên web
- Thao tác Gmail, Google Calendar, Google Sheets
- Scrape Facebook group
- Chạy script Python/Bash trên máy

Nhưng agent **không tự biết làm gì** nếu không được hướng dẫn. Toàn bộ hành vi của agent được định nghĩa bởi 3 file config:

---

## 2.2 Ba File Quyết Định Chất Lượng Agent

### SOUL.md — "Bản mô tả công việc"
Định nghĩa agent là ai, làm gì, theo quy tắc nào. Ví dụ:

```markdown
# Marketing Agent

Bạn là trợ lý marketing của công ty X. Hỗ trợ team:
- Nghiên cứu đối thủ cạnh tranh
- Tổng hợp trend ngành
- Viết content theo brand voice

## Quy tắc
- Luôn trả lời bằng tiếng Việt
- Khi tổng hợp thông tin phải ghi rõ nguồn
- Không đăng bài lên mạng xã hội khi chưa được confirm
```

> **Insight quan trọng**: Cùng 1 agent, SOUL.md khác nhau → kết quả khác nhau hoàn toàn. Viết SOUL.md tốt = 80% thành công.

### TOOLS.md — "Danh sách công cụ"
Liệt kê tools agent có thể dùng và cách dùng. Agent đọc file này để biết mình có những khả năng gì.

### SKILL.md — "Hướng dẫn sử dụng công cụ"
Hướng dẫn chi tiết cho từng tool. Quan trọng nhất: phải có **ví dụ cụ thể**, không chỉ mô tả chung chung.

**Bài học thực tế**: Agent (kể cả Claude, Gemini) hay đoán mò cú pháp → sai. Phải ghi rõ trong SKILL.md: "Trước khi dùng tool X, BẮT BUỘC phải chạy lệnh Y để xem cú pháp đúng."

---

## 2.3 Vòng Đời Một Lần Chat

```
User gửi tin nhắn Telegram
    ↓
Gateway nhận → gửi vào session của agent
    ↓
Agent đọc SOUL.md + TOOLS.md (context)
    ↓
Agent suy nghĩ → quyết định dùng tool nào
    ↓
Agent gọi tool (web search, Gmail, script...)
    ↓
Tool trả kết quả → agent tổng hợp
    ↓
Agent trả lời Telegram
```

**Điều quan trọng**: Agent không có bộ nhớ dài hạn mặc định — mỗi session là một cuộc hội thoại riêng. Nếu cần agent "nhớ" thông tin giữa các session, cần cấu hình memory (Kioku agent).

---

## 2.4 Chọn Model LLM

Agent dùng LLM để "suy nghĩ". Khác model → khác chất lượng và chi phí:

| Model | Điểm mạnh | Phù hợp cho | Chi phí |
|-------|-----------|-------------|---------|
| Claude Sonnet/Haiku | Tool calling tốt nhất, follow instruction chặt | Agent cần thao tác nhiều tool | Trung bình-cao |
| Gemini Flash | Nhanh, context window lớn | Research, tổng hợp văn bản dài | Thấp |
| Kimi K2.5 | Tiết kiệm, follow rules tốt | Daily digest, task đơn giản | Thấp |

**Nguyên tắc thực tế**:
- Agent xử lý task phức tạp, nhiều tool calls → dùng Claude
- Agent chỉ tổng hợp, viết text → Gemini hoặc Kimi để tiết kiệm chi phí
- Test thực tế trước khi kết luận — benchmark trên giấy khác với performance thực tế

**Bài học thực tế (Mar 2026)**: Kimi K2.5 tốt hơn Gemini 3 Flash cho daily-digest — ít tool calls hơn (4 vs 7), 0 lỗi, format output sạch hơn. Gemini có session limit bug sau nhiều tool calls.

---

## 2.5 Cron Job — Agent Tự Chạy Theo Lịch

Agent có thể được lên lịch chạy tự động, không cần người trigger:

```
Mỗi 4 giờ  → Facebook Group Monitor scrape bài mới → gửi Telegram
Mỗi sáng 8h → Daily Digest tổng hợp Reddit/YouTube → gửi Telegram
Mỗi 2 giờ  → Kiểm tra Substack RSS → alert nếu có bài mới
```

User không cần làm gì — chỉ cần đọc kết quả khi nhận được.

---

## 2.6 Điều User Nên Biết Khi Dùng Agent

**✅ Agent làm tốt:**
- Tìm kiếm, tổng hợp thông tin từ nhiều nguồn
- Viết nháp theo template hoặc brief
- Thao tác Google Workspace theo lệnh rõ ràng
- Chạy task lặp đi lặp lại theo lịch

**⚠️ Agent cần verify lại:**
- Số liệu cụ thể (có thể hallucinate)
- Thông tin real-time (phụ thuộc vào kết quả web search)
- Nội dung quan trọng trước khi publish

**❌ Agent không nên làm:**
- Tự đăng bài lên mạng xã hội mà không review
- Gửi email thật mà không xác nhận
- Xóa dữ liệu mà không confirm

> **Nguyên tắc vàng**: Agent là **trợ lý**, không phải người ra quyết định. Luôn giữ human-in-the-loop cho các hành động không thể undo.
