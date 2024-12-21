# Bank Loan Analysis Project

## Overview
The Bank Loan Analysis Project is a comprehensive examination of loan data to extract insights, trends, and key performance indicators (KPIs). This project leverages data analysis, SQL querying, and business intelligence tools to analyze and visualize the performance of a bank's loan portfolio. The analysis provides actionable insights into the quality of loans issued, trends in loan applications, and customer demographics.

![Screenshot 2024-12-16 211422](https://github.com/user-attachments/assets/03a4e2a5-8bea-49d9-9d3f-d19e3afa9618)


## Objective
The primary objective of this project is to:
- Identify trends in loan issuance and repayment.
- Analyze the performance of loan products based on customer characteristics and loan terms.
- Highlight KPIs, such as the total funded amount, interest rates, and good/bad loan percentages.
- Enable data-driven decision-making for stakeholders.

## Problem Statement
The banking industry faces challenges in evaluating the performance of loan products and understanding customer repayment behavior. This project aims to provide a detailed analysis of loan data to identify:
- The distribution of loan applications by term, state, and purpose.
- Key factors contributing to good and bad loans.
- Monthly and overall performance metrics for loan issuance and repayment.

## Dataset
The dataset used in this project includes detailed information about loan applications, including:
- Loan amounts and terms
- Customer details (e.g., state, employment length, home ownership)
- Interest rates and debt-to-income (DTI) ratios
- Loan status and repayment history

## Key Insights
### KPIs
1. **Total Loan Applications**:
   ```sql
   SELECT COUNT(id) AS Total_Applications FROM bank_loan_data
   ```
   
2. **Total Funded Amount**:
   ```sql
   SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data
   ```

3. **Total Amount Received**:
   ```sql
   SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data
   ```

4. **Average Interest Rate**:
   ```sql
   SELECT AVG(int_rate)*100 AS Avg_Int_Rate FROM bank_loan_data
   ```

5. **Good Loan Percentage**:
   ```sql
   SELECT
       (COUNT(CASE WHEN loan_status = 'Fully Paid' OR loan_status = 'Current' THEN id END) * 100.0) /
       COUNT(id) AS Good_Loan_Percentage
   FROM bank_loan_data
   ```

6. **Bad Loan Percentage**:
   ```sql
   SELECT
       (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) /
       COUNT(id) AS Bad_Loan_Percentage
   FROM bank_loan_data
   ```

### Performance Metrics
- **Monthly Loan Applications**:
   ```sql
   SELECT MONTH(issue_date) AS Month, COUNT(id) AS Total_Applications
   FROM bank_loan_data
   GROUP BY MONTH(issue_date)
   ```

- **Loan Performance by State**:
   ```sql
   SELECT
       address_state AS State,
       COUNT(id) AS Total_Loan_Applications,
       SUM(loan_amount) AS Total_Funded_Amount,
       SUM(total_payment) AS Total_Amount_Received
   FROM bank_loan_data
   GROUP BY address_state
   ```

- **Loan Analysis by Purpose**:
   ```sql
   SELECT
       purpose AS PURPOSE,
       COUNT(id) AS Total_Loan_Applications,
       SUM(loan_amount) AS Total_Funded_Amount,
       SUM(total_payment) AS Total_Amount_Received
   FROM bank_loan_data
   GROUP BY purpose
   ```

## Tools and Technologies
- **SQL**: For data querying and analysis.
- **Power BI**: To create dashboards and visualizations.
- **Python (Optional)**: For data preprocessing and additional analysis.
- **Microsoft Excel**: For data exploration and manual checks.

## Files Included
1. **financial_loan.csv**: The dataset used for analysis.
2. **Bank Domain & Terminology Doc**: A document detailing the domain knowledge and terminology.
3. **Problem Statement.pptx**: A presentation outlining the problem statement.
4. **Bank Loan Report_Power BI.pbix**: The Power BI file containing visualizations and dashboards.

## How to Use
1. **Data Analysis**: Use the provided SQL queries to extract and analyze the dataset.
2. **Visualization**: Open the Power BI file to explore the interactive dashboards.
3. **Customization**: Modify the queries and filters to analyze specific aspects of the data.

## Conclusion
This project highlights critical insights into the bank's loan portfolio, providing valuable information on customer behavior, loan performance, and financial trends. By leveraging SQL and Power BI, stakeholders can make informed decisions to improve loan quality and customer satisfaction.

