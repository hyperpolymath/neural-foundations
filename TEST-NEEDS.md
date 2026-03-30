# TEST-NEEDS.md — neural-foundations

> Generated 2026-03-29 by punishing audit.

## Current State

| Category     | Count | Notes |
|-------------|-------|-------|
| Unit tests   | ~8    | echidna: test_agda_backend.rs, test_neural_integration.rs, ffi_integration_test.rs, prover tests (unified_test.ts, prover_test.ts). llm-antidote: test_suite.py |
| Integration  | ~5    | echidna: integration_test.sh, Zig core_native_test.zig, integration_test.zig. llm-unify: e2e_test.sh |
| E2E          | 1     | llm-unify e2e_test.sh |
| Benchmarks   | 4     | echidna: proof_benchmarks.rs, benchmark.zig, overlay_benchmark.zig. llm-antidote: benchmark.py |

**Source modules:** ~337 across 3 satellite groups. neurosymbolic/echidna: ~104 Rust src + Idris2 ABI + Zig FFI + Julia. foundation-models: llm-antidote, llm-unify, llm-unify-core. agentic: elegant-state, conative-gating, agentic-scm.

## What's Missing

### P2P (Property-Based) Tests
- [ ] echidna proof engine: property tests for proof soundness (no invalid proof accepted)
- [ ] Neural integration: property tests for embedding consistency
- [ ] LLM antidote: adversarial input property tests
- [ ] Prover backends: equivalence property tests across prover implementations

### E2E Tests
- [ ] echidna: full proof request -> prover selection -> proof generation -> verification
- [ ] llm-unify: request -> routing -> model inference -> response normalization
- [ ] agentic: agent lifecycle (create -> plan -> execute -> evaluate)
- [ ] Cross-satellite: echidna proof + llm-unify inference in combined workflow

### Aspect Tests
- **Security:** No tests for proof forgery, model injection in llm-unify, agent privilege escalation
- **Performance:** Benchmarks exist for echidna (good) and llm-antidote. Missing: llm-unify latency, agentic execution time
- **Concurrency:** No tests for parallel proof generation, concurrent model inference, agent contention
- **Error handling:** No tests for prover timeout, model unavailability, malformed proof input, invalid agent state

### Build & Execution
- [ ] `cargo test` for echidna Rust
- [ ] `zig build test` for FFI
- [ ] Python test runner for llm-antidote
- [ ] Shell test execution for integration tests

### Benchmarks Needed
- [ ] Proof generation latency by complexity
- [ ] LLM routing decision time
- [ ] Agent planning throughput
- [ ] Cross-prover comparison benchmarks
- [ ] Neural overlay inference time

### Self-Tests
- [ ] Prover health checks (each backend reachable)
- [ ] Model availability verification
- [ ] Proof chain integrity validation

### CRITICAL GAPS

| Subsystem | Source Files | Tests | Status |
|-----------|-------------|-------|--------|
| echidna | ~104 | ~8 | **7.7% — insufficient** |
| llm-antidote | unknown | 1 suite | Minimal |
| llm-unify | unknown | 1 e2e | Minimal |
| agentic (elegant-state) | unknown | 1 archived | **Effectively 0** |
| conative-gating | unknown | 0 | **Untested** |
| agentic-scm | unknown | 0 | **Untested** |

## Priority

**CRITICAL.** 337 source files across a neurosymbolic AI framework with ~14 test files total. echidna at 104 Rust files with 8 tests is 7.7% coverage. The agentic subsystem is completely untested. Benchmarks for echidna are a bright spot, but the overall test story is woeful for a framework that generates formal proofs — the proof engine itself needs far more rigorous testing.

## FAKE-FUZZ ALERT

- `tests/fuzz/placeholder.txt` is a scorecard placeholder inherited from rsr-template-repo — it does NOT provide real fuzz testing
- Replace with an actual fuzz harness (see rsr-template-repo/tests/fuzz/README.adoc) or remove the file
- Priority: P2 — creates false impression of fuzz coverage
