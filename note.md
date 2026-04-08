### Bài học kinh nghiệm & Các lỗi cần tránh (Lessons Learned)

## 1. Sai lầm về Logic Nghiệp vụ (Business Logic Issues)

- **❌ Sai**: Hard-delete Patient → Mất lịch sử.
  **✅ Đúng**: Soft-delete `IsDeleted = true`. Query luôn filter `!IsDeleted`.
- **❌ Sai**: Book appointment không check doctor availability → Overbook.
  **✅ Đúng**: Query overlap `WHERE doctorId = @id AND (start < @end AND end > @start)`.

## 2. Sai lầm về Thực tế Code / Convention

- **❌ Sai**: Trả stack trace ra API.
  **✅ Đúng**: Global Middleware → `{code:500, message:"Lỗi hệ thống"}`.
- **❌ Sai**: `.ToList()` không AsNoTracking → Performance kém.
  **✅ Đúng**: `.AsNoTracking().Select(fields needed)`.
- **❌ Sai**: Không transaction cho multi-table update.
  **✅ Đúng**: `BeginTransactionAsync()` + Commit/Rollback.

## 3. EF Core Pitfalls

- Unique constraint: Check `.AnyAsync()` trước Insert.
- N+1 Query: Eager load `.Include()` hoặc projection `Select`.
