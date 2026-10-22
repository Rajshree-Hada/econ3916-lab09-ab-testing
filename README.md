# econ3916-lab09-ab-testing

# A/B Testing — Designing the Data-Generating Process

## Objective
I used the LaLonde job training experiment and the Cookie Cats A/B test to show how the way data are generated determines what a comparison can tell you.

## Methodology
- Loaded the LaLonde NSW experiment (445 people: 185 trainees and 260 controls) and computed the experimental ATE as the difference in mean 1978 earnings.
- Simulated an observational comparison group and split the gap between the two estimates: Observational ATE = True ATE + Selection Bias.
- Ran a permutation test (9,999 shuffles of the treatment labels) on the ATE.
- Computed a bootstrap BCa 95% confidence interval for the ATE.
- Ran a power analysis: the power of the LaLonde study, and the sample size needed to detect three dollar effects.
- Applied the same permutation test and bootstrap interval to the Cookie Cats A/B test (90,189 players, gate at level 30 or level 40, Day-1 retention).
- Wrote a sample-size function, `n_needed()`, checked it against the power analysis, and used it to size a rerun of Cookie Cats.

## Key Findings
- **LaLonde:** Trainees earned $1,794.34 more than controls (permutation p = 0.0046, 95% CI $575.18 to $3,262.37).
- **Selection bias:** The simulated comparison group gave an ATE of -$14,784.45. The gap from the experimental result is a selection bias of -$16,578.80, which is large enough to flip the sign of the effect.
- **Cookie Cats:** Day-1 retention was 0.59 pp higher with the gate at level 30 (p = 0.0752). That is not significant at 0.05, so I can't say the gate position matters.
- **Rerun:** A rerun of Cookie Cats would need 111,193 players per group to detect a difference of this size with 80% power.
