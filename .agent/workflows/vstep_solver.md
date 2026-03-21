---
description: Tự động nhận diện dạng đề VSTEP Writing và tự động làm bài mẫu (đóng vai Candidate).
---

# VSTEP Exam Solver

Workflow này giúp hệ thống tự động hóa toàn bộ quá trình xử lý một đề thi VSTEP Writing. Khi người dùng gọi workflow này và cung cấp đề bài, hệ thống sẽ thực hiện các bước sau:

1. Đọc nội dung đề thi do người dùng cung cấp.
2. Áp dụng ngay skill **VSTEP Writing Type Identifier** để phân tích từ khóa và đưa ra kết luận nhanh đây là đề bài Task 1 hay Task 2.
3. Ngay sau khi xác định xong (không cần chờ người dùng xác nhận):
   - Nếu là **Task 1** (Thư/Email): Tự động áp dụng skill **VSTEP Writing Task 1 Candidate** để phân tích yêu cầu ngầm, viết một email phản hồi khoảng 120-150 từ (chuẩn B2-C1), và cuối cùng là giải thích các từ vựng ăn điểm.
   - Nếu là **Task 2** (Bài luận/Essay): Tự động áp dụng skill **VSTEP Writing Task 2 Candidate** để lập dàn ý luận điểm (Thesis & Main ideas), viết một bài essay 4-5 đoạn khoảng 250-300 từ (chuẩn B2-C1), và phân tích cấu trúc diễn đạt.
4. Trình bày đầu ra (Output) cuối cùng thật rõ ràng: Kết quả phân loại đề, Bài viết mẫu (Sample Answer), và Giải thích học thuật (Breakdown).
5. **QUAN TRỌNG:** Nếu người dùng cung cấp đề bài dưới dạng link tới một file (Ví dụ: `@[/đường/dẫn/đến/file.md]`), Agent **BẮT BUỘC** phải ghi kết quả bằng cách nối tiếp (append) toàn bộ nội dung bước 4 vào phía dưới cùng của file được cung cấp đó. Hãy dùng đường kẻ `---` ngăn cách đề bài bên trên và bài làm bên dưới để thuận tiện theo dõi.
