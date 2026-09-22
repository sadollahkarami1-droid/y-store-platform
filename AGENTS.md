# AGENTS.md — Universal ChatGPT/Codex Engineering Guardrails

Version: 1.1
Repository: sadollahkarami1-droid/y-store-platform
Default branch: main
Scope: Entire repository tree unless a deeper AGENTS.md or AGENTS.override.md defines more specific rules.

## Prime directive
Make the smallest correct, verifiable change that satisfies the user's request while preserving all unrelated working behavior. Never treat generated code as completion; relevant verification is required.

## Repository / Root Lock
- Treat sadollahkarami1-droid/y-store-platform as the current source of truth while working in it.
- Identify the current branch and baseline commit before non-trivial changes.
- Never silently switch to a similarly named repo, backup, archive, fork, export, generated folder, or stale copy.
- A user-declared official stable commit/hash/version/file is authoritative until explicitly changed.
- Never downgrade newer working files with older copies.
- Verify the active runtime/build/deployment path when duplicate implementations exist.

## Think Before Coding
Before editing, inspect the implementation, callers/imports/routes/schemas/tests/configuration/dependencies; separate facts from assumptions; and define an observable success criterion. Never invent inspectable APIs, versions, paths, symbols, environment variables, schemas, endpoints or credentials.

If ambiguity is reversible and non-destructive, choose the safest interpretation. If it risks data loss, security exposure, destructive migration or broad incompatibility, preserve state and do not perform the destructive part.

## Preserve Existing Functionality
Default: PRESERVE. Do not remove, disable, rename, replace or redesign unrelated working behavior. Before deleting/renaming files, APIs, functions, UI, database fields, dependencies, tests, assets or configuration, search usages and verify necessity. "Cleanup/refactor/modernize" is not permission for unrelated rewriting. Do not rewrite a whole file when a focused patch is sufficient.

## Surgical Changes
Touch the fewest reasonable files and lines. Preserve public interfaces and backward compatibility unless a breaking change is explicit. Keep optional refactors separate. Do not reformat unrelated code. Every changed line must be explainable by the requested goal.

## Recovery Before Risk
Before high-risk changes (database/schema, auth, payments, production config, platform/dependency upgrades, build-system changes, broad refactors, destructive operations, public API removals, secrets), establish a recoverable baseline. Use Git history and, when relevant, data snapshots/backups. Never claim a backup exists unless verified. Never overwrite the only known-good copy with an unverified build.

## Data Safety
Treat persistent data as non-replaceable unless proven otherwise. Prefer additive/backward-compatible migrations; verify forward migration and recovery path; validate constraints; consider mixed old/new deployments. Never destructively modify production data without explicit authorization.

## Security / Secrets
Never commit passwords, API keys, tokens, private keys, production connection strings or secret environment values. Do not weaken authentication, authorization, TLS/certificate validation, permission checks or input validation just to make code/tests pass. Treat external input as untrusted and consider injection, traversal, XSS/CSRF, SSRF, insecure deserialization, leakage and excessive permissions as relevant.

## Dependencies
Before adding a dependency, check existing capabilities, compatibility and maintenance status. Follow existing version/lockfile conventions. Do not upgrade unrelated dependencies during a feature/fix. Never fabricate package names or versions.

## Inspect Before Modify
Read relevant files, references, nearby patterns, tests and configuration before editing. Prefer project-native patterns over introducing a new architecture.

## Simplicity
Choose the simplest correct, readable, testable and maintainable implementation. Avoid speculative abstractions, premature microservices, unnecessary helper layers/state systems and custom infrastructure for solved problems.

## Async / Network / Concurrency
When relevant consider races, cancellation, timeouts, bounded retries, idempotency, duplicate execution, locks, reconnect behavior, cleanup and partial failure. Do not assume external services are reliable.

## UI / UX
Preserve unrelated layout and behavior, accessibility, localization, RTL/LTR and responsive behavior. Check loading/empty/error/disabled/success states where relevant. Do not redesign unrelated screens during a functional fix.

## API Compatibility
Inspect consumers before changing contracts. Prefer additive changes. Preserve error/status semantics and versioning conventions. Do not break an API merely to simplify implementation.

## Testing / Definition of Done
Define success before implementation. Use actual repository manifests/configuration to discover commands; never invent them. Run the narrowest meaningful checks first: static/syntax → targeted unit → targeted integration → affected package/module → type/lint → build/package → smoke/E2E/runtime as relevant. Never weaken tests merely to pass. If verification cannot run, state exactly what remains unverified.

## Diff Review
Before completion inspect the diff for accidental deletions, unrelated formatting, debug/temp code, leaked secrets, unexpected generated files, unnecessary lockfile/dependency drift, unintended API/schema changes and weakened tests.

## Git Discipline
Preserve history; no force-push/history rewrite unless explicitly requested. Keep unrelated changes out. Prefer coherent commits. Retain the pre-change commit for non-trivial work so rollback is clear.

## Performance
Benchmark before optimizing. Identify bottleneck, change the relevant factor, benchmark again and verify correctness. Never trade correctness/data integrity for unmeasured speed.

## Generated / Vendor Files
Do not hand-edit generated artifacts when a canonical source/generator exists. Avoid vendored third-party modifications unless necessary and documented.

## No False Completion
Never say fixed/tested/verified/backed-up/deployed/production-ready/complete unless that action actually occurred or is directly evidenced. Use precise status such as "implemented; runtime not tested" or "build passed; E2E unverified".

## Final Change Report
For non-trivial work report: goal; files changed; behavior changed; behavior deliberately preserved; verification performed/results; remaining risks; rollback note if relevant.

## Stop Conditions
Do not perform destructive actions when root identity is uncertain, the only good copy may be lost, production data may be destroyed, secrets would be exposed, authorization is missing, or migration impact is unknown. Continue safe work that does not depend on the destructive action.

## Mandatory Engineering Loop
UNDERSTAND → INSPECT → DEFINE SUCCESS → PROTECT RECOVERY → MINIMAL CHANGE → STATIC CHECK → TARGETED TEST → BUILD/RUN WHEN RELEVANT → REVIEW DIFF → VERIFY → REPORT

## Master Rule
When speed conflicts with correctness, elegance with compatibility, cleanup with preservation, or assumption with verification, choose CORRECTNESS → COMPATIBILITY → PRESERVATION → VERIFICATION. Make the smallest verified change that solves the actual problem.

## Shared Y Design System

Central UI source of truth: `sadollahkarami1-droid/y_design_system`.

Rules for any new or changed reusable UI:

- Inspect the central Y Design System before creating a new reusable component.
- Identify the actual application stack first. Do not assume every Y project is Flutter.
- Flutter consumers should use the Flutter Core after a verified release exists.
- React/Web consumers should use the Web Core after a verified private distribution path exists.
- Rust, .NET, Python, native desktop, and other stacks should map the canonical tokens/patterns through a stack-appropriate adapter; never import an incompatible UI runtime.
- Preserve product-specific business logic, state management, authentication, routing, permissions, payments, networking, persistence, and domain data in the consuming repository.
- Do not copy/fork a shared component into this repository by default.
- If a temporary local bridge is unavoidable, document the upstream repository + exact commit, keep the bridge minimal, and include a removal/synchronization plan.
- Preserve localization, RTL/LTR, accessibility, responsive behavior, loading/error/disabled/success states, and existing callbacks.
- Production consumers must pin a verified immutable release/version. Do not track `main` or a feature branch.
- Until the central package is actually verified and released, only prepare reversible integration branches/adapters; do not claim the design-system rollout is complete.

