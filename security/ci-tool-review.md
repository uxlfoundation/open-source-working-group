# CI security and quality tool review

Reviewed September 10, 2026 for
[#121](https://github.com/uxlfoundation/open-source-working-group/issues/121).
This is a documentation and configuration review, not a comparative benchmark
or an organization-wide tool mandate. Project maintainers should validate their
selected tools against representative code before adopting new gates.

## Findings and recommendations

| Need | Candidate and observed usage | Recommendation and limits |
| --- | --- | --- |
| Formatting | [clang-format](https://clang.llvm.org/docs/ClangFormat.html); oneDPL has a changed-file formatting check that produces a diff and fails when changes are needed. | Keep the version and project style consistent locally and in CI. Give contributors the diff. Formatting does not detect semantic defects. |
| C++ linting | [clang-tidy](https://clang.llvm.org/extra/clang-tidy/); compiler-aware checks complement formatting. | Use the project's compilation database and a focused check set. Measure noise and runtime before expanding coverage or requiring the check. No new tool trial was run in this review. |
| Test coverage | [gcovr](https://gcovr.com/en/stable/guide.html) is a candidate for collecting and reporting supported native-code coverage. | Trial an instrumented build on a representative target; record source filters and line/branch metrics. No UXL-wide deployment was established here. CPU coverage does not establish GPU kernel coverage or test quality. |
| Static security analysis | oneTBB configures Python and C++ CodeQL. Its [April 3 run](https://github.com/uxlfoundation/oneTBB/actions/runs/23937499123) completed both analyses. | Select supported languages explicitly and verify the analysis step. The Construction Kit's current CodeQL configuration covers C/C++ only; it does not satisfy its separate non-C/C++ task. |
| Automated reporting | GitHub check results, diagnostic artifacts and [SARIF uploads](https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/integrate-with-existing-tools/upload-sarif-file) provide complementary outputs. | Use check status for pass/fail, artifacts for reproducible diagnostics, and SARIF for compatible code-scanning findings. Verify revision attribution, reporting permissions and artifact retention. A successful upload is not proof of remediation. |
| Runner hardening | oneTBB's CI configuration includes [Harden-Runner](https://github.com/step-security/harden-runner). | Evaluate its capabilities in the selected environment. Configuration presence is not evidence that egress is blocked. Combine monitoring with minimal permissions and isolation; an action cannot make an unsafe self-hosted execution model safe by itself. |
| Secret detection | GitHub [secret scanning](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) provides repository scanning and alerts. | Verify applicable coverage and alert ownership, and handle exposed credentials through private remediation. Tool enablement alone does not establish that alerts are being resolved. |

## What was inspected

- [oneDPL CI testing](https://github.com/uxlfoundation/oneDPL/blob/main/.github/workflows/ci-testing.yml): formatting diff generation, failure behavior and artifact configuration.
- [oneTBB CI](https://github.com/uxlfoundation/oneTBB/blob/master/.github/workflows/ci.yml): formatting jobs and Harden-Runner references.
- [oneTBB CodeQL](https://github.com/uxlfoundation/oneTBB/blob/master/.github/workflows/codeql.yml): Python/C++ matrix, permissions and successful analysis evidence.
- [Construction Kit CodeQL](https://github.com/uxlfoundation/oneapi-construction-kit/blob/main/.github/workflows/codeql.yml): C/C++ language configuration.

These are dated observations of selected workflows, not a complete security
assessment. Current upstream documentation is linked in the comparison above.

## Applying the review

Start with an actual gap in the project. Record the current baseline, proposed
tool/configuration, coverage, execution cost and agreed maintainer. Test a known
success and a controlled failure; check that results reach the intended reviewer
without exposing private data. Record skips and unsupported targets explicitly.

Prefer improving an existing working integration over adding a duplicate scanner.
For a new check, trial it before deciding whether it should block merges. Document
how contributors reproduce findings and how false positives are handled.

The [public CI guide](../project-infrastructure/public-ci-guide.md) covers workflow
trust boundaries, deployment and handover. The [security improvement guide](README.md)
covers dependency updates, vulnerability policy, Coverity, CVE-Bin-Tool, Scorecard
and fuzzing. This review does not complete those project-specific tasks or certify
their coverage.

[Working Group home](../README.rst)
