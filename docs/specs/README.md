# CUDA-COMM specifications

**Architecture/ownership authority is accepted; no production communication capability specification is accepted yet.**

- [`SPEC-0001-native-boundary-and-js-only-implementation.md`](SPEC-0001-native-boundary-and-js-only-implementation.md) — accepted cross-cutting rule that CUDA-COMM remains JavaScript/TypeScript, CUDA-JS owns native peer/provider/device integration, and provider-neutral communication semantics remain here. This specification does not select NCCL/NVSHMEM/RDMA or authorize a communication profile.

The [activation roadmap](https://github.com/iteathen/cuda-comm/issues/3) organizes assessment. Production implementation must first have a bounded, consumer-backed semantic contract accepted under the [development instructions](../../AGENTS.md).

Start with the [project charter](../PROJECT_CHARTER.md) and [architecture decision](../decisions/README.md) to understand the intended scope.
