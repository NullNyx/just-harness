# just-harness

[![CI](https://github.com/NullNyx/just-harness/actions/workflows/ci.yml/badge.svg)](https://github.com/NullNyx/just-harness/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Harness riêng, dùng lại được qua nhiều project và agent.

## Mục tiêu

- Giữ task state ngoài prompt
- Ép verify bằng evidence
- Ghi decision và friction để agent sau khỏi lặp lại

## Cấu trúc v0

- `AGENTS.md` - luật nền cho agent trong repo này
- `CONTEXT.md` - từ điển thuật ngữ
- `docs/` - contract của harness
- `state/` - state runtime, không commit
- `scripts/` - gate và helper mỏng

## Nguyên tắc

- Prompt ngắn, state rõ
- Gate trước, tin sau
- Evidence thật mới tính done
- Friction lặp thì biến thành rule
