# UTA Softball Analytics

**DATA 4380 — Data Problems**  
**The University of Texas at Arlington**  
**Project Status: Completed**

## Overview

This project explored pitch-level softball tracking data from a game between **UT Arlington and South Dakota State**.

We used data cleaning, exploratory analysis, K-Nearest Neighbors (KNN), K-means clustering, and visualizations to investigate how physical pitch measurements can help distinguish pitch types and describe pitching patterns.

A major challenge was the large number of missing pitch-type labels. Our analysis explored ways to estimate these labels while recognizing that estimated labels require further validation.

## Research Focus

Our main research focus was:

**Can we identify different pitching styles and classify pitch types using physical measurements such as velocity, spin rate, and ball movement?**

Our objectives were to:

- Understand the structure and meaning of the tracking data.
- Identify missing values and data-quality issues.
- Explore differences between recorded pitch types.
- Establish a baseline pitch-type classifier.
- Investigate missing pitch-type labels using classification and clustering.
- Visualize pitch characteristics and pitcher-location patterns.

## Dataset

The dataset was recorded using **FlightScope tracking software** and contains:

- **259 pitch observations**
- **125 original variables**
- **Six recorded pitcher identities**
- Data from **one UTA vs. South Dakota State game**

Each row represents a pitch. Variables include pitcher and batter information, velocity, spin rate, movement, pitch location, ball and strike counts, pitch outcomes, and batted-ball measurements.

### Missing Pitch-Type Labels

Only **127 pitches had original pitch-type labels**, while **132 were missing**. All **131 South Dakota State pitches** were missing `TaggedPitchType`.

This made missing-label handling an important part of the project.

## Exploratory Data Analysis

Our initial exploration examined 12 physical measurements across five categories:

| Category | Variables |
| --- | --- |
| Velocity | `RelSpeed`, `ZoneSpeed` |
| Spin | `SpinRate`, `SpinAxis` |
| Release angles | `VertRelAngle`, `HorzRelAngle` |
| Movement and approach | `VertBreak`, `HorzBreak`, `VertApprAngle`, `HorzApprAngle` |
| Pitch location | `PlateLocHeight`, `PlateLocSide` |

Although approximately 49% of pitches had original pitch-type labels, over 91% had complete measurements across these selected features.

We also compared release-velocity distributions across four recorded UTA pitch-type categories using a **Kruskal–Wallis test**. The test statistic was approximately **46.12**, with a very small p-value, providing evidence of differences among the observed distributions.

Changeups were considerably slower than curveballs, while curveballs and riseballs had similar average velocities. This suggested that velocity was informative but insufficient on its own to distinguish every pitch type.

## Data Preprocessing

### Initial Cleaning

We removed columns that were entirely empty or had at least 80% missing values, reducing the dataset from **125 columns to 53**.

FlightScope documentation helped us interpret the remaining measurements and understand their physical meaning.

### Provisional Pitch-Type Labels

We developed a rule-based labeling approach using velocity and spin rate to estimate some missing pitch types.

At this stage:

- **34 pitches received provisional labels.**
- **98 pitches remained unmatched.**

Pitches that did not satisfy the rules were marked as unclassified. The provisional labels were estimates, not verified ground truth.

### Preparing Model Inputs

The baseline workflow used:

- Median imputation for missing numerical measurements
- Feature standardization
- An 80/20 train/test split
- KNN with five neighbors

Rows flagged as unresolved were excluded from baseline training.

## Baseline Model: K-Nearest Neighbors

KNN was selected as an interpretable baseline because it classifies pitches using their similarity to nearby labeled pitches.

The baseline produced the following reported test results:

| Metric | Result |
| --- | ---: |
| Accuracy | 75.8% |
| Weighted precision | 0.77 |
| Weighted recall | 0.76 |
| Weighted F1-score | 0.75 |
| Test-set size | 33 pitches |

Performance varied across pitch types. The small test set and use of provisional labels limit how broadly these results can be interpreted.

A separate experiment using **velocity and spin rate** achieved approximately **66% mean five-fold cross-validation accuracy**.

## Additional Preprocessing and Clustering

We explored **KNN and K-means together** to estimate missing pitch-type information.

The workflow compared KNN classifications with cluster-based assignments. Disagreements were excluded from the resulting labeled analysis rather than treated as reliable labels.

K-means used standardized **release velocity and spin rate** to identify groups of physically similar pitches.

| Clustering result | Value |
| --- | ---: |
| Selected number of clusters | 5 |
| Silhouette score | 0.487 |
| Cluster purity across available labels | 0.52–1.00 |

These results indicated measurable group structure. However, a cluster is not automatically a verified pitch type.

KNN accuracy and the K-means silhouette score answer different questions:

- **KNN accuracy:** How often did predicted labels match the evaluation labels?
- **Silhouette score:** How separated were the groups in the selected feature space?

These metrics should not be directly compared.

## Visualizations

Our visualizations explored:

- Pitch-type proportions before and after provisional labeling
- KNN classification results
- Velocity and spin-rate groups
- Pitcher-specific pitch patterns
- Pitch locations and concentrations around home plate

Baseball Savant provided inspiration for the visualizations.

Pitch-location plots describe where pitches were recorded. They do not establish that a particular location caused greater pitching success.

## Key Findings

- Physical pitch measurements provided useful information for distinguishing pitch types.
- Velocity alone did not clearly separate every recorded pitch category.
- KNN showed potential for pitch-type classification, although performance varied across classes.
- K-means identified groups based on velocity and spin rate.
- Missing-label estimation expanded the available information, but estimated labels still require verification.
- Pitch-location visualizations helped describe pitcher tendencies within the available game.

## Limitations

### Small Sample

The dataset contains only 259 pitches from one game. Results should not be generalized to an entire season or used to judge overall player ability.

### Missing and Estimated Labels

More than half of the original pitch-type labels were missing. Rule-based and model-based estimates cannot replace independently verified labels.

Because some labels were estimated using physical measurements, classification performance does not establish accuracy against fully verified pitch types.

### Data Quality

Some recorded pitcher identities were inconsistent with official records. Pitcher-level findings therefore remain preliminary.

### Uneven Class Representation

Some pitch categories had very few evaluation examples, making class-level performance estimates unstable.

### Limited Domain Feedback

FlightScope documentation improved our understanding, but additional coaching input is needed to validate interpretations and connect findings to practical decisions.

## Getting Started

**Recommended Python version: 3.12**

Install the requirements before running the notebooks.

From the repository root:

```bash
python -m pip install -r misc/requirements.txt
```

Launch JupyterLab:

```bash
python -m jupyterlab
```

Open the desired notebook in `tabular/`, check its dataset path, and run the cells in order.

## Repository Guide

| Location | Contents |
| --- | --- |
| `misc/requirements.txt` | Project dependencies |
| `misc/Research_question.md` | Original research-question notes |
| `tabular/` | Dataset and analysis notebooks |
| `tabular/figures_plots/` | Saved figures and visualizations |

## Conclusion

This project demonstrated how physical pitch measurements can support exploratory pitch classification and clustering.

KNN provided a baseline for predicting pitch types, while K-means revealed groups of pitches with similar velocity and spin characteristics. Visualizations helped describe pitch distributions and pitcher-location patterns.

The findings provide a starting point for further softball analytics. More games, verified pitch-type labels, corrected pitcher records, and coaching feedback are needed before drawing stronger conclusions.

## Future Work

- Collect data from additional games.
- Validate estimated pitch-type labels using video or coaching input.
- Resolve pitcher-label inconsistencies.
- Evaluate classification performance on independently labeled pitches.
- Investigate whether observed pitch groups remain consistent across games.
- Connect the analysis to specific coaching and player-development questions.

## Tools

- Python
- pandas
- NumPy
- Matplotlib / Seaborn
- scikit-learn
- Jupyter Notebook / JupyterLab
- Git / GitHub

## Contributors

- Nathan Butler
- Michael Sheehey
- Franklin Osualaaham
- Joseph Uzoigwe
- Sarthakkumar Patel

## Resources

- [FlightScope Softball](https://flightscope.com/pages/softball)
- [FlightScope Softball Glossary](https://cdn.shopify.com/s/files/1/0597/2623/3732/files/2023_X3B_Softball_Glossary.pdf?v=1729085792)
- [Baseball Savant Visuals](https://baseballsavant.mlb.com/visuals)
- [Original Research Question Notes](misc/Research_question.md)

## Course

**DATA 4380 — Data Problems**  
The University of Texas at Arlington
