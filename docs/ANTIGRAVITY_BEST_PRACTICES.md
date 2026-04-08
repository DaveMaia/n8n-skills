# Google Antigravity Optimization Guide (Community-Informed)

This guide adapts `n8n-skills` for effective use in Google Antigravity's agent-first workflow.

## Source Basis

This document is based on:
- Official launch post describing Antigravity's agent-first architecture and artifact-based verification
- Community documentation and operating patterns (task scoping, autonomy ramp-up, artifact review)

> Note: Community guidance can evolve quickly. Re-validate practices periodically.

---

## 1) Task Design for Better Agent Outcomes

Use prompts that are:
- **Specific**: include expected files, constraints, and done criteria
- **Scoped**: one capability area per task (e.g., expression syntax skill only)
- **Verifiable**: require concrete outputs (diff summary + checks)

### Good task template

```text
Objective: Update only `skills/n8n-expression-syntax/*` to improve webhook examples.
Constraints: Do not edit build/versioning files.
Verification: run repo consistency checks and show outputs.
Done when: examples include $json.body pattern and docs remain aligned.
```

---

## 2) Autonomy & Review Policy

For this repository:
- Start with **lower autonomy** for larger edits
- Increase autonomy only after repeated successful, low-risk changes
- Require explicit approval checkpoints for:
  - version bumps
  - packaging/build script changes
  - multi-skill rewrites

---

## 3) Artifact-First Verification

Ask agents to attach artifacts for each non-trivial task:
1. Plan/checklist
2. Changed file list
3. Validation command output
4. (If UI is touched) screenshot/video evidence

For this repo, minimum artifact set is usually:
- changed files
- rationale
- command outputs (`git status`, targeted checks)

---

## 4) Swarm (Parallel Agents) Strategy

Recommended parallelization:
- Agent A: docs updates (`docs/`)
- Agent B: one isolated skill reference file set (`skills/<skill>/...`)

Avoid parallel edits for shared coordination files:
- `README.md`
- `build.sh`
- `dist/README.md`
- same `SKILL.md`

---

## 5) Practical Guardrails for n8n-Skills

- Avoid speculative MCP behavior claims
- Prefer examples grounded in existing repository conventions
- Keep `SKILL.md` concise; move depth into reference files
- Update evaluations when behavior guidance materially changes

---

## 6) Prompt Patterns You Can Reuse in Antigravity

### Pattern A: safe documentation update

```text
Update only docs to improve installation clarity for platform X.
Do not modify skills/evaluations/build scripts.
Provide: changed files + concise rationale + command outputs.
```

### Pattern B: isolated skill enhancement

```text
Improve `skills/n8n-code-javascript/` guidance for return format errors.
Keep activation semantics unchanged.
Add or adjust related evaluation JSONs if behavior guidance changes.
Provide verification commands and outputs.
```

### Pattern C: release preparation

```text
Prepare release notes and distribution docs for next version.
Do not change VERSION until final approval checkpoint.
Cross-check `build.sh`, `dist/README.md`, and root README for consistency.
```
