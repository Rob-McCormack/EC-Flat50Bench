# About Entropy Checkers (EC)

## 1. What EC really is

Entropy Checkers is, at heart, a **children’s game**.

- The rules are just a tiny twist on normal checkers.

- No hidden randomness, no giant search tree on the board.

- A highschool student could have invented it.

The benchmark in this repo doesn’t even simulate the full 8×8 game. Instead, it uses about **100 lines of Python** to **abstract the key idea**:

> Sometimes a capture helps you, sometimes it hurts you, depending on how your opponent is allowed to respond.

On top of that, we put a **very simple learning agent**—basic tabular Q-learning, like you’d see in an introductory RL example.

**So EC + `EC-Flat50Bench` are:**

1. a **simple game** with **simple rules**,
1. a **simple abstraction** of that game in ~100 lines of code, and
1. a **simple learner** trying to figure out whether it should capture or not.

The surprising part is **not** that the code is clever, or that the model is **large** - it’s that **even in this tiny, clean setup, learning gets stuck at ~50%** for structural reasons, **not because the game or the algorithm are complicated**.

---

## 2. How this connects to the main repository

- The full rules and motivation are in [README.md](README.md).

- The formal treatment (Causal 3-Vectors, structural gradient erasure) is in [THEORY.md](THEORY.md).

`EC-Flat50Bench` is the small Python benchmark that shows the 50% flatline.

If you only remember one sentence, remember this:

> **EC is a child-simple game that needs only ~100 lines of Python and a toy learner to show how optimization can quietly lose its meaning.**

---

~ by Rob McCormack, December 2025
