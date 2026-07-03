# just-harness

[![CI](https://github.com/NullNyx/just-harness/actions/workflows/ci.yml/badge.svg)](https://github.com/NullNyx/just-harness/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

just-harness là lớp vận hành cho Codex agent trên mỗi project code.
Nó quản lý task state, kiểm tra scope, ghi evidence, và duy trì project truth
qua nhiều phiên làm việc — thay vì dựa vào prompt context thuần tuý.

## Tại sao harness

Mỗi lần gọi agent là một phiên trắng. Agent không nhớ slice nào đang làm,
lần trước fail vì gì, file nào đã sửa, test nào pass.

Harness giải quyết bằng state machine trên shell script + file JSON:

- Task state sống trên disk, không phải trong prompt
- Gate runner kiểm tra scope trước khi cho phép code chạm file ngoài phạm vi
- Evidence recorder buộc mọi kết luận phải kèm output thật (test log, lint result, build artifact)
- Note system giữ project truth thay đổi nhanh (scope drift, friction, dev-setup)

## Cài đặt

Trong repo đích:

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/NullNyx/just-harness/main/scripts/install-harness.sh) --merge --yes
```

Hoặc clone về rồi chạy:

```bash
git clone git@github.com:NullNyx/just-harness.git /tmp/just-harness
cd /target/repo
bash /tmp/just-harness/scripts/install-harness.sh --merge --yes
```

Sau cài đặt, chạy `setup-matt-pocock-skills` một lần để cấu hình issue tracker,
triage labels, và domain docs layout (xem `docs/matt-pocock-skills.md`).

## Architecture overview

```
intent → intake → profile → context → implement → agent gate → CI gate → record → next task
```

Mỗi vòng lặp task tạo hai output:

1. **Product delta**: code, config, docs, test
2. **Harness delta**: rule mới, template, evidence, decision, friction ghi nhận

### Layer

| Layer | Nội dung | Sống ở |
|-------|----------|--------|
| Harness core | gate runner, scope check, evidence recorder, note system | `scripts/`, `state/` |
| Workflow config | task lanes, profile, context rules, test matrix, skill mapping | `docs/` |
| Agent conduit | rules + skill triggers cho Codex | `AGENTS.md` |
| Glossary + decisions | thuật ngữ chuẩn, ADR | `CONTEXT.md`, `docs/decisions/` |
| Notes | project truth thay đổi nhanh, friction, scope drift | `docs/notes/` |

## Quick start

```bash
# 1. Phân loại task
→ docs/FEATURE_INTAKE.md

# 2. Chạy scope check
scripts/run-gate.sh --profile backend --allowlist docs/templates/slice-allowlist.json

# 3. Ghi evidence sau mỗi lệnh
scripts/record-evidence.sh "unit test" pytest -x

# 4. Ghi note nếu truth thay đổi
scripts/record-note.sh scope-drift backend "Job openings model expanded"
```

Xem `docs/workflow-skills.md` để map phase sang skill cụ thể.

## Nguyên tắc

- Gate trước, tin sau — scope check chạy trước khi build/test
- Evidence thật mới tính done — output từ lệnh, không phải lời model
- CI gate thắng agent gate — build/log CI là truth cuối
- Friction lặp → thành rule — sửa harness trước, code sau

## Tài liệu

| File | Mục đích |
|------|---------|
| `docs/HARNESS.md` | Thiết kế và mô hình tư duy |
| `docs/FEATURE_INTAKE.md` | Phân loại task theo lane/type |
| `docs/CONTEXT_RULES.md` | Thứ tự đọc context |
| `docs/TEST_MATRIX.md` | Proof requirements per area |
| `docs/workflow-skills.md` | Phase → skill mapping |
| `docs/matt-pocock-skills.md` | Tích hợp Skills For Real Engineers |
| `docs/release-process.md` | Quy trình release |

## Giấy phép

MIT — xem [LICENSE](LICENSE).

## Đóng góp

Xem [CONTRIBUTING.md](CONTRIBUTING.md). Bug/feature → issue templates có sẵn.
