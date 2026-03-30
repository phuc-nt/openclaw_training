# Training AI Agent Cho Team Marketing & Sales

> Tài liệu giúp team MKT & Sales bắt đầu sử dụng AI agent — từ hiểu khái niệm, chọn giải pháp, đến vận hành thực tế.

**Slide thuyết trình**: [mở slides](https://phuc-nt.github.io/openclaw_training/slides.html)

---

## Đọc theo thứ tự nào?

### Bước 1 — Hiểu & Chọn giải pháp

> Dành cho **tất cả mọi người** — không cần biết kỹ thuật.

| Thứ tự | Tài liệu | Nội dung | Thời gian đọc |
|---|---|---|---|
| 1 | [AI Agent là gì?](01-overview/ai-agent-intro.md) | AI agent khác ChatGPT thế nào, giúp gì cho MKT & Sales | 5 phút |
| 2 | [So sánh 3 giải pháp](01-overview/solution-comparison.md) | Claude Desktop + ClaudeKit, GoClaw Enterprise, OpenClaw — ai nên chọn gì | 15 phút |
| 3 | [Khảo sát trước training](01-overview/pre-training-survey.md) | 20 câu hỏi để điều chỉnh nội dung training cho phù hợp | 10 phút |

### Bước 2 — Training OpenClaw (nếu chọn self-hosted)

> Dành cho team chọn hướng tự vận hành. Cần 1 Admin biết kỹ thuật cơ bản.

| Buổi | Tài liệu | Đối tượng | Thời lượng |
|---|---|---|---|
| — | [Vai trò Admin vs User](02-openclaw-training/roles-and-structure.md) | Cả team | Đọc trước |
| 1 | [Module 1: Cài đặt & bảo mật](02-openclaw-training/01-infrastructure.md) | Admin only | 3-4 giờ |
| 2 | [Module 2: Hiểu cách agent hoạt động](02-openclaw-training/02-agent-concepts.md) | Cả team | 2 giờ |
| 3 | [Module 3: Demo agent thực chiến](02-openclaw-training/03-core-agents.md) | Cả team | 3 giờ |
| 4 | [Module 4: Vận hành hàng ngày](02-openclaw-training/04-daily-operations.md) | Cả team | 1.5 giờ |
| 5 | [Module 5: Workshop tự thiết kế agent](02-openclaw-training/05-workshop.md) | Cả team | 2-3 giờ |

### Bước 3 — Ý tưởng use case

> Dùng để chọn việc nào nên giao cho agent trước.

| Tài liệu | Nội dung |
|---|---|
| [Use cases làm ngay](03-use-cases/immediate.md) | 6 use case triển khai được ngay: monitor đối thủ, trend digest, báo cáo campaign... |
| [Roadmap mở rộng](03-use-cases/roadmap.md) | Use case nâng cao cần thêm thời gian: GA4 auto-report, Shopee review monitor... |

---

## 3 Giải pháp tóm tắt

| | **Claude Desktop + ClaudeKit** | **GoClaw Enterprise** | **OpenClaw Self-hosted** |
|---|---|---|---|
| **Phù hợp** | Cá nhân, team nhỏ | Agency, doanh nghiệp 10+ người | Team có IT, muốn kiểm soát toàn bộ |
| **Setup** | 30 phút | 1-2 ngày (Digitop hỗ trợ) | 1-2 tuần |
| **Chi phí/tháng (5 người)** | $100-1,000 | ~5-7 triệu VND | $30-150 |
| **Cần kỹ thuật?** | Không | Không (có hỗ trợ) | Cần 1 Admin |
| **Chi tiết** | [Xem so sánh](01-overview/solution-comparison.md) | [Xem so sánh](01-overview/solution-comparison.md) | [Xem so sánh](01-overview/solution-comparison.md) |

---

## Nguyên tắc quan trọng nhất

> **Khoảng cách lớn nhất không phải kỹ thuật — mà là khả năng mô tả công việc của mình thành instruction cho AI.**

Agent hoạt động tốt hay không phụ thuộc **80% vào cách viết instruction**, không phải vào công nghệ. Đây là kỹ năng quan trọng nhất cần học trong training.

---

## Cấu trúc thư mục

```
├── README.md                      ← File này
├── slides.html                    ← Slide thuyết trình (Reveal.js, mở bằng browser)
│
├── 01-overview/                   ← Hiểu AI agent & chọn giải pháp
│   ├── ai-agent-intro.md
│   ├── solution-comparison.md
│   └── pre-training-survey.md
│
├── 02-openclaw-training/          ← Giáo trình OpenClaw self-hosted (5 modules)
│   ├── roles-and-structure.md
│   ├── 01-infrastructure.md
│   ├── 02-agent-concepts.md
│   ├── 03-core-agents.md
│   ├── 04-daily-operations.md
│   └── 05-workshop.md
│
└── 03-use-cases/                  ← Ý tưởng use case cho MKT & Sales
    ├── immediate.md
    └── roadmap.md
```
