Predictive Modeling of Gaming Ballot Voter Behavior
This project analyzes a dataset of county-level demographics and economic data to predict the outcome of a gaming (gambling) ballot initiative. The goal is to build and evaluate several machine learning classification models to determine which factors most accurately predict a "Yes" vote and to provide actionable insights for campaign targeting.

This project was completed as part of an academic assignment, demonstrating an end-to-end data science workflow from data cleaning to model interpretation.

Project Workflow
Data Cleaning & Preparation:

Loaded the dataset and identified a flawed column (PERCENT CHURCH MEMBERS OF POPULATION).

Corrected the flawed data by recalculating the percentage from the raw NO OF CHURCH MEMBERS and POPULATION columns.

Handled missing values and infinite values (resulting from division by zero) by dropping the affected rows.

Feature Engineering:

Converted categorical features (BALLOT TYPE, MSA) into numerical data using one-hot encoding (pd.get_dummies).

Applied StandardScaler to the feature set before training the K-Nearest Neighbors (KNN) model, as it is a distance-based algorithm.

Exploratory Data Analysis (EDA):

Analyzed the distributions of key features like Per Capita Income (PCI) and the corrected Church Member Percentage.

Used box plots to visualize the relationship between predictors (e.g., UNEMPLOYMENT RATE, PERCENT WHITE) and the target variable.

Model Training & Evaluation:

Split the data into a 70% training set and 30% testing set, using stratify to ensure the class balance was preserved.

Trained and evaluated three different classification models:

Decision Tree (DT)

K-Nearest Neighbors (KNN)

Naïve Bayes (Gaussian)

Assessed each model using a comprehensive set of metrics: Accuracy, Precision, Recall, F1-Score, and the Confusion Matrix.

Model Performance & Results
The models were evaluated based on their performance on the unseen test data. The Decision Tree was selected as the best overall model due to its high F1-Score and Recall, making it the most reliable for identifying "Yes" votes.

Metric	Decision Tree	K-Nearest Neighbors	Naïve Bayes
Accuracy	0.6788	0.6865	0.5881
Precision	0.6053	0.6387	0.5309
Recall	0.7012	0.6037	0.2622
F1-Score	0.6497	0.6207	0.3510

Export to Sheets

Key Insights & Feature Importance
A critical part of the analysis was interpreting the top-performing model. The Decision Tree's feature_importances_ attribute revealed the most influential factors in predicting the vote:

Feature	Importance Score
PERCENT WHITE	0.1972
PERCENT CHURCH MEMBERS OF POPULATION_CORRECTED	0.1233
POVERTY LEVEL	0.1035
BALLOT TYPE_2	0.0990
NO OF CHURCHES	0.0880

Conclusion: The analysis shows that demographic and religious factors are more predictive of voting behavior on this issue than purely economic indicators. These insights could be used by a campaign to effectively target and allocate resources to counties with the highest probability of a "Yes" vote.

Technologies Used
Python

Pandas: For data manipulation and cleaning

Scikit-learn (sklearn): For data preprocessing (StandardScaler, train_test_split) and modeling (DecisionTreeClassifier, KNeighborsClassifier, GaussianNB)

Matplotlib & Seaborn: For data visualization
