# Visual Data Exploration of Prosper Loan Data
## by Stetson Done


# Dataset Description

>This analysis will dive into a loan dataset from Prosper (a personal loan company). The raw dataset contains information about 113,937 loans with 81 variables about each loan. The dataset was acquired through Udacity, but can be found on kaggle.com at https://www.kaggle.com/yousuf28/prosper-loan. 


# Preliminary Wrangling

>All data wrangling and cleaning was completed in a separate notebook prior to this analysis. See data_wrangling_and_cleaning.ipynb for details. In the wrangling and cleaning of the dataset, I did the following:

 <ol>
    <li>Changed column casing from camelCase to snake_case</li>
    <br/>
    <li>Changed closed date and loan origination date to datetime datatypes</li>
    <br/>
    <li>Reordered columns into more logical order/grouping</li>
    <br/>
    <li>Converted the income_verifiable and is_borrower_homeowner to binomials</li>
    <br/>
    <li>Added is_account_closed feature as binomials using closed_date column</li>
    <br/>
    <li>Added is_loan_delinquent feature as binomials using loan_current_days_delinquent column</li>
    <br/>
    <li>Separated dataframe into one dataframe for member info and one for loan info</li>
    <br/>
    <li>Made one tidy master dataframe</li>
    <br/>
    <li>Saved new dataframes into new csv files</li>
 </ol>


# Exploratory Questions from the Visual Analysis 

### What is the distribution of borrower's credit scores?
>Both lower and upper credit limit ranges have a narrow distribution, with a lower mean of 685 and an upper mean of 704. Both lower and upper ranges had a standard deviation of 66.

### What does the income distribution of borrowers look like?
> The majority of borrowers are making 25,000 - 74,999 dollars per year.  

### What is the average debt to income ratio for borrowers?
> From the documentation provided to decribe the data set, the debt to income ratio is "The debt to income ratio of the borrower at the time the credit profile was pulled. This value is Null if the debt to income ratio is not available. This value is capped at 10.01 (any debt to income ratio larger than 1000% will be returned as 1001%)." - - Seeing this box plot, I first thought the high numbers but be incorrect data, but it seems from the data description, these ratios really can be up to 1000% for debt to income ratio. The median, however, is 22%.

### On average, how many open revolving accounts did borrowers have when they applied for the loan?
> The average (mean) number of open revolving accounts was 6.9 and the median was 6. There do appear to be several outliers, with the max number of open revolving accounts as 51.

### What was the average number of delinquencies in the last 7 years per borrower at the time the credit was pulled?
> Most borrowers did not have delinquencies in the last seven years, although the mean (4 accounts delinquent) looks to be heavily affected by the number of outliers. 

### What were borrowers' average monthly loan payments?
> The mean monthly payment was 217 dollars a month and the median monthly loan payment was 217 dollars per month.

### How many borrowers were home owners vs non-homeowners?
> The vast majority of borrowers were homeowners, with a ratio of approximately 12:1. 

### What was the average loan amount?
> The average loan amount was 8,337 dollars and the median was 6,500 dollars. 

### At the time this data was pulled, how many loans were delinquent vs not delinquent?
> The majority of loans were not delinquent, with over 4x as many loans not delinquent as were delinquent.

### What was the distribution of loans in each loan status category at the time this data was pulled? (Loan status categories include: Cancelled, ChargedOff, Completed, Current, Defaulted, FinalPaymentProgress, PastDue). 
> Most loans were current, some were completed, and fractions of them were chargedoff, defaulted, or past due.

### What was the average percentage estimated loss of the original loan amount if the loan is charged off? This loss is estimated at the time the loan is issued.
> The average estimated loss if a loan is charged off was 8%. The median estimated loss was 7%.

### Is there a relationship between a borrower's credit score and the estimated percentage loss on the loan if it is charged off? 
> There is a moderate (-0.5 correlation coefficient) negative relationship of borrower's credit score and the estimated loss on the loan in case of chargte-off. Per the pearsonr calculation done in the analysis, the correlation coefficient is -0.5 with a p-value of 0, which tells us there is a statistically significant moderate negative relationship between the two values (i.e. When the borrower's credit score goes up, the estimated loss on the loan goes down). 

### Is there a relationship between a borrower's credit score and their monthly payment and thier APR (annual interest rate)?
> There is a moderate negative relationship between a borrower's APR and their credit score. The pearsonr calculation revealed a correlation coefficient of -0.4 and a p-value of 0, which indicates the moderate negative correlation is statistically significant (i.e. As the borrower's credit score went up, their APR went down). 

### Is there a relationship between a borrower's credit score and their debt to income ratio?
> Surprisingly, based on the pearsonr calculation and visual scatter plot analysis, there did not appear to be any correlation between a borrower's credit score and their debt to income ratio.

### What is the relationship (if any) between the following variables - borrower apr, loan original amount, monthly loan payment, estimated loss, and estimated return?
> The visual relationships that stand out in the pairplots were a positive relationship between estimated return and borrower apr, a positive relationship between monthly loan payment and loan amount, and negative relationships between estimated loss and monthly loan payment/loan amount.

### What are the relationships of the borrowers' credit score and loan amount within each income category? To visualize the data more easily, we will only look at the upper four income ranges.
> The relationship between monthly loan payment and original loan amount seems to stay consistent within each income range.
    
### What was the distribution of borrower credit scores in loan categories of current and defaulted? In loans which were defaulted, were borrower's scores lower on average?
> From the FacetGrid box plots, it is clear the distribution of borrower's credit scores is higher where loan statuses are current and lower where loan statuses are default.


# Key Insights 

> The borrower's credit score greatly affected the loan in three major ways: 
<ol>
<li>Through the analysis, the borrower's annual interest rate was shown to increase when their credit score decreased.</li> 
> The negative correlation of a borrower's credit score and their APR was -0.4 with a p-value of 0.
</br>
<li>The lower the borrower's credit score, the greater estimated risk of the loan in case of charge-off.</li>
> The negative correlation of greater estimated loan risk and borrower credit score was approximately -0.5 with a p-value of 0.
</br>
<li>The range of credit scores for current loans are significantly higher than the range of credit scores for the defaulted loans.</li>
> For the loans which are current, the borrower credit score distribution ranged from 600-880 (lower range) to 619-899 (upper range). The mean credit scores were 698 (lower range) and 717 (upper range). The median credit scores were 700 (lower range) and 719 (upper range). 
> For the loans which are defaulted, the borrower credit score distribution ranged from 0-860 (lower range) to 19-879 (upper range). The mean credit scores were 620 (lower range) and 639 (upper range). The median credit scores were 640 (lower range) and 659 (upper range).
 </ol>
