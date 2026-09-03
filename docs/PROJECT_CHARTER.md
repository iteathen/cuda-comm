# CUDA-COMM Project Charter

**Status:** Accepted architecture after bootstrap integration; production implementation not authorized.

## Purpose

Provide reusable provider-neutral GPU communication semantics above public CUDA-JS mechanisms without moving native transport/resource ownership or consumer policy into this repository.

## CUDA-COMM owns, when separately accepted

- communication group/team/rank and membership-generation meaning;
- collective operations such as broadcast/reduce/all-reduce/all-gather/reduce-scatter/all-to-all;
- provider-neutral point-to-point communication where reusable;
- PGAS/remote-memory-window, one-sided put/get and signaling/ordering semantics;
- finite communication plans, semantic completion/failure composition and provider-neutral equivalence;
- communication-topology requirements/policy without owning physical discovery/admin.

## CUDA-COMM does not own

CUDA device/context discovery; raw peer-access/RDMA registration; memory allocation; streams/events/operations; native NCCL/NVSHMEM handles/bootstrap/transports; cluster scheduling/admin; NN training semantics; MCGS search/replica semantics; or product topology policy.

## Provider boundary

CUDA-JS owns bounded native/provider mechanisms and resource lifecycle. CUDA-COMM owns communication meaning above those mechanisms. A low-level CUDA-JS NCCL call may express an AllReduce provider operation; the provider-neutral group/world/order/failure contract remains here.

NCCL and NVSHMEM are separate profiles: NCCL emphasizes collectives/P2P; NVSHMEM adds PGAS, one-sided operations and GPU-initiated communication. They may coexist without becoming interchangeable.

## Dependency direction

`cuda-comm -> public cuda-js`. Consumers may optionally depend on CUDA-COMM; CUDA-JS remains coherent if this repository is deleted.

## Activation gate

Issue #3 must select a smallest reusable profile from concrete consumers. Production source/API requires an accepted specification and independent reference/equivalence evidence.

## Resource/lifecycle rule

Every group/window/plan is finite and versioned with explicit membership/generation, ownership, buffer access, failure, completion and terminal disposition. Native resource truth remains lower-owned.

## Non-goals

MPI replacement, transparent cluster scheduler, elastic membership by default, consumer policy, or native provider implementation here.