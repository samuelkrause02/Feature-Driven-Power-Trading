# Feature-Driven Power Trading

**Predict-and-optimize strategies for short-term power trading under uncertainty.**

Master's Semester Project at [ETH Zürich, Power Systems Laboratory](https://psl.ee.ethz.ch/), in collaboration with a confidential industry partner (advanced analytics for energy trading).

> The implementation repository and data are private under NDA. This page documents scope and methodology at a conceptual level.

---

## Motivation

Market participants in short-term electricity markets face sequential decisions under uncertainty: prices, renewable infeed, and residual load are only partially observable ex-ante, while positions must be committed ahead of delivery. Traditional *predict-then-optimize* pipelines train forecasters against statistical loss (e.g. MSE) — losses that are **not aligned with trading P&L**.

This project investigates **feature-driven policies** that learn a mapping from contextual features directly to trading decisions, with the downstream optimization objective embedded in the training loss.

## Research Questions

- How do **end-to-end (decision-focused) learning** approaches compare to classical two-stage predict-then-optimize pipelines?
- Can **feature-driven linear policies** recover the performance of stochastic programming with scenario trees at a fraction of the computational cost?
- Under what market regimes (volatility, spread structure, regulatory change) does each approach dominate?

## Methodology

- **Market model:** sequential bidding across day-ahead and intraday stages with closeout at the imbalance price.
- **Policy class:** affine and neural feature-driven policies $\pi_\theta(x) \to q$, mapping features $x$ (forecasts, calendar, residual load, weather) to bid quantities $q$.
- **Training objective:** empirical P&L on historical data, optionally regularized by risk measures (CVaR).
- **Benchmark stack:**
  - Predict-then-optimize with point forecasts
  - Predict-then-optimize with probabilistic forecasts + stochastic programming
  - Bilevel / decision-focused learning (differentiable optimization layers)
  - Feature-driven closed-form linear policies

## Tech Stack

`Python` · `PyTorch` · `cvxpy` / `cvxpylayers` · `Pyomo` · `pandas` · `scikit-learn`

## Status

Active — Spring 2026 at ETH Zürich.

## Contact

**Samuel Krause** · [sakrause@ethz.ch](mailto:sakrause@ethz.ch) · [LinkedIn](https://www.linkedin.com/in/samuel-krause-8b504820b/)
