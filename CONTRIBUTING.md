# Đóng góp

Cảm ơn bạn quan tâm tới just-harness.

## Luồng

1. Mở issue (bug report hoặc feature request) — dùng template có sẵn.
2. Fork, tạo branch, commit, push.
3. Mở PR kèm description theo template.
4. CI phải xanh.

## Code style

- Script: thêm `set -euo pipefail`.
- Docs: tiếng Việt. Giữ tên lệnh / path / canonical terms bằng EN.
- Evidence bắt buộc cho mọi thay đổi có thể verify.

## Scope

Harness giữ gate + evidence + note + profile. Không nhồi skill vào shell script.
Skill là agent construct (prompt). Đề xuất skill mới → docs, không phải script.
