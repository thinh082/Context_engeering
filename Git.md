### WORKFLOW KHI DÙNG GIT

# 1. Điều kiện trước khi commit
- Plan đã được user `accept`.
- Code đã hoàn tất theo scope.
- Unit test cho phần thay đổi đã có.
- `dotnet test` đang PASS.

# 2. Chuẩn commit message
Dùng format:
- `feat: mô tả ngắn thay đổi`
- `fix: mô tả ngắn thay đổi`
- `refactor: mô tả ngắn thay đổi`

Ví dụ:
- `feat: add login endpoint validation`
- `fix: handle null patient address in service`
- `refactor: split booking service validation helpers`

# 3. Quy trình commit & push
1. Kiểm tra thay đổi bằng `git status` và `git diff`.
2. Commit với message đúng chuẩn.
3. Gửi user tóm tắt thay đổi + kết quả test để xin duyệt cuối.
4. Chỉ push khi user xác nhận.

# 4. Quy tắc bắt buộc
- Không push khi chưa có duyệt cuối từ user.
- Không push khi test chưa pass.
- Nếu còn lỗi: quay lại fix -> test lại -> rồi mới xin duyệt.
