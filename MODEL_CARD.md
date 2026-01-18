# Model Card: Black-Box Optimisation Strategy

## Overview
Model name: BBO Strategy – GP/NN Hybrid

Type: Sequential Black-Box Optimisation

Version: v1.0

## Intended Use
Designed for tasks involving:
- Expensive or limited queries
- Unknown, non-differentiable objective functions
- Maximisation within bounded, continuous spaces

Inappropriate use cases:
- Real-time control tasks
- Problems requiring interpretability or immediate responsiveness
- Deployment in high-stakes decision-making contexts without further testing

## Details
The optimisation strategy evolved over 13 rounds:
- Early stage focused on exploration using GP with UCB and EI to cover search space broadly.
- Later stage shifted to more exploitative querying based on regions with strong historical performance. Deployed neural networks and ensemble methods for certain functions.
- Hyperparameters like β (UCB), ξ (EI), candidate resolution and noise levels were adjusted weekly.
- Manual interventions were used when model predictions stagnated. Visualisation aided low-dimensional queries.

## Performance
- New maximum values were achieved in 7 of 8 functions, apart from Function 1 possibly due to its sharp local optima nature.
- Metrics were based on relative improvement over seed data and consistency of high-value sampling.
- Performance was assessed by tracking maximum values over time, as ground-truth optima are unknown.

## Assumptions and Limitations
- Assumed moderate smoothness of objective functions, which may not hold for all cases.
- Heavy reliance on GP models with limited hyperparameter tuning may restrict adaptability.
- Manual visual inspection and override introduce subjective bias.

## Ethical Considerations
- Weekly strategy logs and function-level reflections are publicly documented for transparency and reproducibility.
- This work is for academic and instructional use; real-world adaptation would require rigorous validation.
- No sensitive or personal data is used.
