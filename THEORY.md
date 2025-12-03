# Structural Gradient Erasure in Deterministic Environments: The Entropy Checkers Benchmark

## Abstract

Deep Reinforcement Learning (DRL) relies on the fundamental premise that environmental feedback provides a stable gradient for policy improvement. In standard deterministic perfect-information games (e.g., Chess, Go), this premise holds: local tactical advantages generally propagate into global strategic utility. We challenge this assumption by introducing **Entropy Checkers (EC)**, a minimal deterministic environment designed to demonstrate **Adversarial Causal Decoupling**.

In EC, mandatory capture events trigger a "Board Rewrite" phase, granting the disadvantaged agent immediate legal control over the resulting state topology. This mechanism introduces a negative feedback loop where tactical success (material gain) authorizes the adversary to invalidate the strategic context of that success. Consequently, the environment exhibits **Gradient Erasure**: the correlation between action quality and expected return is structurally suppressed, not by stochastic noise, but by adversarial cancellation.

We present theoretical arguments that EC creates a "Causal 3-Vector" collapse, rendering standard temporal credit assignment intractable. Empirical validation using tabular Q-learning on the _EC-Flat50_ benchmark confirms this hypothesis, revealing a "Competence Ceiling" indistinguishable from random noise (win rate $\approx$ 50%) and a **Sign-Flip Rate of ~35%**, where positive state evaluations are inverted on the immediate next ply.

These findings suggest that "intelligence"—defined as optimization capability—is brittle in environments where the causal link between action and consequence is subject to adversarial veto. EC serves as a diagnostic tool for **Optimization-Robustness**, distinguishing between agents that solve static puzzles and those capable of recognizing when an objective function has become structurally decoupled from reality.
