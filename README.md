# UTA Softball Analytics

**DATA 4380 — Data Problems**

This project explores pitch-level softball tracking data from a game between **UT Arlington and South Dakota State**. The project is being developed in collaboration with the UTA softball program, with the broader goal of helping coaches move toward a more data-driven understanding of player performance.

## Project Status

**Current stage:** Data understanding, exploratory analysis, and research question development.

We are currently:

- learning the structure and meaning of the softball data
- identifying important variables
- investigating missing values and data quality
- exploring pitcher, batter, and team-level patterns
- evaluating possible machine learning research questions
- determining which features and targets are appropriate for modeling

### Notes

**Franklin — October 7, 2026**

I created a separate file for possible research questions so everyone can contribute ideas before we decide on the final project question.

I have added a few possible questions so far, but **nothing is final**. Everyone should feel free to add questions or directions they think could work with the dataset.

**Research Question Notes:** [Possible Research Questions](https://github.com/mikeSheehey/Tabular_Project_DATA4380/blob/main/Research_question.md)

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

The coaching staff is primarily interested in gaining useful information about players and using data more effectively in player evaluation.

Some research directions currently being considered include:

- identifying characteristics that distinguish different pitchers
- developing data-driven pitcher profiles
- examining relationships between pitch characteristics and pitch outcomes
- studying batter responses to different pitch characteristics
- comparing measurable patterns between UTA and South Dakota State

One idea under consideration is using **Principal Component Analysis (PCA)** to reduce the large number of numerical pitch measurements and investigate the major patterns that differentiate pitches and players.

These are exploratory directions and may change as we learn more about the dataset.

## Project Workflow

The project follows the complete data science workflow required for DATA 4380:

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

## Current Tasks

- [ ] Understand important softball terminology
- [ ] Document dataset variables
- [ ] Analyze missing values
- [ ] Identify numerical and categorical features
- [ ] Perform exploratory data analysis
- [ ] Investigate feature relationships
- [ ] Evaluate PCA / dimensionality reduction
- [ ] Select final research question
- [ ] Define target variable and ML task
- [ ] Establish baseline model
- [ ] Compare multiple machine learning models
- [ ] Interpret final model
- [ ] Translate findings into useful coaching insights
- [ ] Prepare final presentation

## Important Limitation

The current data represents a limited game sample rather than an entire season.

Because of this, the project will avoid making broad claims about overall player ability or season-long performance. Findings will be interpreted primarily as patterns observed within the available data.

## Tools

The project will primarily use:

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
