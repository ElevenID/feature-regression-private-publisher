# Restricted runtime publisher

This private repository is reserved for a reviewed GitHub Actions caller that
publishes the ElevenID restricted Auth/Flow observation runtime. It is an
organization-owned workflow identity, not a source mirror or an application
deployment.

The repository currently has no workflow, secrets, runner, package grant, or
publication authority. Those must be added only through the protected central
policy's reviewed publisher sequence. The target package remains private and
unlinked to source repositories.

The intended caller will use its repository-scoped `GITHUB_TOKEN` for write
access to exactly the restricted package, avoiding a personal publisher token.
Any private source reader credential will remain separate and read-only. Keep
the organization GitHub Actions and Packages spending budgets at $0 overage.
