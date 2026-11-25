# Restricted runtime publisher

This private repository is reserved for a reviewed GitHub Actions caller that
publishes the ElevenID restricted Auth/Flow observation runtime. It is an
organization-owned workflow identity, not a source mirror or an application
deployment.

The repository has a gated manual caller with a default source-free context
probe mode. It has no configured secrets, runner, package grant, or
publication authority; the enable flag is unset. Those must be added only
through the protected central policy's reviewed publisher sequence. The target
package remains private and unlinked to source repositories.

The intended caller will use its repository-scoped `GITHUB_TOKEN` to publish
to the fixed restricted package, avoiding a personal publisher token. The
existing restricted package will receive this repository's only Manage Actions
write grant; `packages: write` is not itself a package-specific token scope.
Any private source reader credential will remain separate and read-only. Keep
the organization GitHub Actions and Packages spending budgets at $0 overage.

## Admission sequence

1. Review and merge a central policy change that explicitly permits this named
   private repository to receive **write**, and only this repository, through
   the restricted package's Manage Actions access. The public publisher and
   consumer repositories retain no package grant.
2. Convert the centrally reviewed publisher to a reusable workflow. Its caller
   must be this repository's manual `main` workflow; the callee must check its
   own `job.workflow_repository`, `job.workflow_ref`, and `job.workflow_sha`,
   and check out the central source at that exact SHA. Recheck the bundle and
   private source closure before any credential-bearing step.
3. Add a minimal caller here with `contents: read`, `packages: write`, and
   explicit mappings for separate read-only private-source and package-metadata
   secrets. The write credential is the job's short-lived `GITHUB_TOKEN`; no
   package-writer personal access token or new personal account is needed.
4. After independent review and passing checks, grant this private repository
   package write access, verify that the package is still private and unlinked,
   first run the source-free callee-context probe mode, then dispatch a source-free
   permission probe before any restricted image.
   Confirm the $0 billing guard and available storage before publication.

The repository's default workflow permission is read, workflow PR approvals
are disabled, and private forking is disabled. GitHub Free does not enforce
branch protection for this private repository; only the two organization
owners currently have write access. The central review must explicitly accept
that boundary before the package grant. This README is not that approval and
does not enable publication.
