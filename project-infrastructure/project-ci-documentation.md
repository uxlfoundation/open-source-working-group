# Project Infrastructure for CI and CD

UXL Foundation CI Infrastructure
================================

The table outlines the existing shared public CI available to UXL Foundation projects.

| Owner | Type | OS | Number | Active? | Notes |
| --- | --- | --- | --- | --- | --- |
| GitHub | CPU x86 | Linux, Windows, Mac | Up to 500 concurrent | Yes | |
| GitHub | CPU AArch64 | Linux, Mac | Up to 500 concurrent | Yes | |
| Intel | Intel GPU Max 1550 | Linux | Varies depending on request | Yes | |
| Codeplay | CPU AArch64 | Linux | Cloud-based | Yes | Available until 31 May |
| Codeplay | Intel GPU Battlemage B580 | Linux | 1 | No | |

The following sections gather together, for each UXL Foundation project, the existing public CI set up and the minimum CI requirements so that contributions can be received with confidence that sufficient testing has been done.
This document gathers together for each UXL Foundation project the minimum CI requirements so that contributions can be received with confidence that sufficient testing has been done.
Currently much of the project CI is hosted by internal corporate infrastructure, and is separated from the open source repositories.

This initiative is being kicked off to bring as much public CI as is possible for the UXL Foundation projects.

oneDNN
------

Representative: Vadim Pirogov @vpirogov

Support contacts for CI:

| Area               | Owner                     |
| ------------------ | ------------------------- |
| AArch64            | Hamza Butt @theComputeKid |
| x64, new platforms | Vadim Pirogov @vpirogov   |

*Existing public CI*

| Target      | OS                    | Concurrency  | Active? | How to access logs  |
| ----------- | --------------------- | ------------ | ------- | ------------------- |
| CPU x64     | Linux, Windows, macOS | 2            | Yes     | CI x64 PR check     |
| CPU AArch64 | Linux, macOS          | 2            | Yes     | CI AArch64 PR check |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

Basic required CI coverage includes reasonable OS coverage for all supported
platforms.

| Target        | OS                    |
| ------------- | --------------------- |
| CPU AArch64   | Linux, Windows, macOS |
| CPU PowerPC64 | Linux                 |
| CPU RISC-V    | Linux                 |
| CPU x64       | Linux, Windows, macOS |
| GPU AMD       | Linux, Windows        |
| GPU Intel     | Linux, Windows        |
| GPU NVIDIA    | Linux, Windows        |

oneDNN is a performance library and includes multiple specialized code paths for
relevant hardware features. To test these code paths CI must include functional
and performance testing coverage for all hardware variants that have specific
implementations.

| Target        | ISA/IP Variants                          |
| ------------- | ---------------------------------------- |
| CPU AArch64   | ARMv8.2-A, ARMv8.4 SVE                   |
| CPU PowerPC64 | Power ISA Base                           |
| CPU RISC-V    | RISC-V, RVV 1.0                          |
| CPU x64       | Intel AVX2, Intel AVX-512, Intel AVX10.1 |
| GPU AMD       | CDNA 2                                   |
| GPU Intel     | Xe, Xe2, Xe3                             |
| GPU NVIDIA    | GV100                                    |

Software requirements and minimal supported versions are documented in [project
README.md](https://github.com/uxlfoundation/oneDNN?tab=readme-ov-file#requirements-for-building-from-source).

oneDPL
------

Representative: Timmie Smith

Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| ? | ? | ? | ? | ? | ? |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| AArch64 | Arm | CPU | Ubuntu |

Software Versions:
* CMake
* glibc
* ...

oneDAL
------

Representative: [Nikolay Petrov](https://github.com/napetrov)

Support contacts for CI:

| Area               | Owner                                                                                               |
| ------------------ | --------------------------------------------------------------------------------------------------- |
| AArch64            | [Hamza Butt](https://github.com/theComputeKid) [Rakshith G B](https://github.com/rakshithgb-fujitsu)|
| RISC-V             | [Keeran Rothenfusser](https://github.com/keeranroth)                                                |
| x64, new platforms | [Nikolay Petrov](https://github.com/napetrov)                                                       |

More details available in [MAINTAINERS.md](https://github.com/uxlfoundation/oneDAL/blob/main/MAINTAINERS.md)

*Existing public CI*

oneDAL

| Platform | Type | OS | Number | Active? | Comments |
| --- | --- | --- | --- | --- | --- |
| Github | CPU AArch64 | Linux | 2 | Yes | 2 Pipelines on Physical ARM systems Github hosted and ARM hosted. [ci-aarch64.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/ci-aarch64.yml)  |
| Github | Intel GPU (ICX compiler) | Linux | 1 | Yes* | Pipeline configured for GPU validation on uxlfoundation GPU runners, currently disabled due to issues with Tiber Cloud. [ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/ci.yml)  |
| Github | ABI conformance | Linux | 1 | Yes | 2 Pipelines on Physical ARM systems Github-hosted and ARM-hosted. [ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/ci.yml)  |
| Github | Docker validation | Linux | 1 | Yes | Validation of oneDAL development env docker file. [docker-validation-ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/docker-validation-ci.yml)  |
| Github | CPU Nightly | Linux, Windows | 2 | Yes | Nightly builds and broader validation for oneDAL. [nightly-build.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/nightly-build.yml)  |
| Github | Copyright headers check | Linux | 1 | Yes | Check for proper copyright headers. [skywalking-eyes.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/skywalking-eyes.yml)  |
| Github | PR checklist validation | Linux | 1 | Yes | Validation of PR conformance. [pr-checklist.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/pr-checklist.yml)  |
| Github | Documentation deployment to gh-pages | Linux | 1 | Yes | Automatic docs deployment with release tag creation. [docs-release.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/workflows/docs-release.yml)  |
| Mergify | Helper automation for merges/backporting | Linux | 1 | Yes | Automated labels assignment, removal of renovate branches. .[mergify.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.github/.mergify.yml)  |
| Renovate | Automated dependency updates | Linux | 1 | Yes | Dependabot alternative, manages dependency updates for components. [renovate.json](https://github.com/uxlfoundation/oneDAL/blob/main/.github/renovate.json)  |
| Azure DevOps | Clang format check| Linux | 1 | Yes | Enforce coding standards. [ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.ci/pipeline/ci.yml)  |
| Azure DevOps | CI build/test for x86/ARM/RISC-V with OS compilers | Linux, Windows | 8 | Yes | Intel build natively, ARM and RISC-V with cross-platform build and QEMU emulation. Build with GCC/VC compilers. [ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.ci/pipeline/ci.yml)  |
| Azure DevOps | CI build/test with Bazel | Linux | 1 | Yes | Bazel-based build and validation. [ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.ci/pipeline/ci.yml)  |
| Azure DevOps | oneDAL documentation build | Linux | 1 | Yes | Build documentation for validation purposes in CI. [docs.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.ci/pipeline/docs.yml)  |
| Azure DevOps | sklearnex validation | Linux | 1 | Yes | Checking out sklearnex sources, doing build and validation with oneDAL PR changes. [ci.yml](https://github.com/uxlfoundation/oneDAL/blob/main/.ci/pipeline/ci.yml)  |
| Codefactor | Codefactor checks | N/A | 1 | Yes | Enforcing code checks in PRs, Bandit, and other code quality checks. [Codefactor](https://www.codefactor.io/repository/github/uxlfoundation/onedal)  |

*Required Public CI Infrastructure Needed To Confidently Accept Contributions*
Currently internal intel CI validation is required for code verification. 
Intel employees can start internal CI with comment "/intelci: run" and corresponding CI would be triggered.
It's not possible to access logs without access to Intel network

Migration to public validation is possible but would require more x86 systems available in public - currently public validation covers only ~20% of validation scopes 

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu, Windows |
| AArch64 | Arm | CPU | Ubuntu |
| Xe, Xe2, Xe3 | Intel | GPU | Ubuntu, Windows |

Software Versions:
* C/C++ Compiler
* DPC++ Compiler and oneMKL if building with SYCL support
* BLAS and LAPACK libraries - both provided by oneMKL or openBLAS could be used 
* Python version 3.9 or higher
* oneTBB library (repository contains script to download it)
* oneDPL library if building with SYCL support
* Microsoft Visual Studio* (Windows* only)
* MSYS2 (Windows* only)
* make and dos2unix tools
Full list of SW requirements and steps defined in [INSTALL.md](https://github.com/uxlfoundation/oneDAL/blob/main/INSTALL.md)


oneCCL
------

Representative: Maria Petrova

Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| ? | ? | ? | ? | ? | ? |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| AArch64 | Arm | CPU | Ubuntu |

Software Versions:
* CMake
* glibc
* ...

oneMath
-------

Representative: Maria Kraynyuk

Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| ? | ? | ? | ? | ? | ? |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| AArch64 | Arm | CPU | Ubuntu |

Software Versions:
* CMake
* glibc
* ...

oneTBB
------

Representative: Michael Voss

Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| ? | ? | ? | ? | ? | ? |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| AArch64 | Arm | CPU | Ubuntu |

Software Versions:
* CMake
* glibc
* ...

oneCK
-----

Representative: Aaron Dron

Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| ? | ? | ? | ? | ? | ? |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| AArch64 | Arm | CPU | Ubuntu |

Software Versions:
* CMake
* glibc
* ...
