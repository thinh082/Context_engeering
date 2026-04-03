### MÔ TẢ CẤU TRÚC DỰ ÁN Ở ĐÂY

# Kiến trúc Dự án

## Công nghệ sử dụng (Tech Stack)

- Framework: .NET 8 (ASP.NET Core Web API)
- ORM: Entity Framework Core
- Database: SQL Server / PostgreSQL
- Các công cụ khác: MediatR, AutoMapper, FluentValidation, xUnit

```
Project/
├── Controllers/      ← Chỉ routing + gọi Service
├── Services/         ← Logic nghiệp vụ + Interface cùng file
│   └── CommonServices.cs
├── Models/           ← ⚠️ KHÔNG tự ý sửa (Entities/DB schema)
├── Views/            ← Nếu có Razor Views
├── PDFDocument/      ← Template/luồng xuất PDF
├── Middleware.cs     ← ⚠️ Cẩn thận khi sửa (global HTTP pipeline)
└── Program.cs        ← ⚠️ Cẩn thận khi sửa (cấu hình global)
```

> Các file đánh dấu ⚠️ là **global**, mọi thay đổi phải báo và giải thích rõ với người dùng trước.
