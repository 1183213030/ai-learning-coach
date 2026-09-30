<div align="center">

# AI Learning Coach (V3.0)

### A Knowledge-Driven, Concept-Boundary-Expanded, and Evidence-Based Personal Learning OS

Let the user focus purely on learning; let the AI Learning Coach handle the rest.

[![Protocol Version](https://img.shields.io/badge/Protocol-v3.0.0-007ACC?style=flat-square)](#)
[![Pedagogy](https://img.shields.io/badge/Pedagogy-Minimal%20Complete%20Coverage-4EBA6F?style=flat-square)](#)
[![Interaction](https://img.shields.io/badge/Interaction-Zero--Command%20Natural%20Language-orange?style=flat-square)](#)
[![Verification](https://img.shields.io/badge/Verification-Type--Specific%20Evidence-blueviolet?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)](#)

[简体中文](README.md) • [English](README_en.md)

</div>

---

## Core Breakthrough: What is Truly "Complete Teaching"?

Traditional AI instruction suffers from a fatal flaw: **providing an abstract definition accompanied by a single happy-path example**.
The learner nods along, but collapses when faced with nuanced mutations and boundary edge traps in real code.

**AI Learning Coach V3.0** introduces a fundamental pedagogical law:
> **Do not merely explain what a concept means. Systematically unpack its entire observable behavioral boundary space (Minimal Complete Coverage).**

Learning a concept (such as `assertIn`, `Array.prototype.includes`, or JavaScript's `==`) is far more than reciting definitions. The system guides you through its **7-Dimensional Behavioral Space**:
1. **The Core Invariant**: The single underlying physical rule deciding truth.
2. **Positive Baseline Cases**: Cleanest, zero-distraction nominal conditions where it holds.
3. **Structural Variations**: Padding and mutations where it *still* surprisingly holds.
4. **Counterexample Shocks (The Critical Cognitive Step)**: Superficially identical cases that *instantly fail* (e.g. `admmmmmin` does not contain `admin`, or `['1'].includes(1)` is false), compelling the mind to isolate the invariant.
5. **Boundary & Extreme Limits**: Empty values, type coercion, `NaN`, and object references.
6. **Confusing Neighbor Contrast**: Side-by-side debate against similar ecosystem tools (e.g. `indexOf` vs `includes` vs `some`, or `==` vs `===` vs `Object.is`).
7. **Real Engineering Anchors**: Production failure points where misunderstandings cause silent, disastrous bugs.

---

## Three Dimensions of Completeness

The system operates across three tightly integrated pillars:

| Dimension | Core Mission | Implementation Mechanism |
| :--- | :--- | :--- |
| **1. Knowledge Completeness** | Map the entire operational envelope of a concept | **Concept Boundary Engine**: Invariant, Variations, Shocks, Extremes, and Neighbor Contrasts. |
| **2. Teaching Completeness** | Take a beginner from zero to deep intuition | **Shock & Deduce Cycle**: Everyday intuition -> observation -> counter-case deduction -> standard formalisms. |
| **3. Capability Completeness** | Prove unassisted independent mastery | **Type-Specific Evidence Engine**: Zero-hint (`L0`) assessment via execution simulation, boundary matrices, or clean-slate code. |

---

## Zero-Command Natural Language Interface

Communicate naturally without memorizing complex syntax:

```text
┌────────────────────────────────────────────────────────┐
│                                                        │
│  "I want to systematically master frontend engineering" │
│  "Teach me JS async concurrency; I only know await"    │
│  -> Initiates domain roadmap with light diagnostic     │
│                                                        │
│  "I don't understand closures, teach me from zero"     │
│  "That was too abstract, explain with a real analogy"  │
│  -> Beginner Mode: Intuition -> Minimal Code -> Shock  │
│                                                        │
│  "Continue learning"                                   │
│  "Exhausted today, only have 10 minutes"               │
│  -> Learner reality overrides rigid curriculum syllabi │
│                                                        │
│  "Quiz me on what we just covered, zero hints"         │
│  "Pause the book, I hit a CORS bug in production"      │
│  -> Strict L0 verification or real-world bug diagnosis │
│                                                        │
└────────────────────────────────────────────────────────┘
```

---

## The Tri-Engine Architecture

```text
                           AI Learning OS
                                  │
         ┌────────────────────────┼────────────────────────┐
         ▼                        ▼                        ▼
  Knowledge Engine         Teaching Engine          Evidence Engine
(Concept Boundary & Map)  (Adaptive Pedagogy)      (Verification & Audit)
         │                        │                        │
         ▼                        ▼                        ▼
Minimal Complete Coverage    Shock & Deduce Cycle     Type-Specific Proof
(7-Dimension Boundary)     (Intuition-Observation-  (Immutable L0 Evidence
                            Counterexample-Reality)  Ledger)
         │                        │                        │
         └────────────────────────┼────────────────────────┘
                                  ▼
                         Learner State & Graph
                         (Learner Reality > Syllabus)
                                  │
                                  ▼
                       Review & Spaced Retention
                         (Reversible state machine)
```

---

## Installation & Setup

### Google Antigravity
Natively configured for this workspace. Speak naturally in chat to begin.

### Claude Code
```bash
# Global installation
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent claude-code

# Project installation
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --agent claude-code
```

### OpenAI Codex
```bash
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent codex
```

---

## Directory Structure

```text
ai-learning-coach/
├── SKILL.md                          # V3.0 Tri-Engine Core Protocol Specification
├── README.md                         # Chinese Documentation
├── README_en.md                      # English Documentation
│
├── knowledge/                        # Evolving Knowledge Registry with 7-D Boundary Models
│   ├── frontend/javascript/          # closure.yaml, scope.yaml, includes.yaml, equality.yaml
│   └── software-testing/             # test-case.yaml, unit-test.yaml
│
├── library/                          # Local Textbook Library (Local-First Priority)
│   ├── frontend/                     # Ingested frontend literature
│   └── software-testing/             # Ingested testing handbooks
│
├── references/                       # Operational specifications (Progressive Disclosure)
│   ├── concept-boundary-engine.md    # [V3.0 Core] Minimal Complete Coverage Boundary Specification
│   ├── teaching-protocol.md          # Teacher persona, 4-way pivots, and micro-probes
│   ├── curriculum-engine.md          # Learner-state-over-curriculum arbitration
│   ├── intent-router.md              # Zero-command natural language routing & Teach vs Check
│   ├── local-library.md              # Local textbook reverse parsing protocol
│   ├── knowledge-discovery.md        # S0-S5 source strategy & provenance
│   ├── evidence-model.md             # E1-E5 evidence matrix & decoupled assessment
│   ├── learning-loop.md              # 10-step Coding Learning Loop
│   ├── coding-learning.md            # Git diff concept extraction
│   ├── socratic-hints.md             # L1-L5 scaffolding ladder
│   ├── review-system.md              # Spaced retention & dynamic regression
│   └── quality-rubric.md             # Strict qualitative evaluation standards
│
└── templates/                        # State contracts and persistence ledgers
    ├── concept-expansion.yaml        # [V3.0 Core] Standardized 7-dimension expansion blueprint
    ├── source-manifest.yaml          # Provenance & source coverage manifest
    ├── roadmap.yaml                  # Domain capability topology
    ├── curriculum-lesson.md          # Dynamic runtime lesson generator template
    ├── learner-profile.md            # Long-term learner baseline & blind spots
    ├── learning-state.yaml           # Active frontier & review queues
    ├── session.md                    # Single-session execution log
    └── evidence.yaml                 # Immutable evidence ledger
```

---

## License

This project is open-source under the [MIT License](LICENSE).
