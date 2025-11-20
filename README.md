# EC-Flat50Bench  
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Rob-McCormack/EC-Flat50Bench/blob/main/notebook/EC_Cancellation_Bench.ipynb)

Deterministic 8×8 checkers where tabular Q-learning plateaus at 50 % win-rate and 35 % of winning captures are legally inverted on the next ply—a reproducible benchmark for adversarial-cancellation research.

## Rules (30-second version)
Standard 8×8 checkers **plus one rule**:
> After **any capture**, the player who **lost** the piece must **choose one** of these **legal board rewrites**:
> 1. **Play On** – continue normally  
> 2. **Mutual Removal** – each side removes one opposing piece (attacker first)  
> 3. **Bilateral Swap** – swap one of your pieces with one of theirs (no swap onto rows 1 or 8)

That’s it—**no randomness, no hidden info, no larger board**.

## Quick Start
1. Click the badge above → **Run All** → watch the flat learning curve and download the CSV.
2. **Data**: `data/ec_flat_curve.csv` (50,000 episodes, 35 % sign-flip rate).
3. **Notebook**: `notebook/EC_Cancellation_Bench.ipynb` (pure Python, no compiled deps).

## What You Get
- **Flat win-rate ≈ 0.50 ± 0.06** – no statistically significant slope (p > 0.05).  
- **35 % adversarial sign-flip rate** – measured across 50,000 tabular-Q self-play episodes.  
- **External validation**: Gemini 3 review confirms “flat at 50 % is the smoking gun that the gradient is mathematically zero.”

## Cite This Work
```bibtex
@misc{flat50bench2025,
  author = {McCormack, Rob},
  title  = {EC-Flat50Bench: A 35 % Adversarial Sign-Flip Benchmark},
  year   = {2025},
  url    = {https://github.com/Rob-McCormack/EC-Flat50Bench}
}
```

## License
MIT – feel free to fork, cite, or embed.

## Contact
[rob.a.mccormack@gmail.com](mailto:rob.a.mccormack@gmail.com)
