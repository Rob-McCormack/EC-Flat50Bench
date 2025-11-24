# EC-Flat50Bench: The "Null Model" Benchmark

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Rob-McCormack/EC-Flat50Bench/blob/main/notebook/EC_Cancellation_Bench.ipynb)

A reproducible **null-hypothesis benchmark** demonstrating the statistical signature of **Entropy Checkers (EC)**: a deterministic 8×8 game where tabular Q-learning is structurally forced to plateau at a 50% win-rate.

## The Premise: Why This Exists

**Entropy Checkers** is a theoretical variant of checkers designed to break reinforcement learning.

- **The Rules:** Standard checkers, but after **any capture**, the loser chooses a board rewrite (Mutual Removal or Bilateral Swap).
- **The Prediction:** Because the opponent can retroactively invert the value of a move (the "35% Sign-Flip Rate"), no stable learning gradient exists.

## The Benchmark

This repository contains the **Canonical Failure Mode** implementation. It is a simplified **null-model** (randomized reward baseline) that reproduces the exact empirical pattern predicted for the full game:

1.  **Flat win-rate ≈ 0.50 ± 0.06** – No upward trend after 50k episodes.
2.  **35% Adversarial Sign-Flip Rate** – The "noise floor" of the system.

**Use this benchmark to calibrate full EC engines.** If your complex agent cannot statistically distinguish itself from this null model, it has hit the **Competence Ceiling**.

## Quick Start

1.  Click the badge above → **Run All**.
2.  Observe that the learning curve flatlines exactly as predicted by the "Adversarial Cancellation" theory.
3.  **Data**: `data/ec_flat_curve.csv` (50,000 episodes).

## Empirical Evidence

_Figure 1: The "Dead Signal." This flatline represents the maximum possible performance in an environment where causal history is adversarially severed._

![Flat Learning Curve](figures/ec_flat_curve.png)

**CSV:** [ec_flat_curve.csv](data/ec_flat_curve.csv) – (50,000 episodes of flatline convergence).

## Cite This Work

```bibtex
@misc{flat50bench2025,
  author = {McCormack, Rob},
  title  = {EC-Flat50Bench: A Null-Model Benchmark for Adversarial Sign-Flip},
  year   = {2025},
  url    = {https://github.com/Rob-McCormack/EC-Flat50Bench}
}
```

## License

MIT – feel free to fork, cite, or embed.

## Contact

[rob.a.mccormack@gmail.com](mailto:rob.a.mccormack@gmail.com)

---
