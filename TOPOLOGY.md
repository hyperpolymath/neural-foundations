<!-- SPDX-License-Identifier: PMPL-1.0-or-later -->
<!-- TOPOLOGY.md — Project architecture map and completion dashboard -->
<!-- Last updated: 2026-02-19 -->

# Neural Foundations — Project Topology

## System Architecture

```
                        ┌─────────────────────────────────────────┐
                        │              AI DEVELOPER               │
                        │        (Research, Logic, Systems)       │
                        └───────────────────┬─────────────────────┘
                                            │
                                            ▼
                        ┌─────────────────────────────────────────┐
                        │           NEURAL FOUNDATIONS HUB        │
                        │                                         │
                        │  ┌───────────┐  ┌───────────────────┐  │
                        │  │ Foundation│  │ Agentic Systems   │  │
                        │  │ Models    │  │ (Multi-Agent,     │  │
                        │  │ (LLM-Unify│  │  AI Control)      │  │
                        │  └─────┬─────┘  └────────┬──────────┘  │
                        │        │                 │              │
                        │  ┌─────▼─────┐  ┌────────▼──────────┐  │
                        │  │ Neuro-    │  │  Shared Context   │  │
                        │  │ symbolic  │  │  Primitives       │  │
                        │  │ (ESN, LSM)│  │                   │  │
                        │  └─────┬─────┘  └───────────────────┘  │
                        └────────│────────────────────────────────┘
                                 │
                                 ▼
                        ┌─────────────────────────────────────────┐
                        │          SATELLITE REPOSITORIES         │
                        │  ┌───────────┐  ┌───────────┐  ┌───────┐│
                        │  │ llm-unify │  │ conative- │  │ echidna││
                        │  └───────────┘  └───────────┘  └───────┘│
                        │  ┌───────────┐  ┌───────────┐  ┌───────┐│
                        │  │ neurophone│  │ elegant-  │  │ esn/lsm││
                        │  └───────────┘  └───────────┘  └───────┘│
                        └───────────────────┬─────────────────────┘
                                            │
                                            ▼
                        ┌─────────────────────────────────────────┐
                        │          APPLICATION ECOSYSTEM          │
                        │      (poly-mcps, oikos, dashboard)      │
                        └─────────────────────────────────────────┘

                        ┌─────────────────────────────────────────┐
                        │          REPO INFRASTRUCTURE            │
                        │  Justfile / Rust    .machine_readable/  │
                        │  Julia / ReScript   0-AI-MANIFEST.a2ml  │
                        └─────────────────────────────────────────┘
```

## Completion Dashboard

```
COMPONENT                          STATUS              NOTES
─────────────────────────────────  ──────────────────  ─────────────────────────────────
CORE FOUNDATIONS
  Foundation Models (Hub)           ██████████ 100%    LLM-Unify architecture stable
  Agentic Systems                   ████████░░  80%    Control mechanisms refining
  Neurosymbolic Blocks              ██████████ 100%    ESN/LSM primitives verified
  Semantic Primitives               ██████░░░░  60%    Knowledge extraction active

ECOSYSTEM SATELLITES
  echidna (Theorem Prover)          ██████████ 100%    30 backends operational
  neurophone (Mobile AI)            ████████░░  80%    SNN integration active
  conative-gating                   ██████████ 100%    Inhibitory SLM stable
  llm-unify-core                    ██████████ 100%    Shared types stable

REPO INFRASTRUCTURE
  Justfile Automation               ██████████ 100%    Standard build tasks
  .machine_readable/                ██████████ 100%    STATE tracking active
  Language Policy (CCCP)            ██████████ 100%    RSR stack verified

─────────────────────────────────────────────────────────────────────────────
OVERALL:                            █████████░  ~90%   Foundational hub operational
```

## Key Dependencies

```
Philosophy ──────► Foundation Tech ───► Neural Hub ──────► Satellites
     │                 │                   │                 │
     ▼                 ▼                   ▼                 ▼
CCCP Policy ──────► RSR Compliance ───► Scaffolding ───► Applications
```

## Update Protocol

This file is maintained by both humans and AI agents. When updating:

1. **After completing a component**: Change its bar and percentage
2. **After adding a component**: Add a new row in the appropriate section
3. **After architectural changes**: Update the ASCII diagram
4. **Date**: Update the `Last updated` comment at the top of this file

Progress bars use: `█` (filled) and `░` (empty), 10 characters wide.
Percentages: 0%, 10%, 20%, ... 100% (in 10% increments).
