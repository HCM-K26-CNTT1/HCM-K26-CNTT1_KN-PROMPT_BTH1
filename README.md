# BÀI TẬP: TRÍCH XUẤT VÀ ĐỊNH DẠNG THÔNG TIN TUYỂN DỤNG

## PHẦN 1. XÂY DỰNG PROMPT CREATE

```text
[C - Context]
Bạn là chuyên viên xử lý dữ liệu nhân sự cấp cao.

[R - Request]
Trích xuất: Họ tên, Số điện thoại, Email, Vị trí ứng tuyển, Số năm kinh nghiệm, Kỹ năng chính.

[E - Explanation]
Dữ liệu dùng để nhập vào database tuyển dụng, yêu cầu chính xác, không suy đoán.

[A - Action]
- Đọc email và trích xuất thông tin.
- Chuẩn hóa họ tên, số điện thoại.
- Loại bỏ kỹ năng trùng lặp.
- Thông tin thiếu ghi null.
- Xuất bảng Markdown và JSON.

[T - Tone]
Chính xác, khách quan, ngắn gọn.

[E - Extras: Few-shot]

Ví dụ 1:
Input: "Tôi là NGUYỄN VĂN AN, ứng tuyển Python Developer.
Có 2 năm kinh nghiệm, biết Python, SQL.
SĐT: 0912345678, Email: an@gmail.com"

Output:
{
  "name": "Nguyễn Văn An",
  "phone": "+84912345678",
  "email": "an@gmail.com",
  "position": "Python Developer",
  "experience_years": 2,
  "skills": ["Python", "SQL"]
}

Ví dụ 2:
Input: "Tôi là Trần Thị Bình, ứng tuyển Backend Developer.
Biết Java, SQL, Java. Chưa có kinh nghiệm.
Email: binh@gmail.com"

Output:
{
  "name": "Trần Thị Bình",
  "phone": null,
  "email": "binh@gmail.com",
  "position": "Backend Developer",
  "experience_years": 0,
  "skills": ["Java", "SQL"]
}

Yêu cầu đầu ra:
- Trả về bảng Markdown và mảng JSON.
- JSON đúng cú pháp.
- Không tự thêm thông tin.
- Không viết giải thích ngoài kết quả.
```

## PHẦN 2. KIỂM THỬ PROMPT

Email đầu vào:

"Tôi tên Phạm Minh Khôi, ứng tuyển Software Developer. Có 1 năm kinh nghiệm với Python, Django, Git. SĐT: 0987654321. Email: khoi@gmail.com."

**Bảng Markdown:**

| Trường | Kết quả |
|---|---|
| Họ tên | Phạm Minh Khôi |
| Số điện thoại | +84987654321 |
| Email | khoi@gmail.com |
| Vị trí | Software Developer |
| Kinh nghiệm | 1 năm |
| Kỹ năng | Python, Django, Git |

**JSON đầu ra:**

```json
[
  {
    "name": "Phạm Minh Khôi",
    "phone": "+84987654321",
    "email": "khoi@gmail.com",
    "position": "Software Developer",
    "experience_years": 1,
    "skills": ["Python", "Django", "Git"]
  }
]
```
