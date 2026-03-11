# Module 5: Workshop — Tự Thiết Kế Agent Của Mình

> **Đối tượng**: Cả team
> **Thời lượng**: 2-3 giờ
> **Format**: Mỗi người tự làm, sau đó review chéo

---

## Mục tiêu

Kết thúc workshop, mỗi người có **1 SOUL.md draft** cho agent phục vụ đúng công việc của mình.

---

## Bước 1: Xác Định Use Case (15 phút)

Trả lời 4 câu hỏi:

**1. Agent này làm gì mỗi ngày?**
> Ví dụ: "Tổng hợp bài mới từ 3 Facebook group đối thủ, gửi báo cáo sáng"

**2. Input thường là gì?**
> Ví dụ: "Link group Facebook, keyword cần theo dõi"

**3. Output trông như thế nào?**
> Ví dụ: "Card mỗi bài: tên sản phẩm, giá, nhận xét từ bình luận, link bài gốc"

**4. Điều agent KHÔNG được làm?**
> Ví dụ: "Không tự đăng reply bình luận, không share thông tin nội bộ ra ngoài"

---

## Bước 2: Viết SOUL.md Draft (45 phút)

Dùng template này, điền vào phần `[...]`:

```markdown
# [Tên Agent]

Bạn là [mô tả vai trò] của [tên công ty/team].
Hỗ trợ [tên người dùng hoặc team] thực hiện:
- [Nhiệm vụ 1]
- [Nhiệm vụ 2]
- [Nhiệm vụ 3]

## Tính cách & Phong cách

- Trả lời bằng tiếng Việt
- [Ngắn gọn / Chi tiết / Dạng bullet / Dạng báo cáo...]
- [Tone: chuyên nghiệp / thân thiện / súc tích...]

## Quy tắc BẮT BUỘC

- [Quy tắc 1 — thường là về safety: không tự gửi/đăng/xóa]
- [Quy tắc 2 — về output format]
- [Quy tắc 3 — về nguồn thông tin]

## Ví dụ Lệnh Thường Dùng

- "[Ví dụ lệnh 1]"
- "[Ví dụ lệnh 2]"
- "[Ví dụ lệnh 3]"

## Điều Agent Không Làm

- [Điều 1]
- [Điều 2]
```

---

## Bước 3: Review Chéo (30 phút)

Đổi SOUL.md draft cho người ngồi bên cạnh. Người review trả lời:

1. **Đọc xong, bạn hiểu agent này làm gì không?** (Nếu không → phần mô tả cần rõ hơn)
2. **Có quy tắc nào thiếu không?** (Nghĩ đến tình huống agent có thể làm sai)
3. **Output format có đủ cụ thể không?** (Agent cần biết output trông như thế nào)

---

## Bước 4: Pitching (30 phút)

Mỗi người trình bày ngắn gọn (3 phút):
- Agent của bạn làm gì?
- Sẽ tiết kiệm bao nhiêu thời gian/tuần?
- Khó khăn gì khi viết SOUL.md?

---

## Checklist SOUL.md Tốt

- [ ] Mô tả rõ vai trò trong 1-2 câu
- [ ] Liệt kê ít nhất 3 nhiệm vụ cụ thể
- [ ] Có quy tắc về ngôn ngữ (tiếng Việt/Anh)
- [ ] Có quy tắc safety (không tự gửi/đăng/xóa)
- [ ] Có mô tả output format mong muốn
- [ ] Có ít nhất 2-3 ví dụ lệnh thực tế
- [ ] Có danh sách điều không được làm

---

## Sau Workshop

Admin sẽ:
1. Tổng hợp SOUL.md drafts từ team
2. Kết hợp với config kỹ thuật (TOOLS.md, SKILL.md)
3. Deploy agent → cho team test trong 1 tuần
4. Thu feedback → vòng lặp cải tiến tiếp theo
