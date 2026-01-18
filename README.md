# AI & Machine Learning Capstone Project

Welcome to the capstone project for my AI & Machine Learning course. This project is a culmination of the concepts and techniques learned throughout the course.

📌 Project Overview
---
This project involves optimising eight unknown black-box functions (from 2D to 8D) under strict query constraints. The functions represent diverse, real-world inspired tasks – from contamination detection to chemical process optimisation. The true nature of each function is hidden, and only limited input–output data is available at the start.

Each week, we are allowed to submit one new input query for each function, and receive the corresponding output after evaluation. The challenge is to design a strategy that progressively identifies the inputs that maximise each function’s output value, using a mix of data-driven modelling, intelligent sampling, and adaptable heuristics.

This project reflects many real-world applications in machine learning and operations research, where optimisation must happen under uncertainty and cost constraints. As someone aiming to apply AI in financial markets, this challenge deepens my practical skills in model-based decision-making and experimental design.

📊 Inputs and Outputs
---
Each function has:
- Initial inputs: A small set of evaluated samples (e.g., 10 x 2 array for the 2D function, 40 x 8 array for the 8D function)
- Initial outputs: Corresponding scalar outputs for each input sample

Every week, the model submits one query input in the form of [x1, x2, ..., xd], where d is the number of input dimensions for that function. The goal is to identify the query that leads to the highest output over 12 total iterations (weeks). Input dimensions range from 2D to 8D depending on the function. Example:

```
Input: [0.854811-0.493965-0.735310-0.808092]
Output: -23.139428
```

All functions are maximisation problems with different landscapes (e.g., smooth, noisy, high-dimensional, or multi-modal).

🎯 Objectives
---
The objective is to maximise each black-box function using only 12 queries per function. We must:
- Work with limited initial data and no knowledge of the function structure
- Deal with high-dimensional functions where visual intuition fails
- Rely on intelligent query selection, without access to gradients
- Adapt strategies as new output values are revealed weekly

This setting simulates high-cost real-world experiments (e.g., lab testing, A/B trials), where intelligent query selection is essential.

🧠 Technical Approach
---

💡 Weekly Summary
---
*Week 1* <br /> 
The priority was exploration, given the small number of initial samples. I used Gaussian Process (GP) models to approximate each function and selected new queries using primarily UCB (Upper Confidence Bound) with a high exploration parameter (β = 4–8). In low-dimensional cases (Functions 1–3), I used heatmaps or simple visualisation tools to identify meaningful regions, and introduced specific twist such as low-value toggle on certain inputs. In higher-dimensional cases (Functions 4–8), where patterns were unclear, I applied consistent exploratory settings across the board to collect more informative data early on.

*Week 2* <br />
Strategies evolved based on early feedback. For functions where a promising result emerged, I began tuning UCB parameters to steer toward more informed exploration or light exploitation. For example, I reduced β to narrow sampling around high-performing areas. In Function 3, I continued testing a hypothesis that lower values of x3 led to better results, and toggled parameters accordingly. Some functions showed suggestive patterns (e.g., ridges or basins), prompting slight grid resolution increases or targeted candidate generation.

*Week 3* <br />
I started to introduce more differentiated strategies per function. For Function 5 and 7, where early maximums were found, I favoured exploitation, reducing β and increasing sampling precision. For Function 6, I began probing feature importance (e.g., high x4 and low x5) based on stable output trends. For other functions (e.g., Function 1), I preserved exploratory intent by adding distance penalties to prevent convergence around existing points too early. Surrogate model remained GP across all functions. Other tools (e.g., SVM for dead zone classification) were considered but not yet applied due to limited data.

*Week 4* <br />
The strategy this week aims to balance model stability with careful exploratory nudging. For functions with consistently strong results, I moved further into targeted exploitation, whereas functions with more ambiguity or complexity remain in controlled exploratory mode. Key adjustments include tweaking resolution, EPS, and alpha to refine model sensitivity and avoid convergence traps.

*Week 5* <br />
This week, I noticed multiple functions producing similar results across rounds. To shake up this stagnation, I tried more out-of-the-box tactics—pushing exploration harder (e.g., higher beta in Function 5) and testing new surrogate models (e.g., neural network in Function 8). The balance between refinement and diversification is now my key focus.

*Week 6* <br />
After attaining three new maximums in Week 5, I continue refining the overall strategy with moderate parameter tuning. While some functions (4, 6, 7) are now transitioning into exploitation, others (1, 2, 5) maintain exploratory bias. Neural networks remain under evaluation in high-dimensional cases, now with reduced aggressiveness to prevent overfitting. This measured approach helps strengthen understanding while cautiously optimising performance.

*Week 7* <br />
With only one new maximum in Week 6, I began shifting towards controlled exploitation, especially for functions with established peaks. That said, exploration remains active where signals are weak or outputs flatline. Neural networks continue on Function 8, though their consistency is being reassessed. I aim to refine local optima without prematurely locking in on suboptimal zones.

*Week 8* <br />
After securing two new maxima last week, I continue to tilt towards exploitation while making thoughtful modifications. I introduced manual exclusion zones to push exploration for Function 1 and began testing an ensemble neural network method for Function 8 to improve robustness over previous standalone NN runs.

*Week 9* <br />
Overall a decent set of results with two new maximums. The shift towards more exploitative strategies has been effective in refining promising areas. For Week 9, I retained most hyperparameters or made them more exploitative to continue extracting gains from high-performing regions.

*Week 10* <br />
Last week was unremarkable with no new maxima achieved. For Week 10, I focus on hyperparameter refinement while staying in exploitation mode. I also stop using experimental models like ensemble NNs, shifting back to more stable methods to maximise gains in the final stretch of the project.

*Week 11* <br />

*Week 12* <br />

*Week 13* <br />

🧪 Tools
---

🧾 Documentation
---
[Datasheet](./DATASHEET.md)  
[Model Card](./MODEL_CARD.md)

