# ADR-0001: Independent GPU Communication Semantic Owner

**Status:** Accepted

**Date:** 2026-09-02

## Context

CUDA-JS owns generic multi-device/runtime/provider mechanisms, while CUDA-NN and CUDA-MCGS need materially different distributed behaviors. NCCL provides collective/P2P mechanisms; NVSHMEM provides PGAS/one-sided and GPU-initiated communication. Putting reusable communication meaning in either consumer would encode the first consumer; putting all group/world/collective/PGAS semantics in CUDA-JS would turn the runtime substrate into a communication framework.

## Decision

`cuda-comm` owns reusable provider-neutral communication semantics. CUDA-JS retains native/provider/resource mechanisms. NN/MCGS/products retain why communication affects their own state/policy.

## Deletion test

Deleting CUDA-NN or CUDA-MCGS leaves CUDA-COMM coherent. Deleting CUDA-COMM leaves CUDA-JS a coherent generic runtime. No public CUDA-COMM contract may require one consumer's vocabulary.

## Provider separation

NCCL collective/P2P and NVSHMEM PGAS/RMA are distinct profiles with different ordering, membership and progress implications. CUDA-COMM may normalize common concepts only when doing so preserves those differences.

## Implementation gate

Issue #3 selects a bounded consumer-backed semantic profile. Native provider implementation remains lower-layer work and no source/API is authorized by this ADR alone.

## Consequences

Reusable communication has one semantic owner, consumer policies remain separate, and native transport/resource authority stays below the semantic layer.