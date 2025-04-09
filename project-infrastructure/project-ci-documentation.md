# Project Infrastructure for CI and CD

UXL Foundation CI Infrastructure
================================

The table outlines the existing shared public CI available to UXL Foundation projects.

| Owner | Type | OS | Number | Active? | Notes |
| --- | --- | --- | --- | --- | --- |
| GitHub | CPU x86 | Linux, Windows, Mac | Up to 500 concurrent | Yes | |
| GitHub | CPU aarch64 | Linux, Mac | Up to 500 concurrent | Yes | |
| Intel | Intel GPU Max 1550 | Linux | Varies depending on request | Yes | |
| Codeplay | CPU aarch64 | Linux | Cloud-based | Yes | Available until 31 May |
| Codeplay | Intel GPU Battlemage B580 | Linux | 1 | No | |

The following sections gather together, for each UXL Foundation project, the existing public CI set up and the minimum CI requirements so that contributions can be received with confidence that sufficient testing has been done.
This document gathers together for each UXL Foundation project the minimum CI requirements so that contributions can be received with confidence that sufficient testing has been done.
Currently much of the project CI is hosted by internal corporate infrastructure, and is separated from the open source repositories.

This initiative is being kicked off to bring as much public CI as is possible for the UXL Foundation projects.

oneDNN 
------

Representative: Vadim Pirogov
Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| ? | ? | ? | ? | ? | ? |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System | 
| --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu |
| aarch64 | Arm | CPU | Ubuntu |

Software Versions

CMake
glibc
...

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
| aarch64 | Arm | CPU | Ubuntu |

Software Versions

CMake
glibc
...

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
| aarch64 | Arm | CPU | Ubuntu |

Software Versions

CMake
glibc
...

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
| aarch64 | Arm | CPU | Ubuntu |

Software Versions

CMake
glibc
...

oneMath
-------

Representative: Maria Kraynyuk
Support contact for CI:

*Existing public CI*

| Owner | Type | OS | Number | Active? | How to access logs |
| --- | --- | --- | --- | --- | --- |
| GitHub	| CPU x86 | Ubuntu latest | N/A - GitHub-hosted runners | Yes | From workflow run |

*Required Public CI Infrastruture Needed To Confidently Accept Contributions*

| Instruction set architecture | Hardware Vendor | Processor Type | Operating System | Comment |
| --- | --- | --- | --- | --- |
| x86 | Intel | CPU | Ubuntu | Already supported in Public CI |
| aarch64 | Arm | CPU | Ubuntu | Arm Neoverse Processor Family: N1, V1, or V2 |
| Intel Data Center Max Series | Intel | GPU | Ubuntu | Or at least one from [Intel oneMKL supported list](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-math-kernel-library-system-requirements.html) on Linux |
| A100 or H100 | NVIDIA | GPU | Ubuntu | Or at least Compute Capability 7.5 or later (T4+), see [CUDA toolkit deprecated GPUs](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html#deprecated-architectures) |
| MI210 | AMD | GPU | Ubuntu | Or at least one from [ROCm supported list](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/reference/system-requirements.html) |
| x86 | Intel | CPU | Windows | Can be supported with GitHub-hosted runners, but they have not enough procesors for acceptable build time |
| Intel Flex or Arch Series | Intel | GPU | Windows | Or at least one from [Intel oneMKL supported list](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-math-kernel-library-system-requirements.html) on Windows |

Software requiremenbts: [link](https://github.com/uxlfoundation/oneMath/tree/develop?tab=readme-ov-file#software-requirements)

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
| aarch64 | Arm | CPU | Ubuntu |

Software Versions

CMake
glibc
...

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
| aarch64 | Arm | CPU | Ubuntu |

Software Versions

CMake
glibc
...
