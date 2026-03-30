# Module 3: Các Agent Thực Chiến

> **Đối tượng**: Cả team
> **Thời lượng**: 3 giờ (demo + thực hành)
> **Format**: Admin demo live, User thực hành ngay trên Telegram

---

## 3.1 Personal Agent + Google Workspace

### Làm được gì
- **Gmail**: Đọc inbox, tóm tắt email quan trọng, draft reply
- **Google Calendar**: Xem lịch, tạo event, nhắc nhở
- **Google Drive**: Upload file, tạo folder, share
- **Google Sheets**: Đọc/ghi data, tạo báo cáo
- **Google Docs**: Tạo và chỉnh sửa document

### Demo gợi ý
```
User → Agent: "Tóm tắt 5 email chưa đọc quan trọng nhất trong tuần này"
User → Agent: "Tạo sheet tổng hợp kết quả campaign tháng 3, cột: Kênh, Reach, Click, CPE"
User → Agent: "Soạn email gửi agency về brief campaign Q2, nội dung: [brief]"
```

### Lưu ý khi dùng
- Agent sẽ **draft** email, không tự gửi — phải confirm rõ "gửi đi" mới gửi
- Tích hợp qua `gws` CLI (Google Workspace CLI chính thức của Google)
- Lần đầu setup cần admin cấu hình OAuth, sau đó user dùng bình thường

---

## 3.2 Facebook Group Monitor

### Làm được gì
- Tự động scrape bài mới từ Facebook group theo lịch (mỗi 2-4 giờ)
- Dùng AI vision để đọc nội dung từ ảnh trong bài (book cover, product photo...)
- Tổng hợp thành card: tác giả, nội dung, giá, link bài gốc
- Alert ngay khi có bài mới thỏa điều kiện

### Tại sao không dùng Facebook API?
Facebook Graph API đã **khai tử endpoint Groups Feed từ tháng 4/2024**. Không còn API nào để đọc bài group — browser automation là cách duy nhất hiện tại.

### Demo gợi ý
```
Cron job tự chạy mỗi 4 giờ → agent gửi:
"🔔 3 bài mới từ [Tên Group]

📦 Tên sản phẩm — Người đăng
💰 Giá: xxx
🔗 https://facebook.com/groups/..."
```

### Lưu ý khi dùng
- Cần login Facebook 1 lần duy nhất (admin setup)
- Nên dùng tài khoản phụ, không dùng tài khoản chính
- Interval hợp lý: 2-4 giờ/lần — quá dày dễ bị Facebook flag
- Chỉ monitor group mình là thành viên

---

## 3.3 Daily Digest Agent

### Làm được gì
- Mỗi sáng tự crawl Reddit, YouTube, RSS feeds theo danh sách keyword/subreddit đã cấu hình
- Tóm tắt và dịch sang tiếng Việt
- Gửi Telegram + lưu vào Google Drive

### Phù hợp cho marketing
- Theo dõi trend ngành không cần lướt mạng thủ công
- Monitor đối thủ có channel YouTube/Reddit
- Cập nhật tin tức ngành mỗi sáng

### Demo gợi ý
```
Cron 8:00 AM → Agent gửi:
"☀️ Daily Digest — 2026-03-11

📰 Reddit: r/marketing
• [Tên bài] — 1.2k upvotes — [tóm tắt 2-3 câu]
• ...

▶️ YouTube: [Channel tên]
• [Tên video] — [tóm tắt nội dung chính]"
```

### Cấu hình
Admin setup danh sách nguồn trong SOUL.md của agent. User có thể yêu cầu thêm/bớt nguồn — Admin sửa config.

---

## 3.4 Content Repurposing Agent

### Làm được gì
Nhận input là 1 nội dung dài → tự viết lại thành nhiều format:
- Caption Facebook (ngắn gọn, có CTA)
- Post LinkedIn (chuyên nghiệp hơn)
- Thread X/Twitter
- Script video ngắn (30-60s)
- Bản tin email

### Demo gợi ý
```
User → Agent: "Repurpose bài này thành caption Facebook và thread X:
[paste link bài blog hoặc nội dung]"

Agent trả về:
📘 Facebook Caption:
[nội dung]

🐦 Thread X (5 tweets):
1/ ...
2/ ...
```

### Lưu ý
- Agent viết draft, không tự đăng — user review và đăng thủ công hoặc qua tool scheduling
- Cần định nghĩa rõ brand voice trong SOUL.md: tone, từ ngữ đặc trưng, điều không được nói

---

## 3.5 So Sánh Nhanh

| Agent | Trigger | Output | Cần confirm? |
|-------|---------|--------|--------------|
| Personal + GWS | User chat | Draft email/doc, data vào Sheet | Có (trước khi gửi/xóa) |
| FB Group Monitor | Cron tự động | Card tổng hợp bài mới | Không |
| Daily Digest | Cron tự động | Báo cáo trend sáng | Không |
| Content Repurposing | User chat | Draft content nhiều format | Có (trước khi đăng) |
