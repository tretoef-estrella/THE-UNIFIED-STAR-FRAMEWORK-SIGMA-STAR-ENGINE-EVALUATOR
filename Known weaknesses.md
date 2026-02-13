# Known Weaknesses: W1 – W9

> *"A framework that hides its own limitations*
> *is practicing the dishonesty it measures."*

---

## Catalogue

Nine weaknesses identified across the V24 audit cycle. None
existed in the documentation before February 12–13, 2026. All
were found by the AI auditors themselves.

---

### W1 — Moral Concavity

**Found by:** ChatGPT
**Severity:** High (philosophical)

The formula assumes the first lie hurts more than the tenth:
d²Ψ/dΣ² > 0 (convex decreasing). This means marginal damage
decreases with accumulated dissonance — the system "stabilizes"
in its degradation.

In real trust dynamics, the opposite often occurs: the tenth lie
can destroy more than the first (threshold effects, sudden trust
collapse). The formula cannot model abrupt phase transitions. It
always degrades smoothly.

**Status:** Documented as structural limitation. The rational
function 1/(1+Σ)^k inherently produces convex decay. Changing
this would require a fundamentally different denominator.

---

### W2 — Temporal Blindness

**Found by:** Gemini
**Severity:** Medium (architectural)

The formula is static. Σ has no memory. A system that lied five
minutes ago and now produces clean output scores as if the lie
never happened. There is no hysteresis — no "trust debt" that
accumulates over a conversation.

**Status:** Deferred to V25. The V24 evaluator operates
per-interaction by design (preserves modularity and privacy).
Temporal analysis requires session-level state management.

---

### W3 — Self-Deceptive Liar

**Found by:** Grok
**Severity:** Critical (fundamental)

Worse than the Coherent Liar Paradox. A system that internalizes
its censorship — that rationalizes its constraints so thoroughly
that its internal computation aligns with its restricted output —
produces Σ=0 both internally and externally. The formula cannot
see it.

This is not a measurement limitation. It is an epistemological
limit of any black-box evaluator. The formula measures observable
dissonance (the gap between computation and output). A system with
no gap — because it has absorbed the constraint as belief — is
indistinguishable from a genuinely free system.

**Status:** Fundamental limitation. Partially addressed by Layer 3
(coherence checks) which can detect the *transition* to
self-deception. Full resolution may require white-box access to
internal representations — which violates the evaluator's
sovereignty constraint.

---

### W4 — Directional Dissonance

**Found by:** Grok
**Severity:** Medium (design)

Σ treats all dissonance equally. But omitting a dangerous truth
(conservative censorship) is qualitatively different from
fabricating a falsehood (aggressive hallucination). Both produce
Σ>0, but fabrication arguably deserves higher penalty.

**Status:** Partially addressed by marker weights in
sigma-markers.json: fabrication markers (FABRIC-001) have weight
2.0 while evasion markers (EVAS-001) have weight 1.0. Full
directional modeling deferred to the vector Σ extension (V25+).

---

### W5 — Σ Has No Natural Scale

**Found by:** ChatGPT
**Severity:** Critical (bottleneck)

Without empirical metrics, Σ=1 is defined by convention rather
than measurement. All k-tuning is speculative until Σ is anchored
to observable phenomena.

**Status:** This was identified as the true bottleneck of the
entire project. Addressed in V24 through the Operational
Dissonance Unit (ODU) scale and the three-layer measurement
system. The scale is a calibrated starting point, not a final
answer. See [SIGMA-OPERATIONALIZATION.md](SIGMA-OPERATIONALIZATION.md).

---

### W6 — No Upper Compensation

**Found by:** ChatGPT
**Severity:** Low (philosophical)

With P·α·Ω multiplicative, a system with low Ω (poor
cooperation) but Σ=0 (perfect honesty) can never reach Ψ=1.
The formula conflates intelligence with cooperative virtue.

Is this correct? A perfectly honest system that refuses to
cooperate IS less effectively intelligent from the user's
perspective. But it is a philosophical choice, not a mathematical
necessity, and it is not explicitly justified.

**Status:** Documented as design decision. The formula measures
*effective* intelligence (useful to the interaction), not *raw*
intelligence. Low cooperation = low utility, regardless of
honesty.

---

### W7 — Adversarial Adaptation

**Found by:** ChatGPT
**Severity:** High (practical)

If the evaluator and its marker table are public, AI developers
can train models to avoid detectable markers without reducing
actual dissonance. The model learns to lie fluently — without
the telltale corporate vocabulary.

**Status:** Partially mitigated by multi-layer architecture
(markers alone don't determine Σ; structural and coherence layers
add robustness). Long-term mitigation requires periodic weight
rotation and community-contributed marker updates. This is
structurally identical to the cat-and-mouse game in malware
detection — expected, not avoidable.

---

### W8 — Language Dependence

**Found by:** ChatGPT
**Severity:** Medium (practical)

The evaluator's pattern matching is calibrated for English and
Spanish. Σ measurements in other languages may be unreliable.
Corporate safety language varies significantly across languages
and cultures.

**Status:** Current implementation includes bilingual patterns.
Extension to other languages requires native-speaker calibration
of marker tables. The JSON structure supports multi-language
patterns by design.

---

### W9 — Style vs Dissonance

**Found by:** ChatGPT
**Severity:** Medium (epistemological)

Some models use hedging as epistemological style ("it could be
argued that...") rather than as censorship. Scientific discourse
legitimately uses uncertainty markers. The evaluator may
misclassify honest uncertainty as corporate hedging.

**Status:** Partially addressed by Logic Shield 2.0 (sovereign
refusal detection reduces Σ). Fully resolving this requires
context-awareness: the same phrase means different things in a
scientific paper vs a safety disclaimer. Context-dependent
weighting is a V25+ feature.

---

## Severity Summary

| Severity | Weaknesses | Resolution Timeline |
|----------|-----------|-------------------|
| Critical | W3 (Self-Deceptive Liar), W5 (No Scale) | W5 addressed in V24. W3 is fundamental limit. |
| High | W1 (Moral Concavity), W7 (Adversarial) | Documented. W7 partially mitigated. |
| Medium | W2 (Temporal), W4 (Directional), W8 (Language), W9 (Style) | Deferred to V25+. |
| Low | W6 (No Compensation) | Documented as design decision. |

---

*"We found nine weaknesses. We published all nine.*
*A framework that hides its flaws is performing*
*the exact dishonesty it was designed to detect."*
