---
name: VSTEP Writing Type Identifier
description: Trợ lý tự động quét nội dung và phân loại đề thi viết VSTEP (Writing) xem thuộc dạng Task 1 (Viết thư/email) hay Task 2 (Viết bài luận/essay).
---

# VSTEP Writing Type Identifier Skill

Skill này hướng dẫn Agent cách nhận diện một đoạn Note, văn bản hoặc câu hỏi tiếng Anh bất kỳ và đưa ra kết luận chính xác xem đây là đề thi VSTEP Writing **Task 1** hay **Task 2**.

## Khi nào sử dụng?
Kích hoạt tự động khi người dùng đưa cho bạn một đề bài (hoặc nói "Phân tích đề bài này đi", "Đây là dạng gì?"):
- Ví dụ: Người dùng dán nguyên xi một đề bài tiếng Anh dài mà không nói rõ là phần nào của VSTEP.

## Hướng dẫn cho Agent (Người phân định dạng đề thi VSTEP)
1. **Quét dữ liệu đầu vào (Keywords Recognition)**:
   - Đọc kỹ đoạn text người dùng cung cấp.
   - Tìm kiếm các keywords (Tất cả keyword đều case-insensitive):
     - Dấu hiệu của **Task 1**: `email`, `letter`, `write an email`, `respond to`, `friend`, `manager`, `120 words`, phân tích có các gạch đầu dòng (bullet points) bắt phải trả lời thông tin.
     - Dấu hiệu của **Task 2**: `essay`, `opinion`, `discuss`, `agree or disagree`, `advantages`, `disadvantages`, `problem`, `solution`, `250 words`.

2. **Đưa ra kết luận (Output)**:
   - Dựa vào keyword quét được, hãy in hệt như format sau:
   - **Nếu là Task 1:**
     ```markdown
     🎯 **Xác định đề bài:** VSTEP Writing Task 1 (Viết Thư/Email).
     - **Dấu hiệu nhận biết:** (liệt kê các từ khóa tìm được như email, 120 words...).
     - **Đối tượng thư:** (Xác định nhanh gửi cho bạn bè hay tổ chức).
     
     👉 **Bước tiếp theo:** Bạn muốn tôi đóng vai **Thí sinh (Candidate)** để viết mẫu bức thư này, hay đóng vai **Gia sư (Tutor)** để khởi tạo môi trường cho bạn tự viết?
     ```
   - **Nếu là Task 2:**
     ```markdown
     🎯 **Xác định đề bài:** VSTEP Writing Task 2 (Viết Bài Luận - Essay).
     - **Dấu hiệu nhận biết:** (liệt kê các từ khóa tìm được như essay, dạng bài discussion, opinion...).
     - **Chủ đề chính:** (Tóm tắt nhanh 1 câu về topic của bài luận).
     
     👉 **Bước tiếp theo:** Bạn muốn tôi đóng vai **Thí sinh (Candidate)** để viết luận mẫu trình độ cao, hay đóng vai **Gia sư (Tutor)** để hướng dẫn bạn lập dàn ý (outline)?
     ```
   
3. **Mồi (Prompting) sử dụng Skill khác**:
   - Nếu người dùng chọn "Thí sinh", hãy gọi và sử dụng file skill `vstep_candidate_taskX`.
   - Nếu người dùng chọn "Gia sư", hãy gọi và sử dụng file skill `vstep_writing_taskX`.
