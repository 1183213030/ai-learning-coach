# Learner Profile — Three-View (Ds / Dw / Dr)

*Last updated: YYYY-MM-DD*

> **v3.3.0**: Profile structure absorbed from DeepTutor (HKUDS, arXiv:2604.26962 §2.1.2 Profile Construction). The profile is assembled from **observable trace evidence**, not from learner self-reports. Every weakness entry MUST carry an evidence chain (trace id / probe record); unanchored claims are `INVALID_UNGROUNDED_CLAIM`.

---

## Ds — Session & Context View (会话与背景)

- **Primary Goal / Target Role**: (e.g. 求职前端岗位 / 深度掌握现代前端工程)
- **Baseline / 摸底结论**: (verdict from the initial assessment, with date)
- **Preferred Explanation Style**: (`concrete_first` | `abstract_first`, plus one-line justification)
- **Time Budget / Constraints**: (daily learning time, target date — only if known)
- **Active Learning Tracks**: (pointer to `state/subjects/*` state files + current progress)
- **Recent Session Summary**: (one or two lines per recent session; link to session logs)

---

## Dw — Weakness & Blind-Spot Inventory (弱点清单，证据支撑)

| Weakness | Evidence Chain (trace/probe id) | Status | Last Verified | Planned Target Dimension |
| :--- | :--- | :--- | :--- | :--- |
| (e.g. 混淆 var/let 循环闭包共享语义) | `tr-20261013-s2` probe ADCB failed → repair drill | active | 2026-10-13 | `d4_reference_identity` |

Rules:

- **No evidence, no entry.** Adding a weakness requires at least one L2/L3 trace or failed probe.
- **Status transitions** only via Evidence Engine results: `active → repaired` requires a passing L0 probe on the same dimension.
- **This view drives practice generation** (difficulty calibration and gap targeting in `references/practice-generation.md`).

---

## Dr — Pedagogical Reflection View (教学反思)

- **What worked recently**: (e.g. counterexample contrast on `var` loop beat a 10-minute lecture)
- **What failed recently**: (e.g. abstract rule announced before shock → learner parroted terminology)
- **Calibration notes**: (confidence vs actual performance mismatches, from Evidence Model §4)
- **Next teaching adjustments**: (concrete deltas for the next session, not vague intent)

Rules:

- Dr is **for the coach's next interaction**, not a report card; keep it short and actionable.
- Dr updates AFTER sessions, never mid-session.
