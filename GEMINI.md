# GEMINI.md

Antigravity-native instructions for working in `n8n-skills`.

## Project context
- This repository ships reusable skills that guide AI agents building n8n workflows via n8n-mcp.
- Primary quality signal is whether guidance prevents common workflow/configuration errors.

## Preferred workflow in Antigravity
1. **Plan first**: produce a short implementation checklist before editing.
2. **Edit narrowly**: touch the minimum files needed for the task.
3. **Verify**: run lightweight checks (format, grep, consistency checks).
4. **Summarize with artifacts**: changed files + command outputs.

## Quality guardrails
- Do not add speculative product claims without source links.
- Keep examples realistic and reproducible.
- Keep language actionable and concise.
- If changing install/packaging instructions, cross-check `build.sh` and `dist/README.md`.

## Repo conventions
- `skills/<name>/SKILL.md`: core instructions and activation behavior
- `skills/<name>/*.md`: deep references and examples
- `evaluations/<domain>/*.json`: behavior test scenarios
- `docs/*.md`: platform and contributor documentation

## Shipping checklist
- [ ] Root docs still accurate (`README.md`, `docs/USAGE.md`, `docs/INSTALLATION.md` when relevant)
- [ ] Packaging docs aligned with `build.sh`
- [ ] No unrelated files modified
