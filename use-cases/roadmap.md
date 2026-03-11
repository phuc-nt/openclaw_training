# Use Cases — Roadmap Mở Rộng

> Các use cases dưới đây cần thêm script/skill mới hoặc tích hợp platform mới. Sắp xếp theo độ ưu tiên.

---

## 🟡 Giai đoạn 2 — Cần thêm skill (1-2 tháng sau khi ổn định)

### UC-07: Google Analytics / Ads Performance Summary

**Mô tả**: Agent tự pull số liệu Google Analytics + Google Ads hàng tuần → highlight bất thường (traffic drop, cost spike) → gửi Telegram.

**Cần làm thêm**: Script gọi GA4 API + Google Ads API, viết SKILL.md tương ứng.

**Giá trị**: Phát hiện vấn đề sớm mà không cần login dashboard mỗi ngày.

---

### UC-08: Meeting Notes → Action Items → Tasks

**Mô tả**: Paste transcript meeting (từ Google Meet auto-caption) → agent tóm tắt → tạo Google Tasks + Calendar reminder cho từng người.

**Cần làm thêm**: SKILL.md cho Google Tasks API (đã có GWS CLI support).

**Lệnh mẫu:**
```
"Đây là transcript meeting hôm nay: [paste]
Tóm tắt quyết định chính, tạo task cho từng người,
deadline theo những gì đã thỏa thuận trong meeting"
```

---

### UC-09: Zalo OA Monitoring

**Mô tả**: Monitor Zalo Official Account của đối thủ hoặc của chính mình — alert khi có tin nhắn chưa trả lời quá 30 phút, tổng hợp câu hỏi thường gặp.

**Cần làm thêm**: Playwright script cho Zalo web (tương tự fb-group-monitor.py).

**Lưu ý**: Zalo không có public API cho OA reading — phải dùng browser automation.

---

### UC-10: Shopee/Lazada Review Monitor

**Mô tả**: Tự động đọc review mới trên sản phẩm của mình (và đối thủ) → alert khi có review 1-2 sao → tổng hợp feedback thường gặp theo tuần.

**Cần làm thêm**: Script scrape Shopee/Lazada product reviews.

---

## 🔴 Giai đoạn 3 — Phức tạp, cân nhắc kỹ (3-6 tháng)

### UC-11: Auto-Draft Social Posts Theo Lịch

**Mô tả**: Agent tự soạn content lịch đăng cho cả tuần dựa trên: content calendar template, trend digest, brand guidelines → đưa vào queue chờ human approve.

**Lưu ý quan trọng**:
- KHÔNG để agent tự đăng mà không review
- Cần workflow approve rõ ràng (ví dụ: approve qua Telegram button)
- Risk cao nếu agent hiểu sai brand voice

### UC-12: Influencer Monitoring

**Mô tả**: Track nội dung của list influencer đã hợp tác hoặc muốn hợp tác — họ đang làm gì, engagement rate thế nào, có đề cập brand mình không.

**Cần làm thêm**: Script scrape Instagram/TikTok (phức tạp hơn Facebook do anti-bot mạnh hơn).

### UC-13: Customer Sentiment Dashboard

**Mô tả**: Tổng hợp sentiment từ nhiều nguồn (Facebook comments, Google reviews, Shopee reviews) → dashboard weekly → alert khi sentiment tiêu cực tăng đột biến.

**Cần làm thêm**: Pipeline tổng hợp đa nguồn + sentiment analysis + visualization.

---

## Nguyên tắc Prioritize

Khi chọn use case tiếp theo cần phát triển, đánh giá theo 3 tiêu chí:

1. **Frequency**: Việc này xảy ra hàng ngày hay 1 lần/tháng? → Ưu tiên daily tasks
2. **Time saved**: Thủ công mất bao nhiêu giờ? → Ưu tiên việc tốn nhiều thời gian
3. **Error risk**: Nếu agent làm sai thì hậu quả thế nào? → Ưu tiên việc ít rủi ro trước

> **Không nên**: Tự động hóa việc đăng bài lên mạng xã hội ngay từ đầu — rủi ro brand damage cao hơn lợi ích tiết kiệm thời gian.
