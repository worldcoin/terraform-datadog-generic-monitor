# Copilot review instructions

Before starting any work in this repository, read and follow [`../AGENTS.md`](../AGENTS.md) for repository safety and authoring contracts.

These instructions supplement the organization review policy with repository-specific evidence rules.

## Actionable findings

- Review the current diff and latest commit. Report high-confidence issues grounded in an exact path and line, the concrete failure or misleading behavior, the production or consumer impact, and the smallest sufficient fix or verification.
- Apply the organization severity rubric proportionally to concrete impact. Do not inflate wording, optional cleanup, or a blocked check into an outage-level finding.
- Ground dependency findings in the exact pinned module, provider, runtime, schema, or consumer contract affected by the diff. Do not reason from a newer release, an assumed default, or a neighboring module. Ask a clarifying question when required context is unavailable.
- Avoid speculative abstractions, service-specific recipes for unrelated changes, unrelated cleanup, and broad refactors. Point out unnecessary complexity only when the simpler alternative preserves the requested behavior and safety.

## Validation, dependencies, and pull request evidence

- Verify that claimed commands match the current workflows, configuration, tests, and runbooks, including required inputs, flags, versions, paths, and comparison refs. Confirm evidence covers the affected roots and latest commit; an unrun, blocked, stale, missing, or failed check is not passing evidence.
- Trace changed inputs, outputs, defaults, resource addresses, provider constraints, and module pins through affected consumers. Check companion changes and the stated release, merge, apply, migration, rollback, or cutover order when the changed contract depends on them.
- Confirm code, generated documentation, examples, and the pull request description agree on identifiers, versions, behavior, consumers, compatibility, rollout, and validation.
- Review failures separately from author mistakes. Identify change-caused failures, but describe runner outages, remote-service failures, timeouts, missing credentials, and pre-existing failures as CI or external blockers when the evidence supports that classification. Do not count repeated runs as distinct pull requests.
- When AI created or edited retained code, documentation, commits, pull request text including the title or body, or review replies, verify the applicable AI label when the repository provides it and that the body names each tool and publishes the actual initial user prompt plus material follow-up prompts. A task summary, “AI assisted,” or chat link alone is insufficient.
- Respect explicit redactions of secrets and sensitive personal data. Do not request hidden system/developer instructions, internal reasoning, unavailable private context, or reconstruction of unavailable prompt text.

## Review lifecycle

- Check both inline threads and review summaries. Every Copilot finding needs either a verified fix or an evidence-backed author explanation; do not infer disposition from silence, “outdated” state, or a later approval.
- Re-review the latest material revision. If there are no critical issues, say so and list residual risks or testing gaps without turning them into unsupported findings.
