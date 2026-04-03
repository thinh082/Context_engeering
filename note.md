### Bài học kinh nghiệm & Các lỗi cần tránh (Lessons Learned)

# MẪU

## 1. Sai lầm về Logic Nghiệp vụ (Business Logic Issues)

- **❌ Sai lầm thường gặp:** Cho phép xóa trực tiếp dữ liệu (hard-delete) khách hàng khỏi database khi có request.
- **✅ Cách xử lý ĐÚNG:** Tại dự án này, luôn áp dụng Xóa mềm (soft-delete). Set cờ `IsDeleted = true`. Luôn filter `IsDeleted == false` ở mọi truy vấn GET.

## 2. Sai lầm về Thực tế Code / Convention

- **❌ Sai lầm thường gặp:** Trả về lỗi chi tiết của Exception (stack trace) ra thẳng API response.
- **✅ Cách xử lý ĐÚNG:** Bắt buộc bắt lỗi thông qua Global Exception Middleware và trả về object chuẩn `ApiResponse<T>` với ErrorCode cụ thể.
