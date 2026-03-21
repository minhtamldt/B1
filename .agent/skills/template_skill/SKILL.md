---
name: Tên Skill (ví dụ: Cấu hình Dự án)
description: Mô tả ngắn gọn cấu trúc và chức năng của skill này.
---

# Hướng dẫn chi tiết cho Skill

Skill là tính năng mở rộng dùng để cung cấp thêm ngữ cảnh cho Agent (chứa hướng dẫn phức tạp, tập scripts phụ hoặc file tài nguyên). Bất cứ lúc nào thấy có từ khóa hoặc tình huống liên quan, tôi (Agent) sẽ tự động tìm đọc file `SKILL.md` này trước khi làm việc.

## Khi nào nên dùng Skill này?
[Mô tả các tình huống hoặc từ khóa cụ thể mà người dùng đưa ra thì Agent nên kích hoạt đọc file này]

## Hướng dẫn thao tác (Quy trình)
1. Bước 1: Agent cần kiểm tra...
2. Bước 2: Agent nên sử dụng các script trong thư mục `scripts/` (nếu có).
3. Những điều Agent tuyệt đối [KHÔNG ĐƯỢC LÀM] trong loại công việc này...

## Tham chiếu
Bạn có thể trỏ tới bất kì tài nguyên nào nằm trong các thư mục con (VD: `resources/template.json`, `examples/demo.txt`) để Agent lấy làm tham chiếu.
