# UTA Softball Analytics

**DATA 4380 — Data Problems**

This project explores pitch-level softball tracking data from a game between **UT Arlington and South Dakota State**. The project is being developed in collaboration with the UTA softball program, with the broader goal of helping coaches move toward a more data-driven understanding of player performance.

## Project Status

**Current stage:** Data understanding, exploratory analysis, and research question development.

We are currently:

- understanding the structure and meaning of the dataset
- identifying important variables
- investigating missing values and data quality
- exploring pitcher, batter, and team-level patterns
- developing possible machine learning research questions

### Notes

**Franklin — 10/07/2026**

I created a separate file for possible research questions so everyone can contribute ideas before we decide on the final project question.

I have added a few possible questions so far, but **nothing is final**. Everyone should feel free to add questions or directions they think could work with the dataset.

I also suggest that, if possible, we get in contact with one of the coaches. Having a better understanding of what they would like to learn or extract from the data could help us develop a stronger and more useful research question.

**Research Question Notes:** [Possible Research Questions](https://github.com/mikeSheehey/Tabular_Project_DATA4380/blob/main/Research_question.md)

## Dataset

The current dataset contains pitch-level tracking data from a UTA vs. South Dakota State game.

Each row represents a pitch and includes information related to:

- pitcher and batter
- catcher
- pitch velocity
- spin rate
- horizontal and vertical movement
- pitch location
- ball/strike count
- pitch outcome
- batted-ball measurements
- game context

The dataset contains a large number of numerical and categorical features, making feature selection and dimensionality reduction important parts of the exploration.

## Current Research Direction

One idea under consideration is using **Principal Component Analysis (PCA)** to reduce the large number of numerical pitch measurements and explore the major patterns that differentiate pitches and players.

This direction may change as we better understand the dataset and receive more input from the coaching staff.

## Project Workflow

The project follows the DATA 4380 data science workflow:

1. Problem Definition
2. Data Understanding
3. Exploratory Data Analysis
4. Minimum Data Cleaning
5. Train/Test Split
6. Baseline Model
7. Additional Preprocessing
8. Feature Engineering / Feature Selection
9. Model Selection
10. Model Improvement
11. Hyperparameter Tuning
12. Model Evaluation
13. Model Interpretation
14. Findings and Limitations
15. Conclusion

## Important Limitation

The current data represents a limited game sample rather than an entire season.

Because of this, the project will avoid making broad claims about overall player ability or season-long performance. Findings will be interpreted primarily as patterns observed within the available data.

## Tools

- Python
- pandas
- NumPy
- Matplotlib / Seaborn
- scikit-learn
- Jupyter Notebook
- Git / GitHub

Additional tools may be introduced as the project develops.

## Course

**DATA 4380 — Data Problems**  
The University of Texas at Arlington
