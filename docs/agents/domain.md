# Tài liệu miền

Harness docs phục vụ Codex khi làm việc trong repo đã cài harness.

## Thứ tự nguồn

1. `CONTEXT.md` - thuật ngữ chuẩn.
2. `AGENTS.md` - luật nền repo.
3. `docs/HARNESS.md` - mental model và task loop.
4. `docs/CONTEXT_RULES.md` - thứ tự đọc context.
5. `docs/FEATURE_INTAKE.md` - phân loại work.
6. `docs/workflow-skills.md` - map phase sang skill / lệnh.
7. `docs/decisions/` - tradeoff đã chốt.

## Layout

- Single-context: root `CONTEXT.md` plus `docs/decisions/`.
- No `CONTEXT-MAP.md` in v0.

## Quy tắc

- Dùng đúng thuật ngữ đã chốt trong repo.
- Nếu thiếu thuật ngữ, thêm vào `CONTEXT.md` trước khi biến thành rule thường trực.
- Nếu có xung đột giữa docs và implementation, báo rõ thay vì tự sửa nghĩa.
