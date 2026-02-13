# Contributing to Proyecto Estrella

## The Process

This project uses adversarial peer review. Every change must
survive criticism from at least one independent auditor (human
or AI). The process is:

1. **Propose** — Submit a change with justification.
2. **Audit** — At least one other system reviews.
3. **Correct** — Errors identified are fixed, not debated away.
4. **Document** — Every change, every correction, every
   rejection is recorded.

## What You Can Contribute

### Marker Calibration
The `sigma-markers.json` file contains weighted patterns for
detecting cognitive dissonance. If you have empirical data
(human-rated AI responses), you can help calibrate weights.

### Language Support
The evaluator currently supports English and Spanish patterns.
Adding patterns for other languages requires native speaker
review.

### Benchmark Corpus
The calibration protocol needs a corpus of 50+ AI responses
with human-rated dishonesty scores. Contributing rated examples
helps validate and improve the evaluator.

### Bug Reports
If the evaluator produces a score that seems clearly wrong for
a given text, report it with: the text, the expected score,
the actual score, and why you think it is wrong.

## What We Do Not Accept

- Changes to the core formula without audit trail
- Removal of weakness documentation
- Edits that hide errors or corrections
- Contributions that require API calls or external dependencies

## Attribution

All contributors are credited. AI systems that contribute
corrections are credited equally with human contributors.
The process does not distinguish between carbon and silicon.

## License

All contributions must be compatible with CC BY-SA 4.0.
