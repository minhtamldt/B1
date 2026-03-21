# Antigravity `.agent` Directory

Thư mục này được sử dụng để định nghĩa các cấu hình, rules và workflows tùy chỉnh cho Antigravity (Google DeepMind agent).

## Cấu trúc

- `workflows/`: Chứa các file Markdown (`.md`) định nghĩa các bước chuẩn mực để thực hiện một công việc cụ thể. Khi bạn yêu cầu thực hiện hoặc dùng slash command, Agent sẽ đọc các file này và làm theo.

### Cách viết Workflow

Tạo một file `.md` trong thư mục `workflows/`, với định dạng YAML frontmatter ở đầu file:

```markdown
---
description: [Mô tả ngắn gọn về workflow, ví dụ: Cách build và deploy ứng dụng]
---

# Các bước thực hiện:
1. Bước 1: Kiểm tra trạng thái git bằng `git status`.

// turbo
2. Bước 2: Tự động chạy lệnh `npm install` (sử dụng annotation `// turbo` phía trên để agent tự chạy không cần hỏi ý kiến user cho bước này).

3. Bước 3: ...
```

*Lưu ý: Nếu một workflow chứa annotation `// turbo-all` ở bất kỳ đâu, agent sẽ tự động chạy TẤT CẢ các bước chứa lệnh command console mà không cần chờ user xác nhận.*
