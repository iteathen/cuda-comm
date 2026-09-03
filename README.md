# cuda-comm

Reusable, application-neutral GPU communication semantics above CUDA-JS mechanisms.

**Status:** architecture/governance bootstrap; production implementation not authorized.

CUDA-COMM is intended to own provider-neutral group/team/rank, collective, point-to-point and PGAS/RMA semantics. CUDA-JS remains the owner of native NCCL/NVSHMEM/peer/RDMA provider mechanisms and CUDA resource lifecycle.

CUDA-COMM does not own distributed-training policy, MCGS search/replica policy, or transparent cluster orchestration.

Start with `AGENTS.md`, `docs/PROJECT_CHARTER.md`, and `docs/decisions/ADR-0001-independent-communication-semantic-owner.md`.

Tracking: #1 ownership/bootstrap, #2 repository controls, #3 semantic roadmap.

No package, API, provider, support, topology, performance or production-readiness claim exists yet.