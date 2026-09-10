# oneMath domain split: WG decision brief

**Status: needs a new Working Group decision.** This brief prepares the discussion;
it does not approve, cancel or supersede the original direction.

## Why revisit it

The [June 25, 2024 minutes](../notes/2024-06-25.rst) record consensus to proceed
with splitting the former oneMKL interfaces project by domain, with implementation
details still to resolve. Twelve implementation tasks remain open.

The current [oneMath source tree](https://github.com/uxlfoundation/oneMath/tree/develop/src)
contains BLAS, DFT, LAPACK, RNG and sparse BLAS together. That layout and the
oneMath rename do not establish that the split was cancelled or completed.
During the September 10, 2026 maintenance review, WG co-chair John Melonakos
confirmed that a new WG decision is needed.

## Decision to record

Discuss whether to continue the separate-repository plan, revise its scope, or
retain the domains together. For the selected direction, record the rationale,
affected projects, compatibility implications and links to the decision minutes.

Consider shared types and exceptions, dependencies between domains, release and
version coordination, CI cost, contributor navigation and migration effort.
Refer to the [dynamic oneAPI specification](https://uxlfoundation.org/specifications/oneapi/technical-overview/)
and current project documentation for interfaces; this brief does not change them.

## Tasks affected

| Work | Existing tasks |
| --- | --- |
| Shared repository and common header | [#126](https://github.com/uxlfoundation/open-source-working-group/issues/126), [#127](https://github.com/uxlfoundation/open-source-working-group/issues/127) |
| BLAS repository and code | [#128](https://github.com/uxlfoundation/open-source-working-group/issues/128), [#133](https://github.com/uxlfoundation/open-source-working-group/issues/133) |
| DFT repository and code | [#129](https://github.com/uxlfoundation/open-source-working-group/issues/129), [#134](https://github.com/uxlfoundation/open-source-working-group/issues/134) |
| LAPACK repository and code | [#130](https://github.com/uxlfoundation/open-source-working-group/issues/130), [#135](https://github.com/uxlfoundation/open-source-working-group/issues/135) |
| RNG repository and code | [#131](https://github.com/uxlfoundation/open-source-working-group/issues/131), [#136](https://github.com/uxlfoundation/open-source-working-group/issues/136) |
| Sparse BLAS repository and code | [#132](https://github.com/uxlfoundation/open-source-working-group/issues/132), [#137](https://github.com/uxlfoundation/open-source-working-group/issues/137) |

## Follow-through

Keep the tasks open pending the decision. Afterwards, update their scope and
completion criteria, record agreed owners for continuing work, and close only
tasks explicitly superseded or supported by completion evidence. Link each update
to the decision so the historical agreement remains understandable.

[Meeting archive](../notes/README.rst) · [Working Group home](../../README.rst)
