# Creating a Predictive Model for Employees Turnover using Logistic Regression and Machine Learning
This is the final project for the **Google Advanced Data Analytics Professional Certification**. The aim of this project is to plan, analyze, construct and execute a predictive model that helps a company understand why their employees may leave and prevent it.

This document will present a brief summary of the business case, an overview of the tasks that were conducted and some key metrics/results. However, to *fully understand* where the final results come from, it's necessary to *explore the notebooks*. The following order is recommended:
  1) Salifort Motors - EDA
  2) Logistic Regression Model
  3) Random Forest Model

Finally, there's an **Executive Summary** available that summarizes the whole business case and solution to a single slide.

## Introducing the Business Case
Salifort Motors' senior leadership team is concerned because of **how many employees are leaving the company** (for the time being they won't make a difference between employees who resigned and the ones who were let go). This affects the work culture of the company, morale of employees and ends on high administrative and financial costs (since replacing people involves recruiting, training and upskilling).

They asked their human resources department to conduct a massive survey among employees and deliver the data.

## Important Disclaimer
It's important to clarify that Salifort Motors seems to be a *ficticious company* created by Google/Coursera personnel with educative purposes. This data mirrors reality but should not be associated with any company.

## Goals of the project
  1) **Construct a Predictive Model** that helps determine if an **employee is likely to leave or not**. This will help increase employee retention.
  2) Understand the **main factors** that lead to employees leaving the organization.
  3) Get some **recommendations on actionable next steps** to decrease the employee turnover rate.

## Data Understanding

The data used for this project consists on 15.000 records as the result of the survey mentioned earlier. After removing the duplicates, almost 12.000 unique rows of information remain in the dataset.
The **features** included in the dataset are the following:

![image](https://github.com/DataGuti/Logistic-Regression-and-Machine-Learning-on-predicting-employees-turnover/assets/57073572/9e8cc882-1539-4cc4-a6af-92da16a42df1)

The pie chart below shows the **current Employee Turnover Rate**.

![image](https://github.com/DataGuti/Logistic-Regression-and-Machine-Learning-on-predicting-employees-turnover/assets/57073572/c737351b-1390-4955-9ea5-0af6450acbb7)

The disparity in the results create some *imbalance* in this dataset. However, it's not too imbalanced so we can build a model on this data without oversampling.

Finally, some outliers have been detected (for employees' tenure) and no null values are present in the dataset.

## Model Selection 
This project requires predicting a *binary dependent variable* (if the employee leaves or not, True or False, 0 or 1) based on other *independent variables* (both categorical and numeric). Because of the nature of the project, and after conducting some *Exploratory Data Analysis* (EDA), 2 different approaches will be considered and tested one against the other.

  1) A pure **statistic model**: for this purpose a **Logistic Regression** Model will be built.
  2) A **machine learning model**: specifically, a **Random Forest** Model.

## Metric Selection
It's important to establish the right metric we want to focus on. Because the goal is to detect mainly the employees that would leave, this model should **minimize the amount of False Negatives** detected, and focus on **detecting as many negatives as possible**. Considering these requirements, **Recall** will be the main metric to measure in this model (focusing on the Negative class).


## Logistic Regression
Before building this model the outliers have been removed and the categorical variables have been transformed appropiately.

### Confusion Matrix and Recall Score

![image](https://github.com/DataGuti/Logistic-Regression-and-Machine-Learning-on-predicting-employees-turnover/assets/57073572/26cff3c0-f239-4d28-bc36-9b396d5ef864)

Out of 471 people that left, our model detected 124. Even though the Recall on this model rounds to 86%, the **recall for the negative values** is only **26%**. This means that only 26% of the employees that left were correctly detected. 
It's a considerable improvement on the current situation, but a higher percentage would be ideal for this case's purposes.


### Feature Importance

![image](https://github.com/DataGuti/Logistic-Regression-and-Machine-Learning-on-predicting-employees-turnover/assets/57073572/5980a50a-2ee7-495b-b58a-a4460e32f0da)

The most important metric seems to be the **satisfaction level**, followed by wether the employee had a work accident, their tenure and if they got a promotion over the last 5 years.
It'd be vital to *assess how this satisfaction level is being captured*.

## Random Forest

A random forest model made of 300 decision trees was used to predict the employees that leave and measure the feature importance on the turnover rate.
The best parameters for this forest were determined by using a *cross-validation technique*.

### Confusion Matrix and Recall Score

![image](https://github.com/DataGuti/Logistic-Regression-and-Machine-Learning-on-predicting-employees-turnover/assets/57073572/f9df4b02-ec82-464d-9a4d-02b7c3100578)

This time, the model detected 459 out of 498 negatives. That's an enormous improvement compared to the logistic regression model.
The **recall** for this model is of 98%, and **92% for the negative values**. This means it identified 92% of the people that left the organization.
Even though there's room to suspect this model is somewhat *overfit* (due to the high scores), it's still showing great potential considering the resources and requirements of this case.

### Feature Importance

![image](https://github.com/DataGuti/Logistic-Regression-and-Machine-Learning-on-predicting-employees-turnover/assets/57073572/72c5edb2-079e-4795-983e-68073fb5a9f5)

Again, the **satisfaction level** seems to be the most relevant metric when it comes to turnover rate. In this case, it's followed by the number of projects an employee is assigned to, the score they received on their last evaluation, their tenure and finally their average monthly hours. This model doesn't consider the other variables relevant for the result.

## Conclusions

The **Random Forest** predictive model has significantly **outperformed** the Logistic Regression one and shows a lot of potential to increase this organization's employee retention. 
The key metric of both models is the satisfaction level, so the integrity of it should be measured to validate the models.
It seems most problems could be fixed by **improving the current management strategies** of this organization. The recommendations should be carried **equally across the whole organization**, since there's no clear difference on leave rates across different departments.

## Actionable Next Steps and Recommendations

  - Conduct **exit surveys** to get more information on people that leaves the company (to *balance* the model).
  - Create a policy to consistently **measure and follow-up on satisfaction levels** across the whole organization.
  - Establish a **limit to the amount of projects** assigned to employees (preferably 3 or 4 projects).
  - Try to achieve a **balance of around 200 monthly hours** on average by establishing a limit to the bonus hours (or reward them to make up for it).
  - **Review promotion policies**, since there's a little percentage of employees who got promoted and it has a considerable correlation to the leave rate. Focus specially (but not only) on the people with 6 years or less within the company.
  - Establish a policy to **review salaries periodically**, focusing specially on people with *low* and *medium* salaries.

## Future lines of work on the models

  - Both models are **heavily influenced by the satisfaction level**. If this metric wasn't available, both models should be refactored to adapt.
  - Since there's no clear correlation between the department and the leave rate, the logistic regression model could be modified to ignore this feature and focus on the rest.
  - With more data available on people that leave, the dataset could be *balanced* and both models could be reevaluated again to improve on the current model.
