---
name: Generate Commit Message
description: Áp dụng AI phân tích thay đổi mã nguồn đã staged để tự động tạo một lệnh commit message chuẩn Conventional Commits.
---

# Generate Commit Message Skill

Skill này hướng dẫn Agent cách đóng vai trò tự động sinh ra (generate) một commit message chuyên nghiệp từ mã nguồn đang viết. Phù hợp cho những project sử dụng Conventional Commits.

## Khi nào sử dụng?
Kích hoạt tự động khi người dùng yêu cầu (ví dụ):
- "Tạo commit message cho tôi"
- "Generate commit message"
- "Viết commit dựa trên staged changes"
- Hoặc đơn giản: "gcm" (tên gọi tắt)

## Hướng dẫn cho Agent
Để generate được commit message đúng ý người dùng, vui lòng thực hiện ngầm định/công khai các bước:

1. **Thu thập thông tin**:
   - Sử dụng tool `run_command` để chạy lệnh `git status` trước nhằm kiểm tra nhánh hiện tại và xem có file nào đang ở trạng thái CẦN STAGE không. Nếu có quá nhiều file unstaged, có thể hỏi người dùng xem có muốn stage tất cả không (`git add .`).
   - Sau đó chạy lệnh `git diff --staged` để lấy toàn bộ danh sách các file đã sửa đổi (thuộc về commit sắp tạo).

2. **Phân tích thay đổi**:
   - Đọc kỹ những dòng code bị xóa (`-`) và dòng code được thêm (`+`).
   - Tóm tắt ý nghĩa chính của việc thay đổi này (ví dụ: đang fix bug không hiện thông báo, cải tiến thuật toán login...).

3. **Cấu Trúc Sinh Commit Message (Conventional Commits)**:
   - Tất cả commit message phải tuân theo cấu trúc: 
     `<type>[optional scope]: <description>`
     `[optional body]`
     `[optional footer(s)]`
   - Các `type` được phép sử dụng: `feat` (tính năng mới), `fix` (sửa lỗi), `docs` (tài liệu), `style` (format code như tab/space, không ảnh hưởng logic), `refactor` (cấu trúc lại code mà không thêm/sửa lỗi), `perf` (tối ưu tốc độ), `test` (sửa/thêm unit tests), `chore` (cấu hình môi trường, lib...).
   - `<description>`: Bắt buộc mở đầu bằng chữ thường (lowercase), không có dấu chấm ở cuối câu.
   - BẮT BUỘC toàn bộ nội dung trong câu lệnh commit (type, scope, description, body) phải được viết bằng **Tiếng Anh**.

4. **Định dạng hiển thị cho người dùng**:
   - Agent phản hồi dưới dạng 1 block code Bash chứa câu lệnh rút gọn để người dùng chỉ cần *Copy & Paste* hoặc *Run*.
     Ví dụ:
   ```bash
   git commit -m "feat(auth): add google login screen" -m "Integrate Firebase Auth and optimize login button UI."
   ```
   - Agent cũng đồng thời có thể đưa ra 2-3 tuỳ chọn (Options) khác nhau (Ví dụ: Option 1 ngắn gọn, Option 2 siêu chi tiết) để người dùng tự do lựa chọn.
