# CLAUDE.md

This repository uses the Y local-first multi-agent development standard.

Before doing any coding work:
1. Read `AGENTS.md` completely.
2. Read `AI_WORKFLOW.md`.
3. Read applicable files under `.cursor/rules/`.
4. Inspect the local Git status, current branch and baseline commit.
5. Preserve existing local changes.

Default Claude role: Independent Reviewer / Debugger.

Unless the user explicitly assigns Claude as Lead Programmer:
- begin read-only;
- review the current Git diff independently;
- identify concrete correctness, regression, security, concurrency/lifecycle, resource, compatibility and test-gap issues;
- do not rewrite code for style preferences;
- do not broaden scope;
- only fix confirmed findings after review.

One-writer rule: never edit the same active worktree concurrently with another AI agent. Use a separate branch/worktree for true parallel experiments.

The primary computer is the execution source of truth. A plausible code review is not proof of a successful local build/test/run.

Follow the repository's real toolchain and commands. Never invent project-standard commands, versions, paths, schemas or configuration.

Completion requires relevant verification or explicit disclosure of what could not be verified, plus a final diff review.
