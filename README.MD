## <span style="color:white;background-color:GREY;">INTRODUCTION</span>
Term deposits are a type of fixed investment where customers deposit money with a financial institution for a predetermined   period at an agreed interest rate. These deposits are a reliable and significant source of income for banks, as they provide a  stable inflow of funds while offering customers a secure way to grow their savings.  
To promote term deposits, banks employ various marketing strategies, including email marketing, advertisements, digital   outreach, and telephonic campaigns. Among these, telephonic marketing remains one of the most effective methods for engaging   customers. However, this approach involves substantial costs due to the operational requirements of large call centers. 

## <span style="color:white;background-color:GREY;">BUSINESS PROBLEM</span>
Telephonic marketing is an effective but costly method for promoting term deposits. To optimize resources and improve   conversion rates, the bank needs to identify customers most likely to subscribe to a term deposit before reaching out, ensuring   more targeted and cost-efficient marketing efforts.  

## <span style="color:white;background-color:GREY;">OBJECTIVES</span>

1. **Identify Key Predictors**: Analyze customer demographics, previous interactions, and campaign details to determine the most important factors influencing a customer’s decision to subscribe to a term deposit.

2. **Develop the Best Prediction Model**: Build and evaluate multiple classification models to identify the most accurate model for predicting whether a customer will subscribe to a term deposit, ensuring optimal performance.

3. **Optimize Marketing Strategies**: Use the insights from the model to recommend targeted telephonic marketing strategies, focusing on high-potential customers to maximize conversion rates and reduce unnecessary outreach.
### Metrics of Success:

1. **Model Accuracy:** Achieve over 80% accuracy in predicting customer subscription to a term deposit.
2. **Precision & Recall:** High precision and recall for identifying customers likely to subscribe (Class 1).
3. **Feature Importance:** Identify key factors influencing subscription decisions to optimize marketing strategies.
4. **Conversion Rate:** Increase conversion rates by targeting high-potential customers.
5. **Outreach Efficiency:** Reduce unnecessary outreach to non-potential customers.
6. **Cross-validation Performance:** Ensure consistent performance across different data subsets to avoid overfitting.

## <span style="color:white;background-color:GREY;">DATA UNDERSTANDING</span>
This dataset is related to the direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were conducted through phone calls, often requiring multiple contacts with the same client to determine whether they would subscribe to the product (bank term deposit). The target variable indicates whether the client subscribed (`"yes"`) or not (`"no"`).
### Dataset Overview
The data folder contains two datasets:

- **`train.csv`**: Contains 45,211 rows and 18 columns, ordered by date (from May 2008 to November 2010).
- **`test.csv`**: Contains 4,521 rows and 18 columns, representing 10% of the examples, randomly selected from `train.csv`.
### Column Descriptions
#### Bank Client Data:
1. **`age`**: Age of the client (numeric).
2. **`job`**: Type of job (categorical: `"admin."`, `"unknown"`, `"unemployed"`, `"management"`, `"housemaid"`, `"entrepreneur"`, `"student"`, `"blue-collar"`, `"self-employed"`, `"retired"`, `"technician"`, `"services"`).
3. **`marital`**: Marital status (categorical: `"married"`, `"divorced"`, `"single"`; note: `"divorced"` includes divorced or widowed).
4. **`education`**: Level of education (categorical: `"unknown"`, `"secondary"`, `"primary"`, `"tertiary"`).
5. **`default`**: Has credit in default? (binary: `"yes"`, `"no"`).
6. **`balance`**: Average yearly balance in euros (numeric).
7. **`housing`**: Has a housing loan? (binary: `"yes"`, `"no"`).
8. **`loan`**: Has a personal loan? (binary: `"yes"`, `"no"`).
#### Last Contact of Current Campaign:
9. **`contact`**: Contact communication type (categorical: `"unknown"`, `"telephone"`, `"cellular"`).
10. **`day`**: Last contact day of the month (numeric).
11. **`month`**: Last contact month of the year (categorical: `"jan"`, `"feb"`, `"mar"`, …, `"nov"`, `"dec"`).
12. **`duration`**: Last contact duration in seconds (numeric).
#### Other Attributes:
13. **`campaign`**: Number of contacts performed during this campaign for this client (numeric, includes last contact).
14. **`pdays`**: Number of days since the client was last contacted in a previous campaign (numeric; `-1` means the client was not previously contacted).
15. **`previous`**: Number of contacts performed before this campaign for this client (numeric).
16. **`poutcome`**: Outcome of the previous marketing campaign (categorical: `"unknown"`, `"other"`, `"failure"`, `"success"`).
#### Output Variable (Target):
17. **`y`**: Has the client subscribed to a term deposit? (binary: `"yes"`, `"no"`).  

Data source: https://www.kaggle.com/datasets/thedevastator/bank-term-deposit-predictions?resource=download

### <span style="color:white;background-color:grey;">CONCLUSIONS</span>

1. **Most Important Predictors**:
   - **Duration (0.295)**: Longer interactions significantly increase the likelihood of subscription.
   - **Balance (0.113)**: Higher average yearly balance is associated with a higher probability of subscribing.
   - **Age (0.108)**: Older customers are more likely to subscribe to a term deposit.

2. **Moderate Predictors**:
   - **Day (0.095) and Month (0.094)**: Timing of the last contact influences subscription, indicating seasonality.
   - **Pdays (0.065)**: Recent contact increases the likelihood of subscription.
   - **Job (0.050)**: Job type impacts subscription decisions, with managerial or professional jobs more likely to subscribe.
   - **Campaign (0.039)**: More contacts during the campaign have a positive but smaller impact.

3. **Less Significant Predictors**:
   - **Housing (0.029) and Education (0.029)**: These factors show minor influence.
   - **Previous Contacts (0.028)**: Repeated contacts have a smaller effect.
   - **Marital Status (0.022) and Contact Type (0.021)**: Minimal impact on subscription likelihood.
   - **Loan (0.011) and Default (0.002)**: These features have very low impact.
   - **Poutcome (0.000)**: Previous campaign outcome does not influence the decision.

#### Insights:
- **Key Factors**: Duration of the call, balance, and age are the strongest predictors.
- **Campaign Timing**: The day, month, and timing of contact matter for successful subscriptions.
- **Demographics and Financial Stability**: Job type and balance are secondary but important indicators.

Based on the model evaluations:

- **Random Forest** The model generalizes well from training to testing with consistent performance(96.11%), particularly in predicting the negative class (Class 0). The slight improvement in recall for the positive class (Class 1) on the test set may indicate better generalization or data characteristics in the test set. The model seems well-calibrated with no significant overfitting or underfitting.
- **Logistic Regression** shows decent accuracy (88.56%) but struggles with identifying subscribers, having low recall and F1-score for Class 1.
- **KNN** has good accuracy (90.09%) but also faces challenges with recall for Class 1, similar to Logistic Regression. 

Optimizing Marketing Strategies Based on Subscription Probability:
 
- Customers with high `subscription_prob` values (e.g., 0.892162, 0.871691, 0.870282) have a high likelihood of conversion.   
- Customers with `subscription_prob` values between 0.75 and 0.80 represent the next tier of likely conversions. While not as urgent as the highest-probability customers, this segment still holds significant potential and should be targeted with focused outreach.  
- To maximize conversion rates with minimal effort, prioritize customers with `subscription_prob` values above 0.8. This ensures that marketing resources are allocated to those most likely to convert, improving efficiency and outcomes.  
- Customers with lower `subscription_prob` values (e.g., 0.716083, 0.725284) are less likely to convert and should either be deprioritized or approached with alternative strategies, such as offering incentives or alternative products, rather than standard outreach efforts.


### <span style="color:white;background-color:grey;">RECOMMENDATIONS</span>
- Focus on **longer, high-quality interactions**.
- Tailor campaigns based on **age** and **balance**.
- Utilize **personalized outreach strategies** to improve subscription rates.
- Focus on **Random Forest** for its overall performance, and improve recall for the minority class by addressing class imbalance and tuning model parameters.
- **Target High-Probability Customers**: Focus marketing efforts on customers with high `subscription_prob` (e.g., 0.892162, 0.871691, 0.870282). These customers are highly likely to subscribe, requiring minimal outreach for better conversion rates.

- **Use a Probability Threshold**: Consider customers with probabilities around 0.75–0.80 for the next tier of targeted outreach. While not as urgent as the highest-probability customers, they still represent a valuable segment to target.

- **Optimize Resource Allocation**: Allocate resources efficiently by prioritizing customers with probabilities above 0.8. This ensures higher conversion rates with less effort on low-probability customers.

- **Reduce Unnecessary Outreach**: Deprioritize customers with lower probabilities (e.g., 0.716083, 0.725284), or approach them with different strategies, such as offering incentives or alternate products.