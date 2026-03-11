# Giới Thiệu Kế Hoạch Training OpenClaw

> Tài liệu này dùng để trình bày với công ty trước khi bắt đầu — giải thích mục đích, cấu trúc, và thu thập thông tin để điều chỉnh cho phù hợp.

---

## OpenClaw là gì — Nói ngắn gọn

OpenClaw là nền tảng chạy **AI agent cá nhân hóa** trên máy của công ty. Thay vì dùng các app AI chung chung (ChatGPT, Gemini...), mỗi agent được cấu hình riêng theo đúng workflow, dữ liệu, và quy tắc của team.

Giao tiếp qua **Telegram** — không cần cài thêm app, không cần training phức tạp về UI.

---

## Tại Sao Cần Training — Không Phải Cứ Cài Là Dùng Được

Điểm khác biệt lớn nhất của OpenClaw so với các tool AI thông thường: **agent làm đúng hay sai phụ thuộc 80% vào cách bạn viết instruction cho nó**, không phải vào bản thân công nghệ.

Một agent không được cấu hình đúng sẽ:
- Trả lời chung chung, không theo workflow thực tế
- Dùng sai tool, gây lỗi
- Không tuân thủ quy tắc nội bộ (tone, format, giới hạn hành động)

Training không chỉ là "học cách bấm nút" — mà là học cách **mô tả công việc của mình thành instruction** để agent hoạt động đúng ý.

---

## Cấu Trúc Kế Hoạch — 5 Phần, Mỗi Phần Một Mục Đích Rõ

### Phần 1 — Infrastructure *(Admin, ~4 giờ)*
**Mục đích**: Cài đặt hệ thống đúng cách, bảo mật từ đầu.
**Tại sao cần**: Nếu bỏ qua phần này, API key có thể bị lộ, agent bị treo không ai biết cách restart, chi phí vượt kiểm soát.
**Ai học**: Chỉ cần 1 người Admin — không cần cả team.

### Phần 2 — Hiểu Agent Hoạt Động Thế Nào *(Cả team, ~2 giờ)*
**Mục đích**: Xây nền tảng tư duy — tại sao agent làm đúng/sai, output nào cần verify, output nào tin được.
**Tại sao cần**: Không hiểu cơ chế → dùng sai kỳ vọng → thất vọng và bỏ tool sau 2 tuần. Đây là phần tạo ra sự khác biệt giữa team dùng AI hiệu quả và team dùng AI "cho vui".
**Ai học**: Cả team.

### Phần 3 — Demo Các Agent Thực Chiến *(Cả team, ~3 giờ)*
**Mục đích**: Thấy tận mắt các agent đang chạy, hiểu được ngay giá trị thực tế.
**Tại sao cần**: Người ta chỉ tin khi thấy. Demo live > giải thích lý thuyết.
**Ai học**: Cả team — mỗi người sẽ thấy agent nào phù hợp với mình nhất.
**Nội dung**: Google Workspace (Gmail, Sheets, Calendar), Facebook Group Monitor, Daily Digest, Content Repurposing.

### Phần 4 — Vận Hành Hàng Ngày *(Cả team, ~1.5 giờ)*
**Mục đích**: Biết cách dùng đúng, biết khi nào cần verify output, biết xử lý tình huống thường gặp.
**Tại sao cần**: Không có phần này, team sẽ hoang mang khi agent lỗi lần đầu và không biết phải làm gì.
**Ai học**: Cả team.

### Phần 5 — Workshop Tự Thiết Kế Agent *(Cả team, ~2-3 giờ)*
**Mục đích**: Mỗi người tự viết instruction (SOUL.md) cho agent phục vụ đúng công việc của mình.
**Tại sao cần**: Agent template sẵn không bao giờ fit 100% — workshop này biến team từ "người dùng tool" thành "người làm chủ tool". Đây là phần quyết định hiệu quả dài hạn.
**Output**: Mỗi người có 1 draft agent design, Admin sẽ deploy sau workshop.

---

## Lịch Trình Gợi Ý

| Buổi | Phần | Đối tượng | Thời lượng |
|------|------|-----------|------------|
| 1 | Infrastructure | Admin | ~4 giờ |
| 2 | Hiểu agent + Demo agents | Cả team | ~5 giờ |
| 3 | Vận hành + Workshop | Cả team | ~4 giờ |

**Tổng**: 3 buổi, ~2 tuần. Sau đó 2-4 tuần vận hành thực tế trước khi review và mở rộng.

---

## Use Cases Có Thể Triển Khai Ngay Sau Training

| Use Case | Thời gian tiết kiệm/tuần |
|----------|--------------------------|
| Monitor Facebook group đối thủ tự động | 3-5 giờ |
| Trend digest ngành gửi mỗi sáng | 5-7 giờ |
| Báo cáo campaign tự động vào Google Sheets | 2-3 giờ |
| Content repurposing 1 bài → nhiều kênh | 2-4 giờ |
| Phân loại inbox + draft reply | 2-3 giờ |
| Research đối thủ theo yêu cầu | 1-2 giờ/lần |

---

---

## ❓ Câu Hỏi Khảo Sát — Để Điều Chỉnh Giáo Trình

> Trả lời những câu hỏi dưới đây giúp tôi điều chỉnh nội dung, thứ tự ưu tiên, và mức độ kỹ thuật cho phù hợp với team.

---

### A. Về Team

1. Team marketing có bao nhiêu người? Họ làm gì chính? (content, performance, community, brand...)

2. Trong team có ai có background kỹ thuật không (biết code, dùng tốt terminal)? Họ có thể đảm nhận vai Admin không?

3. Mức độ quen với AI tool hiện tại của team thế nào?
   - [ ] Chưa dùng gì
   - [ ] Dùng ChatGPT/Gemini để hỏi đáp thông thường
   - [ ] Đã dùng AI để viết content, tóm tắt
   - [ ] Đã thử tích hợp AI vào workflow thực tế

4. Team đang dùng Telegram chưa? Hay cần giới thiệu từ đầu?

---

### B. Về Công Việc Hiện Tại

5. Mỗi tuần team dành bao nhiêu giờ cho những việc lặp đi lặp lại (báo cáo, copy data, tổng hợp thông tin)?

6. Kênh marketing chính đang dùng là gì? (Facebook, TikTok, Zalo, Instagram, email...)

7. Hiện tại ai đang theo dõi đối thủ? Họ làm thế nào — vào tay xem hay có tool gì hỗ trợ?

8. Quy trình tạo content hiện tại như thế nào? Từ brief → publish mất bao nhiêu bước và bao nhiêu người?

9. Có đang dùng Google Workspace (Gmail, Drive, Sheets, Calendar) không? Toàn bộ team hay chỉ một số người?

---

### C. Về Kỳ Vọng

10. Sau khi training xong, kết quả nào sẽ khiến bạn đánh giá chương trình này là "thành công"?

11. Pain point lớn nhất hiện tại của team marketing là gì? (thiếu thời gian, thiếu insight, chậm phản ứng với trend, content không đủ...)

12. Có use case cụ thể nào bạn muốn ưu tiên giải quyết trước không?

13. Ngân sách chi phí LLM (API) hàng tháng dự kiến là bao nhiêu? Hay chưa xác định?

---

### D. Về Kỹ Thuật & Bảo Mật

14. Công ty có Mac mini hoặc máy tính nào chạy 24/7 để deploy agent không? Hay cần tư vấn về phần cứng?

15. Có yêu cầu đặc biệt về bảo mật dữ liệu không? (data không được ra ngoài server công ty, không dùng cloud AI...)

16. Ai sẽ quản lý API key và chi phí? IT hay Marketing tự quản?

17. Công ty có policy về việc dùng AI tool xử lý dữ liệu khách hàng không?

---

### E. Về Logistics

18. Thời gian training phù hợp: sáng hay chiều? Cuối tuần hay trong tuần?

19. Hình thức training: offline tại văn phòng, online qua Meet/Zoom, hay kết hợp?

20. Sau training, ai sẽ là đầu mối liên hệ khi có vấn đề kỹ thuật? (Internal Admin hay nhờ trainer support tiếp?)
