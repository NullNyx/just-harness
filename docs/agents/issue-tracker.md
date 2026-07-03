# Bộ theo dõi issue

GitHub Issues là issue tracker mặc định cho repo này.
Dùng `gh` CLI cho mọi thao tác.

## Cách dùng

- **Tạo issue**: `gh issue create --title "..." --body "..."`. Heredoc cho body nhiều dòng.
- **Đọc issue**: `gh issue view <số> --comments`, lọc labels bằng jq.
- **Danh sách**: `gh issue list --state open --json number,title,body,labels,comments --jq '...'` kèm `--label` / `--state` cần thiết.
- **Comment**: `gh issue comment <số> --body "..."`
- **Gắn / bỏ label**: `gh issue edit <số> --add-label "..."` / `--remove-label "..."`
- **Đóng**: `gh issue close <số> --comment "..."`

Infer repo từ `git remote -v`. `gh` tự động nhận khi chạy trong clone.

## PR như request surface

**PR không phải request surface mặc định.** (set `yes` nếu repo nhận feature request qua PR.)

Khi set yes, PR chạy cùng label + state như issue, dùng lệnh `gh pr`:

- **Đọc PR**: `gh pr view <số> --comments` và `gh pr diff <số>` cho diff.
- **List external PR**: `gh pr list --state open --json number,title,body,labels,author,authorAssociation,comments` rồi lọc `authorAssociation` là `CONTRIBUTOR`, `FIRST_TIME_CONTRIBUTOR`, hoặc `NONE` (bỏ `OWNER`/`MEMBER`/`COLLABORATOR`).
- **Comment / label / close**: `gh pr comment`, `gh pr edit --add-label`/`--remove-label`, `gh pr close`.

GitHub chung không gian số cho issue và PR. `#42` có thể là cả hai — phân biệt bằng `gh pr view 42` fallback `gh issue view 42`.

## Khi skill nói "publish to tracker"

Tạo GitHub issue.

## Khi skill nói "fetch ticket"

Chạy `gh issue view <số> --comments`.

## Wayfinder

Dùng bởi skill wayfinder (nếu có).

- **Map**: một issue label `wayfinder:map`, chứa Notes / Decisions-so-far / Fog body. `gh issue create --label wayfinder:map`.
- **Child ticket**: sub-issue của map (dùng API sub-issues). Nếu chưa bật, thêm task list trong body map + ghi `Part of #<map>` đầu body child. Label: `wayfinder:<type>` (`research`/`prototype`/`grilling`/`task`), thêm `wayfinder:claimed` khi ai đó nhận.
- **Blocking**: native issue relationship hoặc dòng `Blocked by: #<n>` đầu body child. Ticket unblocked khi mọi issue nó liệt kê đều closed.
- **Frontier query**: list open children của map, bỏ ticket có `Blocked by` đang mở hoặc label `wayfinder:claimed`; ticket đầu tiên hợp lệ.
- **Claim**: `gh issue edit <n> --add-label wayfinder:claimed`.
- **Resolve**: `gh issue comment <n> --body "<answer>"`, close, rồi thêm context pointer vào Decisions-so-far của map.
