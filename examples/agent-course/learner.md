# Learner profile (example)

## Goal
Build a small agent from scratch, and evaluate agents/harnesses well enough
to say whether a change helped — with numbers, not vibes.

## Background
- ~7 years of statistical modeling and ML: CIs, bootstrap, overfitting, leakage — strong.
- Daily Claude Code user; has never written an agent loop by hand.
- Weak: serving systems, GPU programming.

## Time budget
~5 hours/week. Missed weeks are skipped, not made up.

## Style rules (the tutor must follow these)
- Every concept gets a real-shaped sample (a message, a log line, a data row) and a real number before any abstraction.
- Define every symbol on first use.
- Conclusion first, then the reasoning.
- Skip statistics basics; go straight to what is agent-specific.

## Deliverable
A public repo: ~150-line agent + a 15-task eval with pass^k and confidence intervals.

## Mistake log (newest on top)
- 2026-11-15 · context cost · counted new tokens only, forgot full-history resend · not yet fixed
