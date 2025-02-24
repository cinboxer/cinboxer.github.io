---
layout:     post
title:      "Blackjack strategy"
subtitle:   " \"廿一点策略\""
date:       2025-02-23 22:20:00
author:     "Mickle"
header-img: "img/new/HiUCute.jpg"
catalog: true
mathjax: true
tags:
    - math
    - statistics
    - dynamic
    - poker
---

# Blackjack Strategy

## 1. Basic Strategy Calculation
### 1.1. Expected Value (EV) for Each Action
The optimal strategy is derived by calculating the **Expected Value (EV)** for each possible action (Hit, Stand, Double, Split, Surrender) based on the player's hand and the dealer's upcard.

- **Formula**:

  $$
  EV = \sum \Big( P_{\text{outcome}} \times \text{Payoff}_{\text{outcome}} \Big)
  $$
  - $P_{\text{outcome}}$: Probability of a specific outcome (e.g., win, lose, push).
  - $\text{Payoff}_{\text{outcome}}$: Payout for the outcome (e.g., 1:1, 3:2 for Blackjack).

### 1.2. Probability Calculation
- **Dealer's Final Hand Probability**:  
  Use combinatorial analysis to calculate the probability of the dealer busting or reaching specific totals (17–21) based on their upcard.  
  - *Example*: Dealer upcard = 6. Probability of busting ≈ **42.315%**.

- **Player's Hand Probability**:  
  Calculate the probability of improving a hand (e.g., hitting 12 vs. dealer 2).

### 1.3. Decision Matrix
Construct a matrix comparing the EV of all actions:

| Player Hand (Hard) | Dealer Upcard | EV(Hit) | EV(Stand) | EV(Double) | Optimal Action |
|--------------------|---------------|---------|-----------|------------|----------------|
| 16                 | 7             | -0.41   | -0.48     | -0.83      | **Stand**      |

---

## 2. Card Counting Systems
### 2.1. High-Low System
- **Card Values**:

  | Card Range      | Weight |
  |-----------------|--------|
  | 2–6             | +1     |
  | 7–9             | 0      |
  | 10, J, Q, K, A  | -1     |

- **Running Count (RC)**:
  
  $$
  RC = \sum \Big( \text{Weight of each card seen} \Big)
  $$

- **True Count (TC)**:
  
  $$
  TC = \frac{RC}{\text{Decks Remaining}}
  $$

### 2.2. True Count → Player Edge
- **Conversion Table**:

  | True Count | Player Edge (%)         |
  |------------|-------------------------|
  | $\leq 0$       | -0.5% (House Edge)      |
  | $+3$       | +1.5%                   |

---

## 3. Bet Sizing Using the Kelly Criterion
### 3.1. Kelly Formula
$$
f = \frac{EV}{b}
$$
- $f$: Fraction of bankroll to bet.
- $b$: Net odds received on the wager (for a 1:1 payout, $b = 1$).

### 3.2. Practical Adjustments
- **Full Kelly**: Aggressive (high risk).
- **Fractional Kelly**: 
  $$
  f_{\text{adjusted}} = \frac{f}{2}
  $$
  (common for risk management).

### 3.3. Example Calculation
- **Player Edge** = 1.5%, $b = 1$:
  $$
  f = \frac{0.015}{1} = 1.5\% \quad \Rightarrow \quad \text{Bet 1.5\% of bankroll}.
  $$

---

## 4. Risk Management
### 4.1. Bankroll Requirements
- **Formula**:
  $$
  \text{Minimum Bankroll} = \frac{\text{Max Expected Loss}}{\text{Risk of Ruin}}
  $$
  - *Example*: To withstand a 10% Risk of Ruin, the bankroll must be at least 40× the max bet.

### 4.2. Stop-Loss Limits
- Set daily loss limits (e.g., 50% of the session bankroll).

---

## 5. Dynamic Strategy Adjustments
### 5.1. True Count-Based Modifications
| True Count         | Strategy Adjustment                                 |
|--------------------|-----------------------------------------------------|
| **TC ≥ +3**      | Double down on 9 vs. 2–6; Split 10s vs. 5–6.           |
| **TC ≤ -1**      | Avoid splitting pairs; Surrender 16 vs. 9.             |

### 5.2. Rule Variations Impact
- **Dealer Hits Soft 17**: Increases house edge by 0.2%.
- **Double After Split**: Adds ≈0.15% to player edge.

Normal Strategy and Strategy when our edge is 2.96%:

| Normal Strategy                                     | New Strategy                                     |
|-----------------------------------------------------|--------------------------------------------------|
| ![Normal Strategy](/img/in-post-new/BJ_strategy1.jpg) | ![New Strategy](/img/in-post-new/BJ_strategy2.jpg) |

---

## 6. Development & Validation
### 6.1. Monte Carlo Simulation
Run millions of virtual hands to validate strategy profitability under different conditions.

- Track results in real sessions and adjust for deviations (e.g., bet spread, TC rounding).

### 6.2. Reinforcement Learning
Due to the complex state-action space (even other players' choices influence the dealer!), reinforcement learning (RL) can optimize Blackjack strategy by learning optimal actions through trial and reward feedback in a simulated environment.

---

## Conclusion
1. **Basic Strategy**: Foundation based on EV maximization.
2. **Card Counting**: Track TC to quantify player edge.
3. **Bet Sizing**: Use the Kelly Criterion for optimal growth.
4. **Risk Management**: Protect bankroll with stop-loss limits.
5. **Adaptation**: Adjust for rules and TC fluctuations.
