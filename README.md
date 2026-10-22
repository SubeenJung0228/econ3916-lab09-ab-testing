# A/B Testing — Designing the Data-Generating Process

## Objective
I estimated causal effects from two randomized experiments and checked how random assignment, sample size, and test design decide whether an estimate can be trusted.

## Methodology
- Loaded the LaLonde NSW job training experiment, with 445 people: 185 trainees and 260 controls, and computed the experimental ATE as the difference in mean 1978 earnings.
- Simulated an observational comparison group to show what happens without random assignment, and split the gap into its parts: Observational ATE = True ATE + Selection Bias.
- Ran a permutation test with 9,999 shuffles of the treatment labels to check whether the ATE could be due to chance, without assuming any shape for the earnings distribution.
- Computed a bootstrap BCa 95% confidence interval to show how large the ATE plausibly is.
- Ran a power analysis to find the power of this study and the sample size needed to detect three different dollar effects.
- Applied the same tests to the Cookie Cats mobile game A/B test, with 90,189 players, comparing Day-1 retention when the first gate is at level 30 or level 40.
- Wrote a sample-size function, n_needed(), checked it against the power analysis, and used it to find how many players a rerun of Cookie Cats would need.

## Key Findings
- **Job training effect:** Trainees earned $1,794.34 more than the control group (permutation p = 0.0046), with a 95% confidence interval from $575.18 to $3,262.37. The effect is unlikely to be chance, but its size is uncertain.
- **Selection bias:** The simulated observational comparison group gave an ATE of −$14,784.45, which would wrongly suggest that the training lowered earnings. The trainees were compared with a group that was very different to begin with, which shows why random assignment matters.
- **Cookie Cats:** Players with the gate at level 30 had a Day-1 retention rate 0.59 percentage points higher than at level 40, but the difference was not significant (p = 0.0752), so there is no strong evidence that moving the gate changes retention.
- **Planning a rerun:** To detect a difference that small with 80% power, a rerun would need 111,192 players per group, which shows how quickly the required sample grows as the effect gets smaller.
