# Datasheet: Black-Box Optimisation Capstone Dataset

## Motivation
This dataset was created for the black-box optimisation capstone challenge. The task is to maximise unknown objective functions under a strict query budget. The dataset records all submitted queries and resulting function evaluations, supporting the development and testing of optimisation strategies in limited-feedback settings.

## Composition
The dataset includes evaluations for eight synthetic black-box functions, each inspired by real-world scenarios.
- Input dimensionality ranges from 2 to 8 depending on the function.
- All input values are scaled to the range [0, 1]. Output is a single continuous value.
- There are no missing or invalid values.
- Each function has up to 13 entries in addition to the initial seed data.

## Collection Process
Queries were submitted weekly across 13 rounds. Each round generated one new input-output pair per function.
- Query strategies evolved over time from exploratory to exploitative.
- Primarily used Gaussian Process (GP) models with acquisition functions (UCB, EI). Also incorporated other tools such as neural networks and ensemble methods for certain functions.
- Sampling decisions were based on the full accumulated dataset each week, sometimes supported by visual inspection and manual overrides. 

## Preprocessing and Uses
No transformations were applied to the dataset; all input features are pre-scaled to [0, 1] and free from missing data.

Intended use:
- Benchmarking black-box optimisation strategies
- Educational or research use in constrained-query environment

Not suitable for:
- Real-world deployment or operational decision-making without additional validation

## Distribution and Maintenance
- Maintained by the project author.
- Will be publicly available in this repository by January 2026.
- No updates planned beyond this project unless used for future study.
