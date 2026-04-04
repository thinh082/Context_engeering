### TESTING PATTERN CHUẨN CHO DỰ ÁN

# 1. Mục tiêu
Chuẩn hóa cách viết unit test và cách chạy test để đảm bảo mọi thay đổi đều được kiểm chứng trước khi commit/push.

# 2. Quy ước đặt tên test
Dùng format:
- `MethodName_ShouldExpectedResult_WhenCondition`

Ví dụ:
- `CreateAsync_ShouldReturn200_WhenRequestIsValid`
- `CreateAsync_ShouldReturn400_WhenEmailAlreadyExists`

# 3. Cấu trúc test (AAA)
Mọi unit test nên theo pattern AAA:
- Arrange: Chuẩn bị input, mock dependencies, dữ liệu nền.
- Act: Gọi method cần test.
- Assert: Kiểm tra kết quả trả về và side effects.

# 4. Coverage tối thiểu bắt buộc
Mỗi thay đổi logic phải có test cho:
- Happy path (luồng thành công).
- Edge cases (biên dữ liệu/trạng thái đặc biệt).
- Negative/Error cases (validate fail, not found, exception, business reject).

# 5. Mock dependencies
- Mock các dependency bên ngoài logic chính (repository/service ngoài, HTTP client, clock, cache...).
- Không gọi DB thật trong unit test.
- Ưu tiên test nhanh, độc lập, deterministic.

# 6. Mẫu khung unit test
```csharp
[Fact]
public async Task CreateAsync_ShouldReturn400_WhenEmailAlreadyExists()
{
    // Arrange
    var request = new CreateUserRequest { Email = "existing@mail.com" };
    _repositoryMock.Setup(x => x.ExistsByEmailAsync(request.Email)).ReturnsAsync(true);

    // Act
    var result = await _service.CreateAsync(request);

    // Assert
    Assert.Equal(400, result.code);
    Assert.Equal("Email đã tồn tại trong hệ thống", result.message);
}
```

# 7. Quy trình chạy test bắt buộc
1. Chạy `dotnet test`.
2. Nếu FAIL:
   - Đọc thông tin fail (assert, stack trace, test name).
   - Xác định lỗi ở code hay ở test.
   - Sửa lỗi.
   - Chạy lại `dotnet test`.
3. Lặp lại đến khi PASS hoặc bị chặn bởi nguyên nhân rõ ràng.

# 8. Chuẩn báo cáo kết quả test cho user
Khi hoàn tất, báo ngắn gọn:
- Tổng số test chạy.
- Kết quả pass/fail.
- Nhóm test chính đã cover (happy/edge/error).
- Nếu còn fail: nêu rõ nguyên nhân và hướng xử lý tiếp.
