# Cấu trúc Team: Admin vs User

---

## Hai vai trò cần thiết

OpenClaw là hệ thống **multi-agent**, đòi hỏi hai loại người vận hành với trách nhiệm khác nhau.

---

## 👨‍💻 Vai Admin (1 người)

### Cần biết gì
- Đọc/sửa Python cơ bản
- Dùng terminal thoải mái
- Hiểu workflow của marketing team (để viết SOUL.md đúng)
- **Quan trọng nhất**: prompt engineering — mô tả công việc thành instruction rõ ràng

> Không cần senior developer. Người biết **mô tả vấn đề rõ ràng** và không ngại terminal là đủ. Claude Code (admin agent) sẽ làm phần code.

### Trách nhiệm

**Cài đặt & cấu hình:**
- Setup OpenClaw trên Mac mini, kết nối Telegram bot
- Quản lý API key, chi phí LLM
- Backup cấu hình định kỳ

**Tạo & tối ưu agent:**
- Viết và chỉnh SOUL.md khi yêu cầu của team thay đổi
- Tạo SKILL.md cho tool mới
- Test agent sau khi thay đổi

**Vận hành:**
- Đọc log khi agent lỗi
- Restart gateway khi cần
- Phát triển script mới (với Claude Code hỗ trợ)
- So sánh và switch model LLM khi cần tối ưu chi phí

### Công cụ admin sử dụng
- **Claude Code** (hoặc Cursor/Windsurf) — admin agent chính để tạo/sửa config
- Terminal + `jq` để thao tác JSON config
- `openclaw gateway restart/status` — quản lý gateway
- Log files: `gateway.err.log`, session `.jsonl` — để debug

---

## 👥 Vai User — Marketing Team (nhiều người)

### Cần biết gì
- Dùng Telegram (gửi tin nhắn, nhận file)
- Biết cách mô tả yêu cầu rõ ràng cho agent
- Hiểu giới hạn của agent để không kỳ vọng quá

### Trách nhiệm

**Sử dụng hàng ngày:**
- Chat với agent qua Telegram để thực hiện công việc
- Đọc và verify output trước khi dùng
- Feedback chất lượng để Admin cải thiện agent

**Giao tiếp với Admin:**
- Báo lỗi: "Agent đang làm gì sai, input là gì, output thực tế là gì"
- Đề xuất use case mới
- Mô tả workflow mong muốn để Admin viết SOUL.md

### Những gì User KHÔNG cần làm
- Không cần đụng vào config, terminal, code
- Không cần biết model LLM là gì
- Không cần tự restart gateway — báo Admin

---

## Vòng lặp cải tiến liên tục

```
User dùng agent
    ↓
User phát hiện output chưa đúng / muốn thêm tính năng
    ↓
User mô tả yêu cầu cho Admin
    ↓
Admin sửa SOUL.md / SKILL.md / viết script mới (với Claude Code)
    ↓
Admin test → deploy → báo User
    ↓
User dùng lại → feedback tiếp
```

Dựa trên kinh nghiệm thực tế: phần lớn công việc Admin không phải cài đặt ban đầu mà là **vòng lặp tối ưu này** — diễn ra liên tục, đặc biệt trong 1-2 tháng đầu.

---

## Nếu không có Admin nội bộ

Trong giai đoạn đầu, **người trainer** (người setup ban đầu) có thể đóng vai Admin từ xa:
- Marketing team báo yêu cầu/lỗi qua chat
- Trainer remote access vào Mac mini để sửa config
- Duy trì ít nhất 1-2 tháng đầu cho đến khi hệ thống ổn định

Về dài hạn, nên đào tạo 1 người trong công ty lên vai Admin — người phù hợp thường là người có background IT hoặc người ham học hỏi tool mới.
