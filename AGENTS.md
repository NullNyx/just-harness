# Hướng dẫn Agent

Agent chính do repo cài đặt sử dụng.

## Kỹ năng agent

### Issue tracker

Issues sống trong GitHub Issues của repo này. Xem `docs/agents/issue-tracker.md`.

### Triage labels

Dùng 5 nhãn triage canonical trong `docs/agents/triage-labels.md`.

### Domain docs

Layout single-context: root `CONTEXT.md` cộng `docs/decisions/`. Xem `docs/agents/domain.md`.

### Bộ skill Matt Pocock

Dùng `ask-matt` như router để chọn flow phù hợp khi task còn mơ hồ.
Chạy `/setup-matt-pocock-skills` một lần để seed issue tracker, triage labels,
và layout docs mà các skill engineering khác phụ thuộc.
Xem `docs/workflow-skills.md` để biết map từng phase sang skill.

## Mục tiêu

Xây harness dùng lại cho nhiều project.

## Luật nền

1. Đọc `README.md` và `docs/HARNESS.md` trước khi làm việc lớn.
2. Dùng `docs/FEATURE_INTAKE.md` để phân loại task.
3. Dùng `docs/CONTEXT_RULES.md` để biết phải đọc gì trước.
4. Dùng `docs/TEST_MATRIX.md` để biết proof cần chạy gì.
5. Dùng `docs/workflow-skills.md` để map phase sang skill hoặc lệnh.
6. Mỗi task dài dùng `/goal`.
7. Task mơ hồ dùng `/plan` trước, nếu agent hỗ trợ.
8. Mỗi task phải có evidence thật, không tin lời model.

## Quy ước

- `state/` chỉ cho runtime state.
- `docs/` chỉ cho contract, guide, decision, template, profile.
- `scripts/` chỉ cho helper/gate dùng lại được.
- Không commit file state runtime.

