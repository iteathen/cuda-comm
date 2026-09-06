# SPEC-0001: Native Boundary and JavaScript/TypeScript Implementation

**Status:** Accepted architecture/ownership authority; production communication profiles remain separately gated.

**Version:** 1.0.0

**Owner:** CUDA-COMM

**Lower authority:** `iteathen/CUDA-JS` SPEC-0032

## Purpose

CUDA-COMM owns reusable provider-neutral communication semantics. CUDA-JS is the sole native CUDA/provider integration owner.

## Repository implementation rule

Maintained CUDA-COMM source is JavaScript/TypeScript. Restricted Device-JS generation is permitted only through public CUDA-JS contracts.

CUDA-COMM does not maintain C, C++, CUDA C++, PTX, direct FFI, native addons, NCCL/NVSHMEM/RDMA bindings, native handles/pointers, ABI structs or platform discovery code. Native evidence may be produced externally and recorded, but native oracle/provider source is not maintained here.

A missing native mechanism routes to CUDA-JS before any local workaround.

## CUDA-COMM owns

- group/team/rank/membership/generation meaning;
- collective and P2P communication semantics;
- PGAS/RMA operation, ordering, completion and failure semantics;
- provider-neutral communication equivalence;
- communication-specific finite resources, pressure and semantic scheduling policy;
- JavaScript/TypeScript reference and conformance evidence.

## CUDA-JS owns

- physical devices/contexts and native peer capability;
- native peer-access/copy mechanisms;
- NCCL/NVSHMEM/RDMA or other native provider resources if selected;
- native streams/events/operations/memory/provider compatibility;
- native errors and teardown.

A CUDA-JS P2P copy primitive does not itself create CUDA-COMM P2P semantics, and CUDA-COMM semantics do not authorize a private native implementation.

## Multi-device boundary

Applications such as CUDA-MCGS or CUDA-NN retain their distributed/search/training policy. CUDA-COMM owns only reusable communication meaning. Physical placement/topology facts are consumed from public CUDA-JS; generic cross-domain memory placement strategy requires a separate JavaScript/TypeScript owner if independently justified.

## Activation gate preservation

This specification does not select NCCL, NVSHMEM, RDMA, a collective profile or a multi-GPU runtime. Existing consumer/profile activation gates remain authoritative.

## Non-goals

No native communication backend, no cluster scheduler, no application partition policy, no arbitrary provider passthrough, no production capability or support claim.
