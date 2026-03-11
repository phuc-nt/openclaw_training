# Module 4: Vận Hành Hàng Ngày

> **Đối tượng**: Cả team
> **Thời lượng**: 1.5 giờ
> **Mục tiêu**: Biết cách dùng agent hiệu quả và xử lý tình huống thường gặp

---

## 4.1 Giao Tiếp Hiệu Quả Với Agent

### Nguyên tắc viết lệnh tốt

**❌ Lệnh mơ hồ:**
> "Tổng hợp thông tin về đối thủ"

**✅ Lệnh rõ ràng:**
> "Tìm 3 bài đăng mới nhất của [Tên brand] trên Facebook group [tên group], tóm tắt: họ đang promote sản phẩm gì, giá bao nhiêu, phản ứng của bình luận ra sao"

**Công thức lệnh hiệu quả:**
```
[Hành động] + [Đối tượng cụ thể] + [Output mong muốn] + [Giới hạn nếu có]
```

### Khi agent hiểu sai
- Không chửi agent 😄 — cung cấp thêm context
- "Không phải vậy, ý tôi là..." → agent sẽ điều chỉnh
- Nếu agent liên tục sai → báo Admin để sửa SOUL.md

### Reset session khi cần
Nếu agent đang "kẹt" trong một hướng suy nghĩ sai hoặc lỗi liên tục:
```
Gửi: /new
```
Session mới sẽ bắt đầu, agent quên toàn bộ conversation cũ.

---

## 4.2 Đọc Output Agent — Những Gì Cần Verify

### Luôn verify trước khi dùng
| Loại thông tin | Mức độ cần verify |
|----------------|-------------------|
| Số liệu thống kê | Cao — agent có thể hallucinate |
| Link URL | Trung bình — kiểm tra link có hoạt động không |
| Nội dung tổng hợp từ web search | Thấp — thường có nguồn kèm theo |
| Draft email/content | Thấp — chỉ cần review tone và accuracy |

### Khi agent trích dẫn nguồn
Luôn có phần "Nguồn tham khảo" hoặc link đính kèm. Click kiểm tra ít nhất 1-2 nguồn quan trọng trước khi dùng số liệu trong báo cáo.

---

## 4.3 Xử Lý Tình Huống Thường Gặp

### Agent không phản hồi sau 2-3 phút
1. Thử gửi lại tin nhắn
2. Gửi `/new` để reset session
3. Nếu vẫn không phản hồi → **báo Admin** (gateway có thể bị treo)

### Agent trả lời "Tôi không có quyền truy cập..." hoặc lỗi tool
- Đây là vấn đề config, không phải lỗi của user
- Chụp màn hình error message → gửi cho Admin

### Agent tổng hợp thiếu thông tin
- Hỏi lại cụ thể hơn: "Bài của [tên tác giả] bị thiếu link, tại sao?"
- Hoặc báo Admin để kiểm tra script

### Agent bỗng dưng dùng tiếng Anh
- Nhắc: "Trả lời bằng tiếng Việt nhé"
- Nếu xảy ra thường xuyên → báo Admin, có thể cần sửa SOUL.md

---

## 4.4 Cron Jobs — Đọc Báo Cáo Tự Động

Agent gửi báo cáo tự động vào giờ đã định. Một số tip:

**Đặt tên rõ cho nhóm Telegram:**
- Mỗi agent nên có bot/channel riêng để không bị lẫn
- Ví dụ: bot `@company_daily_digest_bot`, `@company_fb_monitor_bot`

**Khi báo cáo tự động không đến:**
- Đợi thêm 5-10 phút (cron có thể delay nhẹ)
- Nếu quá 30 phút → báo Admin kiểm tra cron job

**Không cần lo nếu thỉnh thoảng miss:**
- Agent có cơ chế track "đã thấy rồi" — sẽ không gửi lại bài cũ
- Lần scrape tiếp theo sẽ gửi bài mới kể từ lần cuối

---

## 4.5 Feedback Vòng Lặp Cải Tiến

Chất lượng agent cải thiện theo thời gian NẾU team feedback đúng cách:

**Feedback tốt (cho Admin):**
> "Agent tổng hợp bài FB thiếu phần giá. Ví dụ bài hôm nay của [tên] có giá 150k nhưng agent không mention. Link: [link]"

**Feedback không actionable:**
> "Agent dở quá"

**Template feedback chuẩn:**
```
Vấn đề: [Mô tả gì sai]
Ví dụ cụ thể: [Input/Output thực tế]
Mong muốn: [Output đúng trông như thế nào]
```

---

## 4.6 Chi Phí — Nên Biết

Chi phí LLM tính theo số token (số từ) xử lý:
- Agent chạy cron nhiều → chi phí cao hơn
- Agent dùng Claude cho task đơn giản → tốn kém không cần thiết

Admin sẽ theo dõi và tối ưu model theo thời gian. User chỉ cần biết:
- **Không chạy task lặp đi lặp lại không cần thiết** (ví dụ: hỏi cùng 1 câu 10 lần)
- **Báo Admin** nếu thấy chi phí tháng bất thường tăng cao
