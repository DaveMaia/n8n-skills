# AGENTS.md

Repository-level operating guide for autonomous coding agents (including Google Antigravity).

## Mission
Maintain and improve this repository of n8n-focused skills while preserving:
1. Accuracy against real n8n/n8n-mcp behavior
2. Reusability across agentic IDEs
3. Testability via evaluation scenarios

## High-priority constraints
1. Never invent MCP tool responses; prefer documented, reproducible behavior.
2. Keep `SKILL.md` concise; move deep detail into focused reference files.
3. Preserve activation quality: each skill description must clearly encode trigger intent.
4. Update or add `evaluations/*` for any meaningful behavioral change.
5. Prefer additive, reversible edits over broad rewrites.

## Antigravity execution model
When running this repo in Google Antigravity:
- Use **small, scoped tasks** (one skill or one doc area at a time).
- Require **artifact-backed verification** for non-trivial changes:
  - task plan
  - changed file list
  - test/check output
- Use **human checkpoint** before destructive actions (mass deletions, large refactors, version bumps).

## Parallelization guidance (swarm-safe)
Safe to run in parallel:
- independent docs edits in `docs/`
- independent skill reference updates in separate skill folders

Avoid parallel edits when touching:
- same `SKILL.md`
- shared root docs (`README.md`, `docs/USAGE.md`, `docs/INSTALLATION.md`)
- build/version files (`build.sh`, `dist/README.md`, `.claude-plugin/*`)

## Definition of done
A task is done only if:
1. Files are internally consistent (README/docs/build metadata aligned)
2. Any changed guidance is reflected in relevant docs
3. Commands used for validation are recorded in the final summary
