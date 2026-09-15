# Terraform agent instructions

## Scope and safety

- Follow existing module layout, naming, documentation, tests, and nearby patterns. Prefer existing repository or approved `worldcoin/*` modules before adding new resources, modules, providers, or abstractions.
- Local agent work may format, initialize without a backend, validate, test, lint, plan, and inspect state read-only when the repository permits it. Never run or suggest `terraform apply`, `terraform destroy`, `terraform import`, manual state edits, or other mutating state commands. Production changes run only through the approved remote workflow.
- Never hardcode secrets, tokens, passwords, or private keys. Preserve least privilege and existing secret-management patterns.
- Do not upgrade providers broadly, rename or move resources, or change Terraform addresses unless the request requires it. Identify migration and rollback needs without performing manual state operations.
- Preserve repository-specific authoring rules in `CONTRIBUTING.md`, current workflows, configuration, and runbooks. Generated files must be updated through their documented generator rather than hand-edited.

## Pull request preflight and evidence

- Determine the affected module roots from the diff against the pull request base. Search this repository and known consumers for changed inputs, outputs, resource addresses, defaults, provider constraints, and module pins. Record any required release, consumer update, apply, migration, rollback, or cutover order.
- Before opening a pull request, run the smallest useful local validation for the affected roots and consumers. Follow the current workflows, test files, configuration, and runbooks for the applicable commands, tool versions, required inputs, and comparison refs; do not copy a validator recipe from an unrelated module.
- Before committing, run `git diff --check` and `git diff --cached --check` as applicable. After committing, run `git diff --check <base>...HEAD` against the pull request base so committed changes are included.
- For Terraform changes, check formatting, initialize only affected roots when dependencies are available, preserve lock selections unless an upgrade is requested, and run the tests, validation, lint, documentation, and policy checks that current repository automation makes applicable.
- Never describe an unrun, blocked, stale, or failed check as passing. In `Tested (yes/no)`, name each command, its scope, result, and the commit SHA it validates. Re-run affected checks after the last material change so the evidence applies to the latest commit.
- Before requesting review, inspect the final diff and reconcile code, generated documentation, examples, release notes, and the pull request description. Confirm identifiers, versions, defaults, affected consumers, compatibility, rollout order, and rollback claims agree.
- Treat CI defects separately from authoring defects. Fix failures caused by the change. Report remote outages, runner failures, timeouts, unavailable credentials, and pre-existing failures with links and scope; repeated runs of unchanged code do not turn an external failure into author validation evidence.

## Review feedback

- Give every Copilot finding a recorded disposition, including inline comments and findings that appear only in a review summary. Apply the smallest correct fix and re-run affected checks, or reply with an evidence-backed explanation grounded in the current diff, exact dependency contract, test output, or authoritative documentation.
- Do not silently ignore repeated, outdated, or low-severity findings. Link duplicates to the existing disposition. Resolve a thread only after the disposition is recorded and justified, when permissions allow.
- After material fixes, inspect all review threads and summaries again and request Copilot re-review. Report any remaining finding or required failed/pending check as a blocker; do not infer resolution from silence or a bot approval.

## Pull request authoring and AI disclosure

- Use Conventional Commits. Preserve the exact headings in `.github/PULL_REQUEST_TEMPLATE.md` when it exists. When using `gh`, submit multiline bodies with `--body-file`; with an API or connector, use its structured body field.
- `Requestor/Issue` must link the ticket when one exists, or name the requestor and state that no ticket was provided. `Tested (yes/no)` must contain concrete evidence rather than a bare yes or no. `Description/Why` must explain the operational or business reason and affected scope.
- When AI materially creates or edits code, documentation, commits, the pull request body, or review replies, add the `ai-generated` label when the repository provides it and fill `AI usage/prompt(s) (if applicable)`.
- Publish the AI tool name, the actual initial user prompt, and every material follow-up prompt that changed scope, constraints, behavior, validation, or retained text. A summary, “AI assisted,” or a chat link alone is insufficient. Keep prompts in order and update the body after material follow-ups.
- Redact secrets and sensitive personal data with explicit placeholders while preserving the useful surrounding prompt. Do not publish hidden system/developer instructions or internal reasoning. If exact prompt text is unavailable, disclose that gap instead of reconstructing it as a quote.
