# PROOF-NEEDS.md — neural-foundations

## Current State

- **src/abi/*.idr**: YES (in satellites) — echidna has `BojForeign.idr`, `Foreign.idr`, `Layout.idr`, `Overlay.idr`
- **Dangerous patterns**: 0 in own code (27 references are all in rule/detection code that identifies dangerous patterns in other repos)
- **LOC**: ~153,000 (Rust + Agda + Julia + Idris2)
- **ABI layer**: ECHIDNA has comprehensive Idris2 ABI with explicit "NO believe_me" invariant
- **Existing proofs**: Agda proofs in `echidna/proofs/agda/` and `echidna/meta-checker/`

## What Needs Proving

| Component | What | Why |
|-----------|------|-----|
| ECHIDNA axiom safety checker | Meta-checker correctly classifies all axiom types | The tool that checks OTHER proofs must itself be proven correct |
| ECHIDNA prover integrations | Each prover bridge (Dafny, dReal, Frama-C, F*, Imandra, Kissat, MetaMath, MiniZinc, Mizar, NuSMV, PRISM) faithfully translates | Incorrect translation makes proof results meaningless |
| LLM-unify parser correctness | Claude/Copilot/Gemini parsers extract correct structured data | Wrong parsing produces incorrect model comparisons |
| Elegant-state consensus | Voting/proposal mechanism produces correct outcomes | Distributed consensus bugs lose data |
| Conative-gating SLM | Small language model gating decisions are sound | Incorrect gating passes unsafe content |

## Recommended Prover

**Agda** for ECHIDNA meta-checker (already in Agda). **Idris2** for ABI layer extensions. The prover bridge translations are ideal for **Lean4** relational proofs.

## Priority

**HIGH** — ECHIDNA is the proof verification meta-tool. If the meta-checker itself has bugs, it undermines all downstream formal verification. The existing Agda proofs need extension to cover all prover bridges.
