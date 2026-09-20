# Y Local AI Programming Workflow

Official flow:

Primary computer → Cursor → ChatGPT/Codex (Lead) → Git diff → Claude (independent review) → targeted fixes → local tests/build/runtime verification → final diff review → Git commit → GitHub.

Only one AI edits the active worktree at a time.

At task start: read AGENTS.md and .cursor/rules; confirm repo/branch; inspect git status; preserve local changes; record baseline commit for non-trivial work; inspect relevant code/tests/config; define measurable success.

Lead handoff to reviewer: goal, baseline commit, changed files, short implementation summary, current Git diff, checks already run/results, known unknowns/failures.

Reviewer checks functional correctness, regressions, concurrency/lifecycle, resource leaks, API/data compatibility, security/privacy, error handling, platform compatibility, missing negative/boundary tests and unnecessary scope expansion. Style preference alone is not a defect.

Fix only confirmed issues and re-run affected checks. Do not start unrelated refactors during the fix cycle.

Verification ladder: static/syntax → targeted unit → targeted integration → affected module/package → lint/type analysis → build/package → smoke/E2E/runtime. Use repository-native commands. Skipped relevant stages must be disclosed.

The primary computer establishes execution truth. A cloud AI saying code looks correct is not equivalent to a successful local build/test/run.

Definition of done: requested behavior exists; relevant local verification passed or remaining gaps are documented; final diff reviewed; no unresolved blocker; repository remains recoverable.
