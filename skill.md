---
name: aspnet-backend
description: Xây dựng và chỉnh sửa backend ASP.NET Core Web API theo đúng quy ước dự án, bắt buộc đi theo flow Plan -> Accept -> Code -> Unit Test -> Test -> Git.
---

# ASP.NET Core Backend Skill

Skill này hướng dẫn AI Agent triển khai backend ASP.NET Core Web API đúng chuẩn dự án, nhất quán từ kế hoạch, code, test đến commit/push.

> Nguyên tắc ngôn ngữ: phân tích/kế hoạch/báo cáo dùng Tiếng Việt. Tên class/method/biến dùng tiếng Anh.

## 1. Workflow bắt buộc

### Bước 1 - Đọc context trước khi lập plan
Phải đọc và nắm các file:
- `ARCHITECTURE.md`
- `PRODUCT.md`
- `Api_References.md`
- `Database.md`
- `note.md`
- `skill.md` (file này)
- `Plan.md`
- `Testing.md`
- `Git.md`

### Bước 2 - Lập plan
- Tạo plan theo template `Plan.md`.
- Nêu rõ: goal, success criteria, scope, steps, test strategy, risk/rollback.
- Chưa được code ở bước này.

### Bước 3 - Chờ user accept
- Chỉ bắt đầu triển khai khi user phản hồi rõ ràng `accept`.

### Bước 4 - Viết code
- Code rõ ràng, dễ bảo trì, tách trách nhiệm.
- Nếu sửa file global (ví dụ `Program.cs`, middleware, model schema) phải nêu rõ tác động trong plan.
- Tuân thủ coding standards ở mục 2.

### Bước 5 - Viết unit test
- Bắt buộc thêm/cập nhật unit test cho mọi thay đổi logic.
- Cover tối thiểu happy path + edge cases + negative/error cases.
- Mock dependencies bên ngoài để test độc lập.

### Bước 6 - Chạy test
- Chạy `dotnet test`.
- Nếu fail: fix và test lại đến khi pass hoặc blocked có lý do rõ ràng.

### Bước 7 - Git
- Chỉ commit/push khi test pass.
- Chỉ push sau khi user duyệt cuối.
- Commit message theo chuẩn `feat|fix|refactor: ...`.

## 2. Coding standards backend

### Service
- Interface và implementation có thể để cùng file theo convention dự án.
- Method public cho Controller gọi phải rõ nghĩa.
- Dùng `async/await` nhất quán.
- Query đọc dữ liệu ưu tiên `.AsNoTracking()` khi phù hợp.

### Controller
- Controller chỉ orchestration, không chứa business logic nặng.
- Validate input ở boundary phù hợp.
- Response format theo contract của dự án.

### Transaction
- Khi thao tác nhiều bảng có phụ thuộc dữ liệu, dùng transaction phù hợp.
- Cân nhắc isolation level cho nghiệp vụ nhạy cảm (số dư, tồn kho...).

## 3. Chuẩn API response (tham chiếu)

```json
{ "code": 200, "message": "Thành công", "data": {} }
```

```json
{ "code": 400, "message": "Lỗi nghiệp vụ" }
```

```json
{ "code": 404, "message": "Không tìm thấy dữ liệu" }
```

```json
{ "code": 500, "message": "Đã xảy ra lỗi, vui lòng thử lại" }
```

## 4. Unit test standards

- Đặt tên test theo format: `MethodName_ShouldExpectedResult_WhenCondition`.
- Áp dụng AAA pattern (Arrange, Act, Assert).
- Không gọi phụ thuộc ngoài thật trong unit test.
- Test phải deterministic và chạy độc lập.

## 5. Done checklist trước khi báo hoàn tất

- [ ] Plan đã được user accept.
- [ ] Code đã hoàn tất đúng scope.
- [ ] Unit test đã thêm/cập nhật.
- [ ] `dotnet test` pass.
- [ ] Đã báo user xin duyệt trước push.
