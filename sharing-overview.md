# Sharing Overview: AI Agent Cho Team Marketing & Sales

> Buổi sharing tổng quan trước khi training chi tiết.
> Mục tiêu: giúp team hiểu AI agent là gì, có thể làm gì cho MKT & Sales, và 2 hướng triển khai để lựa chọn.

---

## 1. AI Agent Là Gì — Không Phải ChatGPT

Khác với ChatGPT/Gemini (hỏi 1 câu — trả 1 câu), **AI agent** là trợ lý ảo có khả năng:

- **Thao tác trên máy tính**: duyệt web, đọc email, mở file, thao tác Google Sheets...
- **Chạy nhiều bước tự động**: nhận 1 yêu cầu → tự chia thành các bước → thực hiện → trả kết quả
- **Chạy theo lịch**: tự động crawl thông tin mỗi sáng, gửi báo cáo định kỳ
- **Nhớ ngữ cảnh**: hiểu workflow, quy tắc, tone giọng riêng của team

**Ví dụ thực tế**: "Mỗi sáng lúc 8h, crawl 5 group Facebook đối thủ, tóm tắt bài mới, phân loại theo chủ đề, gửi báo cáo vào Telegram" — agent làm tự động, không cần ai bấm nút.

---

## 2. AI Agent Làm Được Gì Cho MKT & Sales?

### Marketing

| Công việc | Agent làm gì | Tiết kiệm |
|-----------|--------------|------------|
| **Research thị trường** | Crawl Facebook group, Reddit, news → tóm tắt trend | 1-2 giờ/ngày |
| **Theo dõi đối thủ** | Monitor page/group đối thủ, alert khi có bài mới | 30-45 phút/ngày |
| **Trend digest hàng ngày** | Tự crawl nguồn tin → tổng hợp báo cáo mỗi sáng | 1 giờ/ngày |
| **Content repurposing** | 1 bài viết → chuyển thể cho FB, LinkedIn, Email, Video script | 30-45 phút/bài |
| **Báo cáo campaign** | Đọc email agency → extract số liệu → đổ vào Google Sheets | 2-3 giờ/tuần |
| **Phân loại inbox** | Đọc email → phân loại → draft reply | 2-3 giờ/tuần |

### Sales

| Công việc | Agent làm gì | Tiết kiệm |
|-----------|--------------|------------|
| **Tìm data lead** | Search web, LinkedIn, directory → tổng hợp danh sách | 1-2 giờ/lần |
| **Research khách hàng** | Tra thông tin công ty/người trước meeting | 30 phút/lead |
| **Draft email outreach** | Viết email cá nhân hóa theo template + context | 15-20 phút/email |
| **Tóm tắt email dài** | Đọc chuỗi email → tóm tắt key points + action items | 10-15 phút/chuỗi |
| **Báo cáo định kỳ** | Tổng hợp data từ Sheets/email → format báo cáo | 1-2 giờ/tuần |

---

## 3. Hai Hướng Triển Khai

### Hướng A: OpenClaw (Self-hosted)

Cài đặt hệ thống AI agent **trên máy của công ty**, tự quản lý toàn bộ. Agent chạy 24/7 trên Mac mini hoặc server nội bộ, giao tiếp qua Telegram.

### Hướng B: Claude Desktop + Cowork

Dùng **app Claude Desktop** (của Anthropic) với chế độ **Cowork** — biến Claude thành agent chạy trực tiếp trên máy tính cá nhân. Điều khiển từ xa bằng điện thoại qua tính năng **Dispatch**.

---

## 4. So Sánh Chi Tiết

### 4.1. Cài Đặt & Vận Hành

| Tiêu chí | OpenClaw (Self-hosted) | Claude Desktop (Cowork) |
|----------|----------------------|------------------------|
| **Cài đặt ban đầu** | Phức tạp — cài qua terminal, cấu hình API key, Telegram bot, gateway | Đơn giản — tải app, đăng nhập, bắt đầu dùng |
| **Thời gian setup** | 3-4 giờ (cần Admin có kỹ thuật) | 15-30 phút (tự cài được) |
| **Máy chạy agent** | Cần 1 máy chạy 24/7 (Mac mini/server) | Máy cá nhân của mỗi người (cần mở app) |
| **Vận hành hàng ngày** | Cần Admin theo dõi log, restart khi lỗi | Gần như không cần — Anthropic quản lý |
| **Cập nhật** | Tự update, có thể gặp breaking changes | Tự động update qua app |
| **Troubleshooting** | Đọc log, debug config — cần kỹ thuật | Ít lỗi hơn, support từ Anthropic |

### 4.2. Sử Dụng Hàng Ngày

| Tiêu chí | OpenClaw (Self-hosted) | Claude Desktop (Cowork) |
|----------|----------------------|------------------------|
| **Giao diện** | Telegram (quen thuộc, nhẹ) | Claude Desktop app + Dispatch trên điện thoại |
| **Điều khiển từ xa** | Gửi lệnh qua Telegram bất kỳ lúc nào | Dispatch — gửi task từ điện thoại, máy tính thực hiện |
| **Chạy tự động (cron)** | Có — agent chạy theo lịch 24/7 | Có — scheduled tasks trong Cowork |
| **Duyệt web/Facebook** | Cần cấu hình script scraping | Agent tự dùng browser trên máy, click/gõ như người thật |
| **Google Workspace** | Cần setup OAuth, cấu hình connector | Agent mở browser → thao tác trực tiếp trên Gmail, Sheets... |
| **Nhiều agent chuyên biệt** | Có — mỗi agent có SOUL.md riêng, Telegram bot riêng | Dùng Projects để tổ chức — mỗi project có instruction riêng |
| **Độ khó sử dụng** | Thấp (gửi tin nhắn Telegram) | Thấp (chat trong app hoặc gửi từ điện thoại) |

### 4.3. Yêu Cầu Kỹ Năng

| Vai trò | OpenClaw | Claude Desktop (Cowork) |
|---------|----------|------------------------|
| **Admin / Ops** | Cần biết: terminal, Python cơ bản, đọc log, quản lý API key, viết SOUL.md/SKILL.md | Cần biết: quản lý subscription, viết instruction cho project, hướng dẫn team |
| **User (MKT/Sales)** | Cần biết: dùng Telegram, mô tả yêu cầu rõ ràng | Cần biết: dùng Claude app, mô tả yêu cầu rõ ràng |
| **Rào cản kỹ thuật** | Trung bình-cao (cần ít nhất 1 người kỹ thuật) | Thấp (mỗi người tự dùng được) |

### 4.4. Chi Phí

| Hạng mục | OpenClaw | Claude Desktop (Cowork) |
|----------|----------|------------------------|
| **Phần mềm** | Miễn phí (open source) | Pro: $20/người/tháng, Max: $100-200/người/tháng |
| **API LLM** | Trả theo dùng — Anthropic API ~$3-15/triệu token, OpenRouter cho model rẻ hơn | Đã bao gồm trong subscription (có giới hạn message) |
| **Phần cứng** | Cần Mac mini hoặc server (~$700-1500 một lần) | Dùng máy cá nhân có sẵn |
| **Nhân sự vận hành** | Cần 1 Admin part-time | Không cần Admin chuyên trách |
| **Chi phí team 5 người/tháng** | ~$30-80 API (tùy mức dùng) + phần cứng ban đầu | Pro: $100/tháng, Max: $500-1000/tháng |
| **Chi phí team 10 người/tháng** | ~$50-150 API (tùy mức dùng) | Pro: $200/tháng, Max: $1000-2000/tháng |

> **Lưu ý**: OpenClaw rẻ hơn nhiều nếu team lớn, nhưng cần đầu tư nhân sự kỹ thuật. Claude Desktop đắt hơn nhưng không cần ops.

### 4.5. Ưu & Nhược Điểm

#### OpenClaw (Self-hosted)

| Ưu điểm | Nhược điểm |
|----------|------------|
| Chi phí thấp khi scale team lớn | Cần Admin kỹ thuật để vận hành |
| Toàn quyền kiểm soát data (chạy nội bộ) | Setup phức tạp, mất thời gian |
| Tùy biến sâu (viết script, skill riêng) | Cần máy chạy 24/7 |
| Agent chạy liên tục không phụ thuộc máy cá nhân | Troubleshooting cần đọc log, debug |
| Dùng được nhiều model (Claude, Gemini, Kimi) — tối ưu chi phí | Cần training bài bản cho Admin |

#### Claude Desktop + Cowork

| Ưu điểm | Nhược điểm |
|----------|------------|
| Setup cực nhanh, ai cũng tự cài được | Chi phí cao khi team lớn ($20-200/người/tháng) |
| Không cần Admin kỹ thuật | Phụ thuộc vào Anthropic (pricing, policy, downtime) |
| Computer use mạnh — duyệt web, thao tác app như người | Máy cá nhân phải mở + online để agent chạy |
| Dispatch — điều khiển từ điện thoại rất tiện | Ít tùy biến hơn so với self-hosted |
| Update tự động, ít maintenance | Giới hạn message theo plan, dùng nhiều có thể bị rate limit |
| Anthropic hỗ trợ kỹ thuật | Data đi qua server Anthropic (cần cân nhắc bảo mật) |

---

## 5. Hướng Nào Phù Hợp Với Ai?

| Tình huống | Khuyến nghị |
|------------|------------|
| Team nhỏ (3-5 người), không có Admin kỹ thuật | **Claude Desktop** — setup nhanh, chi phí chấp nhận được |
| Team lớn (10+ người), có 1 người kỹ thuật | **OpenClaw** — chi phí thấp hơn nhiều khi scale |
| Cần bảo mật cao, data không ra ngoài | **OpenClaw** — chạy hoàn toàn nội bộ |
| Muốn dùng ngay, không muốn đợi setup | **Claude Desktop** — 30 phút là chạy |
| Cần agent chạy 24/7 không phụ thuộc ai online | **OpenClaw** — agent chạy trên server riêng |
| Mỗi người cần agent cá nhân hóa riêng | **Claude Desktop** — mỗi người tự config |
| Cần tích hợp sâu với hệ thống nội bộ | **OpenClaw** — viết script/skill tùy ý |

### Kết hợp cả hai?

Hoàn toàn có thể:
- **Claude Desktop** cho từng cá nhân — xử lý task ad-hoc hàng ngày (research, draft content, đọc email)
- **OpenClaw** cho task chạy tự động 24/7 — monitor đối thủ, trend digest mỗi sáng, báo cáo định kỳ

---

## 6. Demo Nhanh — Agent Làm Gì Được?

> Phần demo trực tiếp trong buổi sharing — chọn 2-3 use case phù hợp nhất với team.

### Demo 1: Research đối thủ
- Yêu cầu: "Tìm hiểu về thương hiệu X — sản phẩm chính, giá, kênh marketing, điểm mạnh/yếu"
- Agent tự search web, tổng hợp, format báo cáo

### Demo 2: Content repurposing
- Yêu cầu: "Chuyển bài blog này thành post Facebook, LinkedIn, và email newsletter"
- Agent đọc bài gốc, rewrite theo tone phù hợp từng kênh

### Demo 3: Duyệt Facebook group
- Yêu cầu: Agent mở browser, vào group Facebook, đọc bài viết mới, chụp ảnh phân tích nội dung
- Minh họa computer use — agent thao tác như người thật

### Demo 4: Tìm data lead (Sales)
- Yêu cầu: "Tìm 10 công ty edtech tại Việt Nam, lấy tên, website, email liên hệ"
- Agent search web, tổng hợp vào bảng

---

## 7. Bước Tiếp Theo

Sau buổi sharing này, team sẽ:

1. **Chọn hướng triển khai** (hoặc kết hợp) phù hợp với nhu cầu và nguồn lực
2. **Liệt kê công việc cụ thể** mà team muốn agent hỗ trợ (MKT + Sales)
3. **Đăng ký training chi tiết** — nội dung sẽ được điều chỉnh theo hướng đã chọn:
   - Nếu chọn OpenClaw → training theo giáo trình 5 module (~12-14 giờ)
   - Nếu chọn Claude Desktop → training nhẹ hơn, tập trung vào cách viết instruction và workflow (~4-6 giờ)
   - Nếu kết hợp → training cả hai, ưu tiên theo nhu cầu

---

## Q&A — Câu Hỏi Thường Gặp

**Agent có tự gửi email/đăng bài không?**
> Có thể, nhưng khuyến nghị luôn có bước review của người trước khi publish/send. Agent là trợ lý, không phải người ra quyết định.

**Data của công ty có bị lộ không?**
> OpenClaw: data ở trên máy nội bộ, chỉ nội dung gửi đến LLM mới đi qua API. Claude Desktop: data đi qua server Anthropic — cần đọc kỹ privacy policy nếu xử lý data nhạy cảm.

**Dùng AI có thay người không?**
> Không. Agent xử lý phần lặp đi lặp lại (research, tổng hợp, format) để người tập trung vào phần cần tư duy (chiến lược, sáng tạo, quyết định).

**Chi phí có kiểm soát được không?**
> OpenClaw: theo dõi qua API usage dashboard, set limit. Claude Desktop: chi phí cố định theo subscription, dễ dự đoán.

**Không biết code có dùng được không?**
> Claude Desktop: hoàn toàn được — chỉ cần biết mô tả yêu cầu. OpenClaw: cần ít nhất 1 người biết code trong team để vận hành.
