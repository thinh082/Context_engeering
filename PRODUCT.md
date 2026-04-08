### NGHIỆP VỤ PHẦN MỀM NẰM Ở ĐÂY

# Hệ thống Quản lý Phòng khám (Clinic Management Backend)

## Tổng quan Sản phẩm

Backend API cho phòng khám đa khoa: Quản lý bệnh nhân, bác sĩ, lịch khám, hóa đơn. Hỗ trợ CRUD, search, báo cáo.

## Các Module Cốt lõi

1. **Patient** (Bệnh nhân): CRUD, search by name/phone/email.
2. **Doctor** (Bác sĩ): CRUD, chuyên khoa.
3. **Appointment** (Lịch khám): Book/reschedule/cancel, validate conflict.
4. **Invoice** (Hóa đơn): Tạo từ appointment, thanh toán.
5. **Report**: Stats bệnh nhân theo ngày/tháng.

## Quy tắc Nghiệp vụ (Business Rules)

- **Soft-delete everywhere**: Luôn có `IsDeleted` bool, filter `WHERE IsDeleted = false`.
- **Appointment**:
  - Không book nếu doctor bận (check time overlap).
  - Cancel chỉ trong 24h trước giờ khám.
  - Max 5 lịch/ngày/doctor.
- **Patient**: Email/phone unique. Age >= 0.
- **Invoice**: Tự động tạo sau appointment hoàn tất. Status: Pending/Paid/Cancelled.
- **Validation**: DTO có method `Validate()` trả string lỗi.
- **Concurrency**: Transaction cho book appointment + update doctor schedule.
- **Auth**: Giả định JWT, check role ở Controller (Admin/Doctor/Patient).
