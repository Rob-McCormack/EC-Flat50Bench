# Structural Gradient Erasure: Theoretical Foundations

## 1. Abstract

Deep Reinforcement Learning (DRL) relies on the premise that environmental feedback provides a stable gradient for policy improvement. We challenge this by introducing **Entropy Checkers (EC)**, a deterministic environment designed to demonstrate **Adversarial Causal Decoupling**.

In EC, mandatory capture events trigger a "Board Rewrite," granting the adversary legal control to retroactively invalidate the strategic context of the move. This introduces a negative feedback loop: tactical success (material gain) authorizes the adversary to destroy strategic utility.

We verify this phenomenon using a **Multi-Armed Bandit (MAB) Reduction**, demonstrating that standard Q-learning agents flatline at random performance (~50%) even in a simplified state space, provided the reward signal is subject to adversarial inversion.

## 2. The Causal 3-Vector

In standard games (Chess, Go), a move has a scalar payoff (e.g., $+1$). In EC, a capture exists as a **3-Vector** of mutually exclusive deterministic futures:

$$
\text{Credit}(a_t) = \begin{bmatrix}
\text{Play On} \\
\text{Removal} \\
\text{Swap}
\end{bmatrix}
\approx
\begin{bmatrix}
+1.0 \\
+0.1 \\
-1.0
\end{bmatrix}
$$

Immediately after the action $a_t$, the adversary (or the environment structure) collapses this vector to a single component $r_{t+1}$. Because the adversary rationally selects the minimum value, the realized reward is systematically decoupled from the action's intended utility.

## 3. The Reduction Argument (MDP $\to$ MAB)

To rigorously isolate the "Reward Inversion" mechanism from the noise of spatial complexity, we reduce the full game (a Markov Decision Process) to a **Multi-Armed Bandit (MAB)** problem.

**The Logic of the Lower Bound:**

- **Lemma 1:** A Multi-Armed Bandit is a single-state MDP.
- **Lemma 2:** If an optimization algorithm cannot identify the optimal arm in a single-state MDP due to reward inversion, it cannot identify the optimal policy in a multi-state MDP ($10^{20}$ states) under the same inversion conditions.
- **Conclusion:** The failure of Q-learning in the EC-Flat50 Bandit Benchmark constitutes a **sufficient condition** to prove the unlearnability of the full game under standard RL assumptions.

## 4. Methodology: The "Strategic Proxy"

In our benchmark, we model the outcome of the "Bilateral Swap" as a negative reward ($-1.0$).

**Justification:**
A naive material evaluation would treat a Swap as neutral ($\Delta \text{Material} = 0$). However, in the full game, a rational adversary only chooses Swap when it creates a positional disadvantage for the attacker. Therefore, assigning a neutral reward to Swap would fundamentally misrepresent the adversarial nature of the transition.

We use **Strategic Proxy Scoring**:

- **Play On ($+1$):** Models the retention of advantage.
- **Swap ($-1$):** Models the adversarial inversion of advantage (Goodhart's Law).

This allows us to test whether an agent can optimize for survival when the environment actively selects the negative outcome. The empirical result (50% flatline) confirms that standard agents cannot overcome this structural inversion.

## 5. The Determinism Paradox

EC is fully deterministic, yet produces behavior indistinguishable from random outcomes. This reveals that **determinism $\neq$ learnability**.

Traditional assumptions hold that deterministic environments support stable learning gradients, while randomness introduces noise. EC demonstrates:

- **Structural adversariality** can erase gradients in deterministic systems.
- The failure is not due to stochastic transitions, but to **adversarial branch selection**.
- This creates a new class of problems: **Deterministic but Optimization-Resistant Environments**.

## 6. EC as an Instantiation of Goodhart's Law

Goodhart's Law states: _"When a measure becomes a target, it ceases to be a good measure."_

In EC, this is not an emergent phenomenon but a rule-based guarantee:

- **Measure:** Material advantage.
- **Target:** Capturing pieces.
- **Outcome:** When the agent optimizes for the target (Captures), the opponent uses the capture mechanism to invert the advantage (Swap).

This creates a formal, deterministic model of metric corruption where the corruption is intrinsic to the physics of the game.

## 7. Implications for AI

1. **AI Safety:** EC demonstrates environments where optimization becomes self-defeating.
2. **Reinforcement Learning:** It challenges the Reward Hypothesis in adversarial settings.
3. **Intelligence Theory:** It suggests that true intelligence requires the meta-cognitive ability to recognize when optimization is futile—a capability current AI lacks.
