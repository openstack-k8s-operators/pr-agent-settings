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

## Documentation

- Qodo AI: https://www.qodo.ai/
- Qodo Merge docs: https://qodo-merge-docs.qodo.ai/
- Configuration options: https://qodo-merge-docs.qodo.ai/usage-guide/configuration_options/
- Organization-level configuration (`pr-agent-settings`):
  https://qodo-merge-docs.qodo.ai/usage-guide/configuration_options/#global-configuration-file
