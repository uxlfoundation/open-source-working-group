# Configuring and deploying public project CI

Use this guide to establish reproducible public build and test workflows. It
provides recommendations for project maintainers, not a new foundation policy
or a promise of shared hardware. The [CI inventory](project-ci-documentation.md)
records requirements and dated execution evidence.

## 1. Define what the workflow must prove

Choose one initial build/test target and record its operating system, processor,
compiler, dependencies and test command. Distinguish compiling the library,
running functional tests, measuring performance and publishing a release.
Documentation builds and static analysis do not establish functional coverage.

Put reproducible setup, build and test commands in the project repository so
contributors can run them locally. Record dependency versions and the source
revision. For hardware-specific tests, identify the actual device and driver;
a runner label or emulated target alone is not proof of physical device coverage.

## 2. Choose the execution environment

Prefer GitHub-hosted runners when they meet the target's needs. For specialized
hardware, first establish an owner, permitted repositories, access route,
isolation model and update process. Do not reuse an old capacity catalogue as
evidence that a machine is available.

GitHub recommends avoiding self-hosted runners for public repositories because
pull requests can execute untrusted code. Review its
[runner access guidance](https://docs.github.com/en/actions/how-tos/manage-runners/self-hosted-runners/manage-access)
before choosing that design. If specialized hardware requires self-hosting,
document how untrusted changes are isolated from credentials, other jobs and
internal networks. A container or manual approval alone does not establish that
isolation.

For autoscaling, use clean, single-job environments and retain runner diagnostics
outside the disposable machine. Plan how the machine is reset or replaced after
each job; deregistration alone does not wipe it. See GitHub's
[ephemeral runner guidance](https://docs.github.com/en/actions/reference/runners/self-hosted-runners).

## 3. Configure a small, reviewable workflow

Use the [CI tool review](../security/ci-tool-review.md) to select checks for
specific quality or security gaps without duplicating existing integrations.

Start with one target before expanding the matrix. Use a pull-request trigger
for contributor validation and an appropriate main-branch or scheduled trigger
for integration checks. Keep publishing credentials out of contributor testing.

Set explicit minimum token permissions, pin third-party actions to verified
full commit hashes, and avoid placing untrusted PR titles or other event text
directly into shell commands. Do not combine privileged `pull_request_target`
execution with checkout and execution of untrusted contributor code. Review
[GitHub's secure-use guidance](https://docs.github.com/en/actions/reference/security/secure-use)
when configuring these boundaries.

Use stable job names, bounded timeouts and cancellation of obsolete runs where
appropriate. Make build or test failures fail the check. Document intentional
path/domain filters so a skipped job cannot be mistaken for tested coverage.

## 4. Validate before relying on the check

Run a known-good revision and inspect individual build/test steps. Then use a
temporary test change that should fail and verify that the check reports failure.
Exercise the contributor/fork path using harmless test changes in the intended
isolated environment. Confirm that logs identify the tested revision and target.

Check cancellation, unavailable-runner behavior and any conditional skips. If a
check will become required, first confirm its name and triggering behavior match
the intended contribution paths; an absent check can leave a PR waiting forever.

For examples of real execution, use the
[verified workflow evidence](project-ci-documentation.md#public-workflow-evidence).
Those examples are evidence for their stated targets, not templates guaranteeing
the same coverage in another project.

## 5. Publish the result and hand it over

Add the workflow and local reproduction instructions through the project's normal
review process. Record the following in its CI documentation and update the shared
inventory with a verification date and evidence link:

| Record | What to include |
| --- | --- |
| Coverage | Build/test targets, hardware, software versions and known gaps |
| Entry points | Workflow, triggers, required-check names and local commands |
| Evidence | Successful run and deliberate-failure validation on the tested revision |
| Operations | Agreed primary/backup contact, access route and update responsibility |
| Resources | Shared or dedicated capacity, limits and unavailable-runner behavior |
| Recovery | How to stop dispatch, replace an unhealthy runner and restore service |

Report private operational details through the project's restricted channels.
Public documentation should still explain how contributors obtain help and
interpret failures.

## 6. Keep the setup useful

Review failures and queue delays, update images and dependencies, and revalidate
after changes to drivers, compilers or hardware. Give infrastructure outages a
clear explanation so contributors can distinguish them from code regressions.
If a runner is retired, update its workflow and inventory entry together.

If publishing artifacts is added later, document it as a separate process with
its own permissions and verification. Public test infrastructure does not by
itself establish release provenance or release readiness.

[CI inventory](project-ci-documentation.md) · [Security guide](../security/README.md)
· [Working Group home](../README.rst)
