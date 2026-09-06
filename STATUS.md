# CUDA-COMM Status

**Updated:** 2026-09-06

**Architecture/ownership:** accepted independent communication semantic owner under SPEC-0001.
**Production implementation/API:** not authorized / none.
**Native/provider/topology support:** none claimed.

## Current work

- #1 ownership/bootstrap authority — completed.
- #2 repository-control/protected-main alignment — completed; `main` is protected and the selected CUDA-family settings were read back.
- #3 is the current provider-neutral collective/P2P and PGAS/RMA activation roadmap; it remains planning/assessment authority, not a production specification.

## Next executable decision

Use concrete CUDA-MCGS needs to determine whether a smallest reusable communication profile is justified; collective/P2P and PGAS/RMA remain separable lanes. Future NN collective demand counts only if `cuda-nn` is independently reactivated by new semantic evidence. Production implementation still requires an accepted bounded child specification.

CUDA-JS #164 is historical/dormant NCCL native-provider provenance, currently closed `not_planned`; it is not an active dependency. NVSHMEM/NCCL/RDMA provider mechanisms activate in CUDA-JS only if an accepted CUDA-COMM profile selects them. CUDA-COMM owns provider-neutral communication meaning, never raw provider records or native resource lifecycle.

## Governance

Protected-main and repository-setting alignment is complete. No local CI workflow currently exists, so no required status-check name is fabricated.

No roadmap entry, provider availability, repository creation or completed governance bootstrap is production implementation authority.
