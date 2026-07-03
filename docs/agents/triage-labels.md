# Nhãn triage

Năm vai trò triage canonical. Cột bên phải là label thật trong issue tracker — sửa nếu tracker dùng tên khác.

| Vai trò | Label | Ý nghĩa |
|---------|-------|---------|
| `needs-triage` | `needs-triage` | Cần maintainer đánh giá |
| `needs-info` | `needs-info` | Đợi reporter cung cấp thêm thông tin |
| `ready-for-agent` | `ready-for-agent` | Đã spec đủ, agent có thể làm |
| `ready-for-human` | `ready-for-human` | Cần human thực hiện |
| `wontfix` | `wontfix` | Sẽ không xử lý |

Khi skill nói "áp label triage", dùng label từ cột Label của bảng trên.

## Nguyên tắc

- label ngắn và ổn định
- một issue có thể mang nhiều label
- label định tuyến work, không thay acceptance criteria
