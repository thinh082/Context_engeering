### CHỨA CẤU HÌNH THÔNG TIN API

## Ví dụ Endpoint: Login

### URL

`/api/v1/auth/login`

### Method

`POST`

### Headers

- `Content-Type: application/json`

### Request Body Parameters

- `email` (string, bắt buộc): Email người dùng.
- `password` (string, bắt buộc): Mật khẩu tài khoản.

### Request Example

```json
{
  "email": "user@example.com",
  "password": "P@ssw0rd123"
}
```

### Response Success (`200 OK`)

```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refresh_token": "dGhpc19pc19hX3JlZnJlc2hfdG9rZW4...",
    "expires_in": 3600,
    "user": {
      "id": 101,
      "email": "user@example.com",
      "full_name": "Nguyen Van A",
      "role": "user"
    }
  }
}
```

### Response Error (`401 Unauthorized`)

```json
{
  "success": false,
  "message": "Invalid email or password"
}
```

### Response Error (`422 Unprocessable Entity`)

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": {
    "email": ["Email is required"],
    "password": ["Password must be at least 8 characters"]
  }
}
```
