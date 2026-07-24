# Writing Rules — Research

Evidence for writing the rules, instructions, and constraints inside a skill. Read this before drafting any rules so the skill primes the agent well instead of degrading it. The actionable rules derived from this evidence live in `SKILL.md` under **Reference › Rules**.

## Study: "Guardrails Beat Guidance" (Zhang et al., arXiv:2604.11088, 2026)

5,000+ controlled runs of Claude Code (Claude Opus 4.6) on SWE-bench Verified, plus a corpus analysis of 679 rule files (25,532 rules) from GitHub.

**Scope and strength.** All results are for one agent/model on Python bug-fix tasks, and most are _directional, not statistically significant_ (n=35–58). The authors frame them as "scoped empirical findings rather than universal laws." Treat them as priors, not proof.

### Findings

1. **Negative constraints help, positive directives hurt.** In their per-rule ablation, every beneficial rule was a negative constraint ("do not X") and every harmful one a positive directive ("do X"). The only individually significant rule was "do not refactor unrelated code" (~20pp drop when removed). "Follow code style" and "handle edge cases" were among the harmful positive directives.

2. **Content matters less than presence.** Random, shuffled, and wrong-domain rules performed the same as curated rules (all ~+13.8pp). Rules appear to work through context priming, not specific instruction.

3. **Rule count doesn't degrade.** Pass rates stayed stable from 0 to 50 rules; harmful individual rules did not visibly accumulate in ensemble.

4. **State-dependent beats state-independent.** Tool/process rules ("if tests fail, fix the root cause") scored highest; state-independent architecture rules ("use the repository pattern") scored lowest (10.4pp spread, not significant).
