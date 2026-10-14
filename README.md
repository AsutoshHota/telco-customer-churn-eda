# Telco Customer Churn Analysis (EDA)

An exploratory data analysis (EDA) project investigating customer churn
in a telecommunications dataset using Python, Pandas, Matplotlib, and
Seaborn. The analysis explores how churn relates to customer tenure,
contract type, payment method, senior-citizen status, and subscribed
services.

## Project Overview

Customer churn occurs when customers stop using a company's services.
Understanding patterns associated with churn can help a business
identify at-risk customer groups and plan retention initiatives.

This project focuses on: - Exploring and cleaning the dataset. -
Checking data types, missing values, and duplicate records. -
Understanding the overall distribution of churn. - Comparing churn
across demographic, contract, payment, tenure, and service-related
categories. - Communicating findings through charts and exploratory
visualizations.

## Repository Contents

Suggested repository structure:

``` text
telco-customer-churn-eda/
├── Customer_Churn(EDA Proj).ipynb   # Jupyter Notebook containing the analysis
├── Teco Customer Churn Analysys.pdf # PDF report / summary of findings
├── Customer Churn.csv               # Source dataset (add this if you have permission to share it)
└── README.md                        # Project documentation
```

> **Dataset note:** The notebook loads a file named
> `Customer Churn.csv`. That CSV was not included with the files
> reviewed for this README. Add it to the repository only if you are
> allowed to redistribute it. Otherwise, include instructions for
> obtaining it from its original source and keep it out of the
> repository.

## Tools and Libraries

-   **Python** --- analysis and data processing
-   **Pandas** --- data loading, cleaning, grouping, and summaries
-   **NumPy** --- numerical operations
-   **Matplotlib** --- chart layout and visualization
-   **Seaborn** --- statistical plots, including count plots and
    histograms
-   **Jupyter Notebook** --- interactive workflow

## Analysis Workflow

1.  **Load the data** with Pandas from `Customer Churn.csv`.
2.  **Inspect the dataset** using methods such as `head()`, `info()`,
    `describe()`, and `isnull().sum()`.
3.  **Clean `TotalCharges`** by replacing blank-string values with `0`
    and converting the column to a numeric type.
4.  **Check duplicates** across complete rows and the `customerID`
    column.
5.  **Prepare `SeniorCitizen`** by converting the numeric `0`/`1` values
    to readable `no`/`yes` labels.
6.  **Explore churn distribution** using a count plot and a pie chart.
7.  **Compare churn across customer groups**, including gender,
    senior-citizen status, tenure, contract type, subscribed services,
    and payment method.
8.  **Create multi-panel count plots** for `PhoneService`,
    `MultipleLines`, `InternetService`, `OnlineSecurity`,
    `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`,
    and `StreamingMovies`, with `Churn` used as the hue.
9.  **Summarize findings** and suggest retention strategies based on the
    observed patterns.

## Key Findings

The accompanying PDF summary reports the following patterns from the
analysis:

-   **Overall churn:** Approximately **26.54%** of customers churned.
-   **Contract type:** Month-to-month customers had the highest reported
    churn rate (**42%**), compared with **11%** for one-year contracts
    and **3%** for two-year contracts.
-   **Payment method:** Electronic-check users had the highest reported
    churn rate (**45%**). The report gives approximately **15%** for
    credit-card users and describes other payment methods as generally
    lower, around **15--18%**.
-   **Tenure:** Customers with less than one year of tenure had a
    reported churn rate of **50%**. The report describes a decline to
    **35%** for 1--3 years and **15%** for more than three years.
-   **Internet service:** The report gives a churn rate of **30%** for
    Fiber Optic customers and **20%** for DSL customers.
-   **Senior citizens:** The report gives a churn rate of **41%** for
    senior citizens and **26%** for non-senior citizens.
-   **Service subscriptions:** The notebook compares churn across phone,
    internet, security, backup, device-protection, technical-support,
    and streaming services.

**Important:** These percentages are reproduced from the project's
accompanying report; they have not been independently recalculated for
this README. Treat them as descriptive findings from this dataset, not
proof that any particular factor causes churn.

## Business Recommendations

Based on the patterns described in the report:

1.  **Encourage longer-term contracts:** Test suitable incentives for
    customers considering one-year or two-year plans.
2.  **Improve early-tenure engagement:** Introduce onboarding check-ins
    and proactive support during the first year.
3.  **Review electronic-check customers' experience:** Investigate
    payment friction, failed payments, billing questions, and customer
    concerns before encouraging alternative payment options.
4.  **Review Fiber Optic customer experience:** Examine service quality,
    reliability, pricing, and support feedback.
5.  **Offer relevant support to senior customers:** Make support and
    plan information accessible and easy to understand.
6.  **Use data to target retention efforts:** Validate these patterns
    with current data and measure whether any retention initiative
    improves outcomes.

These are recommendations to investigate and test; the EDA alone does
not establish causation.

## How to Run the Project

### 1. Clone the repository

``` bash
git clone <your-repository-url>
cd telco-customer-churn-eda
```

Replace `<your-repository-url>` with the URL of your GitHub repository.

### 2. Install dependencies

``` bash
pip install pandas numpy matplotlib seaborn jupyter openpyxl
```

### 3. Add the dataset

Place `Customer Churn.csv` in the same directory as the notebook, or
update the path in the notebook to match where you saved the file.

### 4. Launch Jupyter

``` bash
jupyter notebook
```

Open `Customer_Churn(EDA Proj).ipynb` and run the cells in order.

## Example Visualization Code

The notebook uses count plots to compare churn across service
categories. For example:

``` python
import matplotlib.pyplot as plt
import seaborn as sns

cols = [
    "PhoneService", "MultipleLines", "InternetService",
    "OnlineSecurity", "OnlineBackup", "DeviceProtection",
    "TechSupport", "StreamingTV", "StreamingMovies"
]

fig, axes = plt.subplots(3, 3, figsize=(18, 12))

for col, ax in zip(cols, axes.flatten()):
    sns.countplot(data=df, x=col, hue="Churn", ax=ax)
    ax.set_title(f"Count Plot of {col}")
    ax.set_xlabel(col)
    ax.set_ylabel("Count")
    ax.tick_params(axis="x", rotation=30)

plt.tight_layout()
plt.show()
```

## Limitations

-   This is an exploratory analysis; it does not build or evaluate a
    predictive churn model.
-   Associations shown in charts do not demonstrate causation.
-   The percentages listed above come from the supplied report and
    should be rechecked against the source data before being used in
    business decisions.
-   Results depend on the quality, coverage, and date of the dataset.

## Future Improvements

-   Calculate churn rates by category directly and display them as
    percentages.
-   Add a correlation or association analysis where appropriate for the
    variable types.
-   Create an interactive dashboard using Plotly or Power BI.
-   Build a baseline churn prediction model and evaluate it using
    suitable metrics.
-   Add a reproducible environment file such as `requirements.txt`.
-   Add data validation and automated checks for missing values and
    duplicate customer IDs.

## Author

**Asutosh Hota**

## License

Add a license before publishing if you want others to reuse the code.
Confirm the dataset's license and sharing terms separately; a code
license does not automatically grant rights to redistribute the data.
