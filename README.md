Loan Default Prediction Analysis
Overview

Loan approval and risk assessment are critical processes in the banking and financial sector. Financial institutions need to understand borrower characteristics and loan behavior to reduce the risk of defaults and make informed lending decisions.

This project performs Exploratory Data Analysis (EDA) on loan data and builds a basic Machine Learning model using Linear Regression to analyze the relationship between borrower information and loan amounts. Various visualizations are used to uncover patterns in loan status, income levels, interest rates, and loan purposes.

Objectives
Analyze loan application data
Clean and preprocess raw loan records
Explore borrower demographics and loan characteristics
Visualize loan distribution and repayment status
Identify factors influencing loan amounts
Build a predictive model using Linear Regression
Evaluate model performance using R² Score
Dataset Information

The dataset contains loan application and repayment information collected from borrowers.

Selected Features
Feature	Description
loan_amnt	Loan amount requested
term	Loan duration (months)
int_rate	Interest rate
annual_inc	Annual income of borrower
emp_length	Employment length
home_ownership	Home ownership status
purpose	Purpose of the loan
grade	Loan grade assigned
loan_status	Current loan status
Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Plotly
Scikit-Learn
Jupyter Notebook
Data Preprocessing

The following preprocessing steps were performed:

Feature Selection

Relevant columns were extracted from the original dataset containing 151 columns.

Missing Value Handling

Rows containing missing values were removed using:

df.dropna(inplace=True)
Data Conversion

Interest rates were converted from string format to numerical values.

df['int_rate'] = df['int_rate'].astype(str).str.replace('%','').astype(float)

Loan term values were converted into integer months.

df['term'] = df['term'].astype(str).str.extract('(\d+)').astype(int)
Exploratory Data Analysis
Descriptive Statistics

The project calculates:

Average Loan Amount
Average Annual Income
Minimum and Maximum Values
Standard Deviation
Quartile Distribution
Dataset Summary
Total Records After Cleaning: 9,272
Average Loan Amount: 15,306
Average Annual Income: 80,653
Loan Status Distribution

Loan status analysis revealed:

Loan Status	Count
Fully Paid	6670
Charged Off	1570
Current	961
Late (31-120 days)	57
In Grace Period	11
Late (16-30 days)	3

The majority of loans in the dataset were successfully repaid.

Data Visualizations

Several visualizations were created to better understand the dataset.

Count Plot

Displays the distribution of loan statuses.

Box Plot

Compares annual income across different loan statuses.

Purpose Analysis

Shows the relationship between loan purpose and repayment status.

Scatter Plot

Analyzes the relationship between:

Annual Income
Loan Amount
Correlation Heatmap

Identifies correlations among numerical variables.

Interactive Plotly Visualizations
Loan Amount Distribution
Income vs Loan Amount Analysis
Loan Status Visualization
Machine Learning Model
Model Used

Linear Regression

The model predicts loan amount using:

Annual Income
Interest Rate
Loan Term
Feature Matrix
X = df[['annual_inc','int_rate','term']]
Target Variable
y = df['loan_amnt']
Train-Test Split
test_size = 20%
random_state = 42
Model Training
model = LinearRegression()
model.fit(X_train, y_train)
Model Evaluation

The model was evaluated using the R² Score.

Result
R² Score = 0.2798
Interpretation

The model explains approximately 28% of the variation in loan amounts using annual income, interest rate, and loan term.

This indicates that additional borrower features may be required to improve prediction accuracy.

Key Insights
Most borrowers successfully repay their loans.
Higher annual income generally corresponds to larger loan amounts.
Interest rates vary significantly across loan grades.
Certain loan purposes have higher default rates.
Loan amount is influenced by multiple factors beyond income and interest rate.
