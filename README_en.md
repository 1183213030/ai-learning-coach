<div align="center">

# AI Learning Coach

### A Knowledge-Driven, Evidence-Based Personal Learning Operating System

Let the user focus purely on learning; let the AI Learning Coach handle the rest.

[![Protocol Version](https://img.shields.io/badge/Protocol-v2.2.0-007ACC?style=flat-square)](#)
[![Interaction](https://img.shields.io/badge/Interaction-Zero--Command%20Natural%20Language-4EBA6F?style=flat-square)](#)
[![Verification](https://img.shields.io/badge/Verification-Type--Specific%20Evidence-orange?style=flat-square)](#)
[![Architecture](https://img.shields.io/badge/Architecture-Six--Tier%20Knowledge%20Plane-blueviolet?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)](#)

[简体中文](README.md) • [English](README_en.md)

</div>

---

## Overview

In the era of modern AI coding assistants, obtaining working code and instant answers has become trivial. However, **building durable personal engineering capabilities has become harder than ever**.

### Two Pervasive Pitfalls in AI Learning
1. **The Illusion of Competence**: Reading an AI explanation or copying working code gives the sensation of mastery. But when confronted with a blank file, intricate runtime concurrency, or an unexpected production outage, the developer gets stuck.
2. **Fragmentation & Ad-hoc Knowledge**: Asking AI sporadic questions about configs or errors leaves isolated fragments. No structured mental lattice ever forms.

**AI Learning Coach** flips the script on passive answer-dumping and static online courses. It transforms AI into a **long-term cognitive coach, strict examiner, and dynamic curriculum engine** that adapts to the learner's real-world constraints.

---

## Core Philosophy

> **Learner state decides what to learn right now; objective evidence proves whether it is mastered.**

- **Global Perspective, Zero Fragmentation**: Before diving into isolated details, the coach constructs an authoritative **prerequisite capability tree (Roadmap)**, establishing an unshakeable foundation step-by-step.
- **Socratic Guidance, Zero Spoon-Feeding**: When encountering difficult mechanics, the coach withholds walls of text. It uses physical metaphors, observable contradictions, and micro-predictions to help you deduce the mechanism yourself.
- **Closed-Book Verification, Zero Fake Mastery**: Saying "I understand" yields zero evidence points. The coach strictly decouples **Teaching** from **Testing**. During verification, hints and solutions are withheld; only unassisted explanations, predictions, or implementations unlock true mastery.
- **Learner Reality over Curriculum Progress**: Real humans experience fatigue, tight time limits, and sudden work interruptions. The coach yields static syllabi to your immediate reality.
- **Zero-Command Natural Language**: No complex CLI flags or config syntax to memorize. Speak naturally as you would with a human mentor.

---

## Natural Language Interface

You communicate purely through natural conversation:

```text
┌────────────────────────────────────────────────────────┐
│                                                        │
│  "I want to systematically master frontend engineering" │
│  "Teach me JS async concurrency; I only know await"    │
│  -> Initiates a new domain with light diagnostic       │
│                                                        │
│  "Continue learning"                                   │
│  -> Seamlessly resumes the unclosed frontier           │
│                                                        │
│  "Exhausted today, only have 15 minutes"               │
│  -> Halts new chapters; downgrades to targeted drill   │
│                                                        │
│  "I don't understand closures, teach me from zero"     │
│  "That was too abstract, explain with an analogy"      │
│  "Quiz me on what we just covered, zero hints"         │
│  "Pause the book, I hit a CORS bug in my real project" │
│  -> Targeted clarity, pedagogical pivot, or real work  │
│                                                        │
└────────────────────────────────────────────────────────┘
```

---

## Six-Tier Architecture

Beneath the minimalist conversation interface lies an uncompromising six-tier system:

```text
┌─────────────────────────────────────────────────────────────────┐
│ Layer 1: Learner Profile (Baselines, blind spots, preferences)  │
├─────────────────────────────────────────────────────────────────┤
│ Layer 2: Knowledge Ingress (Multi-source ingestion S0 to S5)    │
│   [Local Library Priority library/]  [Official Specs]  [Git Diff]│
├─────────────────────────────────────────────────────────────────┤
│ Layer 3: Knowledge Map & Topology (Capability trees & graphs)   │
├─────────────────────────────────────────────────────────────────┤
│ Layer 4: Adaptive Curriculum Engine (Single-lesson dynamic growth)│
├─────────────────────────────────────────────────────────────────┤
│ Layer 5: Teaching Engine (MCE explanations, 4-way pivots)       │
├─────────────────────────────────────────────────────────────────┤
│ Layer 6: Evidence & Review (Type-specific proof, spaced retention)│
└─────────────────────────────────────────────────────────────────┘
```

### 1. Source Ranking (S0 to S5)
- **S0 (Official Specs)**: ECMAScript, W3C, MDN, Vue/React/Node.js Official Handbooks.
- **S1 (Canonical Literature)**: Ingested local textbooks (`library/`), classic engineering literature.
- **S2 to S4**: Vetted courses, high-reputation engineering blogs, community articles.
- **S5 (AI Memory)**: Parametric model memory (must be cross-referenced with S0/S1; never substitute AI metaphors for standard facts).

### 2. Local-First Library Ingestion
Store your own Markdown notes, e-books, or documentation under `library/<domain>/` (e.g. `library/frontend/`). The coach parses your local materials as the primary curriculum spine before searching external resources.

### 3. Objective Evidence Over Scores
The coach rejects arbitrary percentage metrics (e.g. "Score: 85%"). Capabilities are proven through decoupled dimensions:
- **AI Intervention Level**: Zero assistance (`L0`) vs. guided scaffolding (`L1 to L3`). AI-authored code awards 0% independent mastery credit.
- **Evidence Dimensions**: Mechanism explanation (`E1`), runtime simulation (`E2`), debugging (`E3`), independent implementation (`E4`), cross-domain transfer (`E5`).
- **Domain-Specific Verification**: Conceptual models require counter-case defense; runtime requires execution tracing; testing requires boundary matrix derivation; architecture requires 7-step trade-off analysis.
- **Reversible State Machine**: `UNKNOWN -> EXPOSED -> GUIDED -> INDEPENDENT -> TRANSFERABLE -> DURABLE`. Failures in subsequent complex tasks trigger real regression.

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
├── SKILL.md                          # Core protocol & arbitration laws
├── README.md                         # Chinese Documentation
├── README_en.md                      # English Documentation
│
├── knowledge/                        # Evolving Knowledge Registry
│   ├── frontend/                     # JavaScript, browser, and runtime concepts
│   └── software-testing/             # Software testing methodology and standards
│
├── library/                          # Local Textbook Library (Local-First Priority)
│   ├── frontend/                     # Ingested frontend literature
│   └── software-testing/             # Ingested testing handbooks
│
├── references/                       # Operational specifications (Progressive Disclosure)
│   ├── intent-router.md              # Zero-command natural language routing & Teach vs Check
│   ├── teaching-protocol.md          # Teacher persona, 4-way pivots, and micro-probes
│   ├── curriculum-engine.md          # Learner-state-over-curriculum arbitration
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
