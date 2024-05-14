# Analysis of Ironhack Payments by cohorts

## **Introduction**

IronHack Payments, is a financial services company has been offering innovative cash advance solutions since its inception in 2020. With a commitment to providing free cash advances and transparent pricing, IronHack Payments has achieved a substantial user base. As part of its ongoing effort to improve its services and understand user behavior, IronHack Payments has commissioned a cohort analysis project.

The report provides an overview of IronHack Payments' cohort analysis project, which aims to understand user behavior and improve services. By utilizing a cohort study approach, the project examines how various factors influence subsequent cash request behavior and explores the relationship between commission fees and cash requests. Organizing users into cohorts *based on their first cash request month*, the study analyzes metrics such as *'user retention rate'*, *'credit incident rate'*, *'generated income'*, and *xxxx*. 

The insights gained from this analysis assist IronHack Payments in making informed decisions regarding marketing, product development, and customer retention strategies in the future.


## **Data Collection and Data Cleaning**

As a retrorespective study, the study has been provided with two datasets:
  1. Extract of cash requests (project_dataset\extract - cash request - data analyst.csv)
  2. Extract of fees (project_dataset\extract - fees - data analyst - .csv)

  *For description of columns, please check the glossary file (project_dataset\Lexique - Data Analyst.xlsx)

### - Overview of Raw Datasets

We have created heatmaps to visualizae the null data in each dataset - cash request(Figure 1) and fees (figure 2), *red* marks cells with null data while *green* marks those with values. At this stage, our focus is to analyze the meaning and impact of each collection of data thus engage with the next step of data cleaning. 

![alt text](Resources/null_cr_heatmap.png)
<p align="center"><b>Figure 1</b>

![alt text](Resources/null_fees_heatmap.png)
<p align="center"><b>Figure 2</b>

### - Data Types

Both datasets contain object and integer types of data, in order to facilitate furture analysis, we have transformed datas with the date&time format into datatime type in Python. The operation shows as following:

                df_fees[["created_at", "updated_at", "paid_at", "from_date", "to_date"]] = 
                    df_fees[["created_at", "updated_at", "paid_at", "from_date", "to_date"]].apply(pd.to_datetime, format="ISO8601")

### - Data Cleaning

Handling Missing Values:

To address missing data in the above datasets, we have develpoed a strategy of replacing the empty cells with relevant data accordingly. As for cash request dataset, we have imputed the combination of 'status' and 'transfer_type' into the missing cells; and for fees dataset, missing cells are filled in depending on its 'type' and 'category' - if the missing cell is missing due to unapplicable condition, the cell is filled in with "not applicable"

For detailed imputation process, please check *[NoteBooks\3_DataCleaning.ipynb]*


## **Exploratory Graphic Analysis for Cash Request Dataset**

- Summary Statistics

    Dataset has in total 23970 rows, representing users who had requested cash with IronHack Paymnets from 2019-11-19 until 2020-11-01.
    2020-10 has the most users who made their 1st transaction with the company. 
    ![alt text](Resources/cohort_overview_cr.png)

- Distribution Plots

    - Distrubution of Different Status of Cash Request Types
    ![alt text](Resources/status_cr_distribution.png)

    - Line Chart for Request Frequency per Month
    ![alt text](Resources/cr_frequency_monthly.png)


## **Exploratory Graphic Analysis for Fees Dataset**

- Summary Statistics
    
    Dataset has iin total 21061 rows, representing the fees added per cash request, from 2020-05-29 until 2021-02-10.
    4 fees have missed data in cash_request_id;
    1 fee is 10 euros while the rest are 5 euros fixed fee;

- Distribution Plots

    - Bar Plot of Fee types
    ![alt text](Resources/fees_types_plot.png)

    - Distribution of Fee Status
    ![alt text](Resources/fee_status.png)

    - Fees Transaction Frequency by Started_Date
    ![alt text](Resources/fees_frequency_start_date.png)

    - Proportion of Fees Transaction Categories
    ![alt text](Resources/Proportion_fee_category.png)


## Visualizations of Relation between Two Datasets

- Charts and graphs

    - Comparison of Fee Transaction and Cash Request Status
    ![alt text](Resources/fee_cr_status_compare.png)

    - Comparison of Fee Transaction and Cash Request Frequency per Month
    ![alt text](Resources/fee_cr_frequency_compare.png)


- Interpretations

  

## **Insights and Findings**

- Key findings

- Anomalies and patterns

- Potential actions


## **Conclusion**

- Summary

- Next steps


## **Appendix**

*session 1 - 4th May*

- crear organization in github
- study the raw data and understand the dataframes -> flowchart of cash request, fee&reimbursement created
- create Trello board to notedown tasks (https://trello.com/b/LRPUSwtH/ironhack-firstproject)
- EDA
    1. Exploratory Graphical Analysis for df_fees;
        *e.g. 'Distribution of type of fees', 'Number of Transactions by Status', 'Transaction Frequency by Date', 'Proportion of Transaction Categories'*
    2. Exploratory Graphical Analysis for df_cash_request;
        *e.g. 'Distrubution of cash requests status by types', 'Request Frequency per Month'*
    3. Exploratory Graphical Analysis of Relationship between both DataFrames.
        *e.g. 'Comparison of Transaction and Request Status', 'Comparison of Transaction and Request Frequency per Month'*


*session 2 - 7th Mayo*

- data cleaning -> investigate null data and fill in/drop accordingly
- define cohort -> first transaction month
- calculate cohort 'retention rate' by month

*session 3 - 9th Mayo*

- correct calculation of 'retention rate'
- fill in Null value in heatmap
- investigate rare date -> fees status 'cancelled' & "paid"; transaction "send_at" after "received_date" 