# CUDA-COMM Status

**Updated:** 2026-09-05

**Architecture/governance:** independent communication semantic owner integrated.

**Production implementation/API:** not authorized / none.

**Native/provider/topology support:** none claimed.

## Current work

- #1 established the durable ownership/bootstrap authority — completed.
- #2 tracks repository settings and protected-main alignment; `main` remains unprotected.
- #3 is the current provider-neutral collective and PGAS/RMA activation roadmap; it is planning/assessment authority, not a production specification.

## Next executable decision

Compare concrete CUDA-MCGS and CUDA-NN consumers and select the smallest reusable communication profile that has independent semantic value: collective/P2P and PGAS/RMA remain separable lanes. Any production implementation still requires an accepted bounded child specification and public lower-layer mechanisms.

CUDA-JS #164 remains the lower NCCL mechanism tracker. NVSHMEM and GPUDirect-RDMA require lower-layer CUDA-JS/infrastructure mechanism work before accelerated production realization here. CUDA-COMM owns reusable group/team/rank, ordering, collective/P2P/PGAS/RMA meaning rather than native provider records.

No roadmap entry, repository creation or completed governance bootstrap is production implementation authority.
