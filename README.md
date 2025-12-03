# EC-Flat50Bench: Adversarial Gradient Erasure Benchmark

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Rob-McCormack/EC-Flat50Bench/blob/main/notebook/EC_Cancellation_Bench.ipynb)

**Status:** Active Research / Null-Model Baseline  
**License:** MIT

## 1. Overview

**EC-Flat50Bench** is a reproducible stochastic baseline designed to quantify **Adversarial Causal Decoupling** in Reinforcement Learning.

It simulates the statistical signature of **Entropy Checkers (EC)**—a deterministic environment where the opponent possesses legal authority to retroactively invert state value post-capture. This repository provides the "Null Model": a tabular Q-learning agent operating against an entropy distribution that mimics the EC game mechanics, demonstrating that standard optimization methods are structurally forced to plateau at random performance.

## 2. Theoretical Premise

**Entropy Checkers** is designed as a counter-example to the Reward Hypothesis in deterministic settings.

- **The Mechanism:** Mandatory capture events trigger a "Board Rewrite" (Mutual Removal or Bilateral Swap) selected by the adversary.
- **The Prediction:** Because the adversary can minimize the realized value of a chosen action $a_t$ _after_ it is taken, the correlation between $a_t$ and $r_{t+1}$ approaches zero.
- **The Metric:** We measure the **Sign-Flip Rate**—the frequency with which a state evaluated as positive ($V>0$) transitions to a negative value ($V<0$) on the immediate next ply.

_(For the full theoretical abstract and arguments regarding Causal 3-Vector Collapse, please see [THEORY.md](THEORY.md))_

## 3. The Benchmark Results

This repository reproduces the empirical pattern predicted for the full EC environment:

| Metric                    | Standard Checkers | EC-Flat50 (This Bench) |
| :------------------------ | :---------------- | :--------------------- |
| **Win-Rate Convergence**  | > 90%             | **50.0% (± 0.06)**     |
| **Adversarial Sign-Flip** | < 2%              | **~35%**               |
| **Learning Gradient**     | Logarithmic       | **Flat / Oscillating** |

### Visual Evidence

The learning curve below illustrates the **Competence Ceiling**. Despite 50,000 episodes of training, the agent fails to extract a policy better than random noise.

![Flat Learning Curve](figures/ec_flat_curve.png)

**Raw Data:** [`data/ec_flat_curve.csv`](data/ec_flat_curve.csv)

## 4. Usage Guide

### Quick Verification (Browser)

Click the **Open In Colab** badge above to run the full training loop in your browser.

### Local Installation

```bash
git clone [https://github.com/Rob-McCormack/EC-Flat50Bench.git](https://github.com/Rob-McCormack/EC-Flat50Bench.git)
cd EC-Flat50Bench
pip install -r requirements.txt
```

### Interpretation

Use this benchmark to calibrate full EC game engines.

- **The Noise Floor:** This benchmark establishes the baseline for "Optimization Failure."
- **Success Criterion:** If a complex agent (e.g., AlphaZero) cannot achieve a win-rate statistically distinguishable from this benchmark ($>55\%$), it indicates the agent is suffering from structural gradient erasure.

## 5\. Research Implications

**Can Optimization Be Defined Here?**
We challenge the community to design an agent that outperforms this null model. We hypothesize that EC represents a class of **"Optimization-Flat"** systems where the objective function is structurally decoupled from the action space. Any "proof" of optimization in this domain likely testifies to the metric's bias rather than the agent's control.

## 6\. Citation

If you use this benchmark in research regarding AI Safety, Goodhart's Law, or RL Robustness, please cite:

```bibtex
@misc{flat50bench2025,
  author = {McCormack, Rob},
  title  = {EC-Flat50Bench: A Benchmark for Adversarial Gradient Erasure},
  year   = {2025},
  url    = {[https://github.com/Rob-McCormack/EC-Flat50Bench](https://github.com/Rob-McCormack/EC-Flat50Bench)}
}
```

## Contact

**Rob McCormack** [rob.a.mccormack@gmail.com](mailto:rob.a.mccormack@gmail.com)
