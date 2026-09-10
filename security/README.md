# Project security improvement guide

Use this guide to turn a shared security practice into a project-specific work
item. It consolidates the reference issues below; it does not certify a project's
security or introduce a new foundation policy.

For vulnerabilities, use the affected project's private reporting channel.
This guide and the public issue form are for improvement work.

## Start a project task

Check the [security work board](https://github.com/orgs/uxlfoundation/projects/3?pane=info)
and existing issues before opening a
[security improvement work item](https://github.com/uxlfoundation/open-source-working-group/issues/new?template=security-work-item.yml).
Name the repository, current state, proposed change, agreed owner and completion
evidence. Scope work to the project's languages, dependencies and release process.
Record an applicability decision where a tool does not fit.

## Onboarding

Nominate at least one security representative. Coordinate with
[security@uxlfoundation.org](mailto:security@uxlfoundation.org) to confirm the
private representative list, relevant
[GitHub security team](https://github.com/orgs/uxlfoundation/teams/security),
mailing list and private Slack access. These are the routes recorded in the
original reference; administrators must confirm access.

Watch the [2024 security strategy overview](https://www.youtube.com/watch?v=ImaggrWdEH4)
for background, then agree project tasks from the security board.

Completion evidence: confirmed representative and access, plus scoped project
tasks. Keep private rosters and access details in restricted locations.

## GitHub tokens

Inventory automation credentials and required permissions. In Actions, use
[GITHUB_TOKEN with minimum permissions](https://docs.github.com/en/actions/tutorials/authenticate-with-github_token)
where sufficient. Evaluate a GitHub App or suitably restricted personal token
when additional access is needed. The original reference preferred fine-grained
personal tokens and requested security-team review of classic-token exceptions;
retain that review route through security@uxlfoundation.org.

Completion evidence: reviewed credential types, permissions and exception
rationale, with configuration changes linked. Never include token values.

## Secret scanning

Review [secret-scanning coverage](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning)
and alert handling. Public repositories receive automatic scanning; the old
instruction to enable a setting does not establish that alerts are handled.

Completion evidence: confirmed coverage and an alert-response owner. Keep secret
values and alert details out of public tasks.

## Dependency updates

Review Dependabot alerts, security updates and grouped security updates, the
three settings recommended in the original reference. Tune grouping to the
project's review and testing capacity using
[GitHub's guidance](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/configure-security-updates).

Completion evidence: documented settings, covered manifests and a review/test
process for update PRs. Record dependency coverage gaps separately.

## Vulnerability policy

Publish SECURITY.md with supported versions and private reporting routes. The
[oneDNN policy](https://github.com/uxlfoundation/oneDNN/blob/main/SECURITY.md)
is an example; choose support commitments the project can meet. Confirm private
vulnerability reporting and who receives reports.

Completion evidence: a published policy and confirmed reporting configuration.

## CodeQL

The original task targeted non-C/C++ code, such as Python. Inventory applicable
languages and use the [CodeQL setup guidance](https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/configure-code-scanning/configure-code-scanning)
to choose a suitable configuration. Review existing setup before replacing it.

Completion evidence: successful analysis, recorded language coverage and an
alert-triage owner. An enabled setting alone does not establish successful scans.

## Coverity

Evaluate [Coverity Scan](https://scan.coverity.com/) for C/C++ static analysis,
as recommended in the original reference. If appropriate, register the project,
restrict access to scan results, configure the build tool and integrate scanning
with the build workflow. Review third-party actions before adoption; the original
issue links an unofficial integration as background.

Completion evidence: an evaluation decision and, if adopted, a successful scan,
covered build configuration and restricted-results access process.

## CVE-Bin-Tool and dependency inventory

Evaluate [CVE-Bin-Tool](https://github.com/ossf/cve-bin-tool) for C/C++ dependency
inventory and known-vulnerability matching, including projects that do not ship
binaries. It supports binaries or known component/version information, including
an SBOM. Record actual coverage gaps instead of assuming one tool finds every
dependency.

Completion evidence: representative input, results, limitations and a decision
on continued use. Handle sensitive findings through private channels.

## OpenSSF Scorecard

Review [Scorecard results and badge guidance](https://github.com/ossf/scorecard).
Link the badge to the correct repository and track actionable findings. The
original reference recommended a score of at least 7; this remains a recorded
recommendation, not a newly enforced release gate or security guarantee.

Completion evidence: a dated report, correct badge/link where adopted, and tasks
for remaining findings. A badge alone does not complete remediation.

## Fuzzing

Evaluate useful fuzz targets and [OSS-Fuzz](https://github.com/google/oss-fuzz),
the original reference's recommended option. That issue also links the Scorecard
criteria used at the time. Choose a suitable integration and document the decision
if fuzzing is not applicable.

Completion evidence: target scope, reproducible build/run instructions and a
working integration with a findings owner, or an applicability decision.

## Original references

These issues preserve the source instructions and historical links. They are
reference material, not evidence of completed project work.

| Topic | Original issue |
| --- | --- |
| Onboarding | [#199](https://github.com/uxlfoundation/open-source-working-group/issues/199) |
| GitHub tokens | [#198](https://github.com/uxlfoundation/open-source-working-group/issues/198) |
| Secret scanning | [#197](https://github.com/uxlfoundation/open-source-working-group/issues/197) |
| Dependency updates | [#196](https://github.com/uxlfoundation/open-source-working-group/issues/196) |
| Vulnerability policy | [#195](https://github.com/uxlfoundation/open-source-working-group/issues/195) |
| CodeQL | [#194](https://github.com/uxlfoundation/open-source-working-group/issues/194) |
| Coverity | [#193](https://github.com/uxlfoundation/open-source-working-group/issues/193) |
| CVE-Bin-Tool | [#192](https://github.com/uxlfoundation/open-source-working-group/issues/192) |
| Scorecard | [#191](https://github.com/uxlfoundation/open-source-working-group/issues/191) |
| Fuzzing | [#190](https://github.com/uxlfoundation/open-source-working-group/issues/190) |

[Working Group home](../README.rst) · [Contributing](../CONTRIBUTING.md)
