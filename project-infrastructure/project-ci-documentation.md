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

| Maintainers               |
| ------------------------- |
| Dan Hoeflinger @danhoeflinger |
| Dmitriy Sobolev @dmitriy-sobolev |
| Timmie Smith @timmiesmith |

*Existing public CI*

| Owner | Type | OS | How to access logs |
| --- | --- | --- | --- | --- | --- | --- |
| GitHub | CPU x86 | Ubuntu | Via CI Testing Workflow view |
| GitHub | CPU x86 | Windows | Via CI Testing Workflow view |
| GitHub | AArch64 | Mac OS | Via CI Testing Workflow view |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System |
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| AArch64 | Arm | CPU | Ubuntu |
| Xe, Xe2, Xe3 | Intel | GPU | Ubuntu, Windows |
|  | NVIDIA | GPU | Ubuntu, Windows |
|  | AMD | GPU | Ubuntu, Windows |

There are no special paths for particular architectures for AMD and NVIDIA GPUs in oneDPL at this point. It is
sufficient for correctness to run functional testing on one GPU from a vendor.

Testing on CPU platforms must exercise several execution policies with OpenMP and oneTBB to cover all of the oneDPL backends.
| Processor Type | Execution Policy |
| --- | --- |
| CPU | seq, unseq, par (using oneTBB), par (using OpenMP), par\_unseq(using oneTBB), par\_unseq(using OpenMP) |
| GPU | device\_policy |

Software Versions:
| Windows | Linux | MacOS (Arm CPU testing) |
| --- | --- | --- |
| OpenMP | OpenMP | OpenMP |
| oneTBB | oneTBB | oneTBB |
| CMake 3.20 | CMake 3.11 | CMake 3.11 |
| git | git | git |
| python | python | python |
| DPC++ Compiler | DPC++ Compiler | clang++ compiler |
| ninja | clang++ compiler | |
| Visual Studio 2019 | g++ | |
| Visual Studio 2022 | | |

oneDAL
------

Representative: Nikolay Petrov

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
