### TEMPLATE LẬP KẾ HOẠCH TRIỂN KHAI

# Kế hoạch Triển khai

## 1. Mục tiêu (Goal)

- [Mô tả ngắn gọn tính năng hoặc lỗi cần xử lý]

## 2. Tiêu chí hoàn thành (Success Criteria)

- [ ] Tiêu chí 1
- [ ] Tiêu chí 2
- [ ] Không phát sinh regression ngoài phạm vi

## 3. Yêu cầu & Ngữ cảnh (Requirements & Context)

- [ ] Đã đọc `ARCHITECTURE.md`
- [ ] Đã đọc `PRODUCT.md`
- [ ] Đã đọc `skill.md`
- [ ] Đã đọc `note.md`
- [ ] Đã đọc `Api_References.md`
- [ ] Đã đọc `Database.md`
- Ràng buộc nghiệp vụ/kỹ thuật liên quan:
  - [Ghi rõ ràng]

## 4. Phạm vi tác động (Impact Scope)

- Trong phạm vi:
  - [Thành phần A]
  - [Thành phần B]
- Ngoài phạm vi:
  - [Không thay đổi gì để tránh scope creep]

## 5. Triển khai từng bước (Implementation Steps)

1. [Bước 1]
2. [Bước 2]
3. [Bước 3]

## 6. File dự kiến tạo mới / chỉnh sửa

- `[path/file-1]` (Create/Update)
- `[path/file-2]` (Create/Update)

## 7. Kế hoạch Unit Test

- Test cases Happy Path:
  - [Case 1]
- Test cases Edge Cases:
  - [Case 2]
- Test cases Negative/Error:
  - [Case 3]
- Dependencies cần mock:
  - [Dependency A]

## 8. Kế hoạch chạy test

- Lệnh chính: `dotnet test`
- Nếu fail: phân tích lỗi -> sửa -> test lại đến khi pass hoặc blocked.

## 9. Rủi ro & Rollback

- Rủi ro chính:
  - [Rủi ro 1]
- Phương án rollback:
  - [Rollback 1]

## 10. Điều kiện sang bước Code

- Chỉ bắt đầu code sau khi user phản hồi `accept` plan.
