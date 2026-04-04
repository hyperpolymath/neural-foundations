# TEST-NEEDS.md — neural-foundations

> Generated 2026-03-29 by punishing audit.

## Current State — Updated 2026-04-04

| Category     | Count | Notes |
|-------------|-------|-------|
| Unit tests   | ~8    | echidna: test_agda_backend.rs, test_neural_integration.rs, ffi_integration_test.rs, prover tests (unified_test.ts, prover_test.ts). llm-antidote: test_suite.py |
| Integration  | ~5    | echidna: integration_test.sh, Zig core_native_test.zig, integration_test.zig. llm-unify: e2e_test.sh |
| E2E          | 3     | llm-unify e2e_test.sh, echidna tests/e2e_proof_pipeline.rs (29 tests), llm-unify-core tests/e2e_routing_test.rs (10 tests) |
| P2P/Property | 31    | echidna tests/neural_property_tests.rs — embedding/dispatch/trust/hash/axiom/prover |
| Aspect       | 32    | echidna tests/security_aspect_tests.rs — forgery/injection/escalation/axiom/integrity |
| Concurrency  | 27    | echidna tests/concurrency_test.rs — parallel factory/routing/trust/hash/agent/axiom |
| Benchmarks   | 5     | echidna: proof_benchmarks.rs, routing_benchmarks.rs (7 groups), benchmark.zig, overlay_benchmark.zig. llm-antidote: benchmark.py |

**Source modules:** ~337 across 3 satellite groups. neurosymbolic/echidna: ~104 Rust src + Idris2 ABI + Zig FFI + Julia. foundation-models: llm-antidote, llm-unify, llm-unify-core. agentic: elegant-state, conative-gating, agentic-scm.

## What's Missing (Remaining After 2026-04-04 Session)

### Completed in 2026-04-04 CRG C Blitz ✓

- [x] echidna E2E: full proof request → prover selection → proof generation → verification (`tests/e2e_proof_pipeline.rs`)
- [x] llm-unify E2E: request → routing → normalisation → fallback (`crates/llm-unify-core/tests/e2e_routing_test.rs`)
- [x] P2P property tests: embedding, dispatch, trust monotonicity, hash stability, axiom ordering (`tests/neural_property_tests.rs`)
- [x] Security aspect tests: forgery, injection, escalation, axiom sanitisation, integrity (`tests/security_aspect_tests.rs`)
- [x] Concurrency tests: parallel factory, routing, trust, hashing, agent, axiom (`tests/concurrency_test.rs`)
- [x] Routing benchmarks: decision latency, axiom throughput, trust computation, factory instantiation, agentic planning, BLAKE3 (`benches/routing_benchmarks.rs`)

### Still Missing

- [ ] Agentic E2E: agent lifecycle (create → plan → execute → evaluate) for elegant-state, conative-gating
- [ ] LLM antidote adversarial property tests — NOTE: test_suite.py is semi-manual and Python (banned). Needs rewrite in Julia or Rust.
- [ ] Cross-satellite: echidna proof + llm-unify inference in combined workflow
- [ ] Fuzz harness: replace `tests/fuzz/placeholder.txt` with a real cargo-fuzz harness

### P2P (Property-Based) Tests — Remaining
- [ ] LLM antidote: adversarial input property tests (blocked: Python banned, needs Julia rewrite)
- [ ] Prover backends: equivalence property tests across all 49 prover implementations (coverage increase)

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
