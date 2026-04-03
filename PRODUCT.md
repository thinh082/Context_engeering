### NGHIỆP VỤ PHẦN MỀM NẰM Ở ĐÂY

# ĐÂY LÀ MẪU

# Tổng quan Sản phẩm

Đây là một hệ thống backend [B2B/B2C E-commerce/SaaS] được thiết kế để xử lý [mô tả ngắn gọn giá trị cốt lõi của bạn vào đây].

## Các Module Cốt lõi

1. **Quản lý Người dùng (User Management)**: Xử lý xác thực (JWT) và phân quyền RBAC (các vai trò Admin, Manager, User).
2. **Quản lý Đơn hàng (Order Management)**: Xử lý đơn hàng của người dùng, tích hợp với cổng thanh toán, và cập nhật hàng tồn kho.
3. **Kho hàng (Inventory)**: Theo dõi mức tồn kho và kích hoạt cảnh báo khi sắp hết hàng.

## Quy tắc Nghiệp vụ (Business Rules)

- Người dùng không thể thanh toán nếu giỏ hàng của họ chứa các mặt hàng đã hết.
- Mật khẩu phải được băm (hash) bằng BCrypt trước khi lưu.
- Xóa mềm (Soft-delete) được sử dụng cho tất cả các thực thể chính (IsDeleted = true). KHÔNG BAO GIỜ xóa cứng (hard delete) các bản ghi khỏi cơ sở dữ liệu.
