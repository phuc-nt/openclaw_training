# Use Cases — Có Thể Làm Ngay

> Tất cả use cases dưới đây có thể triển khai ngay với OpenClaw hiện tại, không cần viết thêm skill/script mới.

---

## UC-01: Competitor Intelligence — Monitor Group Đối Thủ

**Vấn đề**: Mỗi ngày phải vào tay 3-5 Facebook group đối thủ để xem họ đang push gì.

**Giải pháp**: Facebook Group Monitor cron job chạy mỗi 4 giờ → tổng hợp bài mới từ tất cả group → gửi 1 báo cáo duy nhất.

**Output mẫu:**
```
🔍 Competitor Intel — 14:00 11/03/2026

[Brand A - Group Mua Bán]
📦 Áo thun basic oversize — 150k
💬 Bình luận: 12 người hỏi size, 3 người chê chất liệu
🔗 [link bài]

[Brand B - Community]
📢 Flash sale cuối tuần -30% toàn bộ collection hè
🔗 [link bài]
```

**Tiết kiệm**: ~30-45 phút/ngày lướt thủ công.

---

## UC-02: Daily Trend Digest — Cập Nhật Xu Hướng Ngành

**Vấn đề**: Không có thời gian đọc Reddit, YouTube, báo ngành mỗi sáng.

**Giải pháp**: Daily Digest agent tự crawl theo keyword ngành → gửi tóm tắt 8h sáng.

**Cấu hình ví dụ cho ngành thời trang:**
- Reddit: r/femalefashionadvice, r/malefashionadvice, r/streetwear
- YouTube: channel của các fashion blogger Việt
- RSS: Vogue Vietnam, Elle Vietnam

**Tiết kiệm**: ~1 giờ/ngày đọc tin.

---

## UC-03: Báo Cáo Campaign Tự Động Vào Google Sheets

**Vấn đề**: Mỗi tuần mất 2-3 giờ copy số liệu từ email agency vào Sheet tổng hợp.

**Giải pháp**: Personal agent đọc Gmail → tìm email báo cáo từ agency → extract số liệu → điền vào Sheet template.

**Lệnh mẫu:**
```
"Đọc email từ [tên agency] trong tuần này, tìm báo cáo campaign,
điền vào Sheet [tên sheet]: cột Ngày, Reach, Click, CPC, CPE"
```

**Tiết kiệm**: 2-3 giờ/tuần.

---

## UC-04: Content Repurposing — 1 Bài → Nhiều Format

**Vấn đề**: Có 1 bài blog/báo cáo nhưng cần đăng lên Facebook, LinkedIn, Zalo với format khác nhau.

**Giải pháp**: Content Repurposing agent tự viết lại theo đúng format từng kênh.

**Lệnh mẫu:**
```
"Từ bài này [link hoặc paste nội dung], viết lại thành:
1. Caption Facebook (max 300 chữ, có emoji, CTA cuối)
2. Post LinkedIn (tone chuyên nghiệp, không emoji)
3. Bản tin Zalo ngắn (max 150 chữ)"
```

**Tiết kiệm**: 30-45 phút/bài.

---

## UC-05: Inbox Triage — Phân Loại Email Và Draft Reply

**Vấn đề**: Inbox ngập email, khó biết cái nào quan trọng cần xử lý ngay.

**Giải pháp**: Personal agent đọc inbox → phân loại → draft reply cho email cần trả lời.

**Lệnh mẫu:**
```
"Xem inbox Gmail hôm nay, phân loại:
- Khẩn cần trả lời ngay
- Cần xử lý trong tuần
- FYI không cần reply
- Spam/newsletter

Với email khẩn, soạn draft reply tạm"
```

**Quan trọng**: Agent chỉ soạn draft, không tự gửi. User review rồi mới gửi.

---

## UC-06: Research Đối Thủ Theo Yêu Cầu

**Vấn đề**: Cần thông tin nhanh về một brand mới hoặc sản phẩm đối thủ vừa ra.

**Giải pháp**: Personal agent web search + tổng hợp từ nhiều nguồn.

**Lệnh mẫu:**
```
"Research [tên brand/sản phẩm]:
- Họ đang target khách hàng nào?
- Điểm khác biệt so với mình là gì?
- Pricing strategy
- Kênh marketing đang dùng
- Review từ khách hàng (tích cực và tiêu cực)

Nguồn: website chính thức, Facebook, Google reviews, báo online"
```

**Thời gian**: Agent làm trong 2-3 phút, thủ công mất 1-2 giờ.
