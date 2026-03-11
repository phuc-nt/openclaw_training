# Kế hoạch Training OpenClaw — Đội Marketing

> Tài liệu này được soạn dựa trên kinh nghiệm vận hành thực tế từ 2026-02-14 đến nay.
> Mục tiêu: giúp đội marketing của một công ty triển khai và sử dụng OpenClaw hiệu quả.

---

## Cấu trúc tài liệu

```
training/
├── README.md                     ← File này — tổng quan & mục lục
├── roles-and-structure.md        ← Cấu trúc team: Admin vs User, ai cần biết gì
│
├── modules/
│   ├── 01-infrastructure.md      ← Module 1: Cài đặt & bảo mật (dành cho Admin)
│   ├── 02-agent-concepts.md      ← Module 2: Hiểu cách agent hoạt động (cả team)
│   ├── 03-core-agents.md         ← Module 3: Các agent thực chiến (cả team)
│   ├── 04-daily-operations.md    ← Module 4: Vận hành hàng ngày (cả team)
│   └── 05-workshop.md            ← Workshop: tự viết SOUL.md cho use case của mình
│
└── use-cases/
    ├── immediate.md              ← Use cases có thể làm ngay với OpenClaw
    └── roadmap.md                ← Roadmap mở rộng (cần thêm skill/script)
```

---

## Lịch trình gợi ý

| Buổi | Đối tượng | Nội dung | Thời lượng |
|------|-----------|----------|------------|
| 1 | Admin only | Module 1: Infrastructure | 3-4 giờ |
| 2 | Cả team | Module 2: Hiểu agent + SOUL.md | 2 giờ |
| 3 | Cả team | Module 3: Demo các agent thực chiến | 3 giờ |
| 4 | Cả team | Module 4: Vận hành + troubleshoot cơ bản | 1.5 giờ |
| 5 | Cả team | Workshop: tự design agent cho use case của mình | 2-3 giờ |

**Tổng: ~12-14 giờ** — có thể chia 2-3 buổi/tuần trong vòng 2-3 tuần.

---

## Điều kiện tiên quyết

- Có **1 người Admin** biết code cơ bản (đọc/sửa Python, dùng terminal) — xem `roles-and-structure.md`
- Phần cứng: Mac mini hoặc máy chạy macOS 24/7 (hoặc Linux server)
- Tài khoản: Anthropic API key, Telegram bot token
- Tùy chọn: OpenRouter API key (để dùng Gemini, Kimi — rẻ hơn cho các task đơn giản)

---

## Nguyên tắc quan trọng nhất

> **Khoảng cách lớn nhất không phải kỹ thuật — mà là khả năng mô tả công việc của mình thành SOUL.md.**

Một agent hoạt động tốt hay không phụ thuộc 80% vào cách viết instruction (SOUL.md, TOOLS.md, SKILL.md), không phải vào code hay model. Đây là kỹ năng cần đầu tư nhiều nhất khi training.
