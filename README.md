# pr-agent-settings

Organization-level configuration for the [Qodo AI](https://www.qodo.ai/) code review
tool (Qodo Merge, formerly PR-Agent) across the
[`openstack-k8s-operators`](https://github.com/openstack-k8s-operators) GitHub org.

Qodo Merge looks for a repository named `pr-agent-settings` in the organization and
applies the settings defined here as defaults to **every** repository in the org.
Settings can still be overridden per-repository by adding a local `.pr_agent.toml`
file to an individual repo.

## Contents

- [`.pr_agent.toml`](.pr_agent.toml) — the org-wide Qodo Merge configuration. It
  enables `/agentic_describe` and `/agentic_review` on pull requests and tunes the
  review agent's behavior (comment placement and inline-comment severity threshold).
  Its `issues_user_guidelines` carries the openstack-k8s-operators code-review
  conventions (reconciliation, conditions, webhooks, RBAC, testing, etc.).

## Operator-only review guidelines

Because this file applies to **every** repo in the org, the operator-specific review
criteria in `issues_user_guidelines` are **self-gating**: the review agent is instructed
to first detect whether the repo is a kubebuilder/operator-sdk-scaffolded operator
(presence of a `PROJECT` file, `api/*/v*beta*/` types, and controller-runtime
controllers). The operator conventions are applied only when those markers are present;
non-operator repos (docs, tooling, this settings repo) get a normal general-purpose
review. Qodo Merge has no native per-repo-type conditional, so a repo that needs
different behavior can still override everything with its own local `.pr_agent.toml`.

## Documentation

- Qodo AI: https://www.qodo.ai/
- Qodo Merge docs: https://qodo-merge-docs.qodo.ai/
- Configuration options: https://qodo-merge-docs.qodo.ai/usage-guide/configuration_options/
- Organization-level configuration (`pr-agent-settings`):
  https://qodo-merge-docs.qodo.ai/usage-guide/configuration_options/#global-configuration-file
