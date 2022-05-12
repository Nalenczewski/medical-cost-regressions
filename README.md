![](./README_files/medical.jpg)

# Medical Cost Regressions
## Contents
1. **Introduction**
2. **My Approach**
3. **Findings**
4. **Ideas for Further Research**
5. **Recommendations**

## 1. Introduction
Today, medical costs are skyrocketing. Measures must be taken to decrease the financial burden on patients and their families. Through analyzing medical data, it is hoped that ways of cutting costs may be found.

**About the Dataset**

The data in this analysis comes from the public domain. It contains the below variables.

* Age: the age of the patient.
* Sex: the gender of the patient.
* BMI: the patient's body mass index.
* Children: the number of the patient's children.
* Smoker: whether the patient is a smoker or not.
* Region: the patient's U.S. residential area.
* Charges: the pateint's medical costs.

## 2. My Approach

**Exploratory Data Analysis**

I first conducted EDA in order to derive insights from the data. I looked at basic things, such as the cardinality of each variable, the number of unique values of each variable, a heatmap showing correlations between variables, and a detailed look at the correlated variables.

**Machine Learning**

I first created X and y variables by making Charges the target variable. I then pre-processed the numerical data (BMI and age) using Min Max Scaler and Standard Scaler to compare performance. Then I applied several different regression models: linear, lasso, and ridge regression, decision tree and random forest, AdaBoost decision tree, and support vector machine. I then compared the results to determine the optimal model.

## 3. Findings

**Exploratory Data Analysis**

There was no missing data and were no outliers. The only variables that were corrolated were charges with smoking (smokers had higher charges). Smokers made up for more than half of the charges above $15,000.

**Machine Learning**

The results of the best performing model of each type are below. Random Forest with max depth of 3 and 400 estimators performed the best.


```python
%store -r final_results
final_results
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Training R2</th>
      <th>Test R2</th>
      <th>Training RMSE</th>
      <th>Test RMSE</th>
    </tr>
    <tr>
      <th>Model</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Linear Regression</th>
      <td>0.756279</td>
      <td>0.734275</td>
      <td>6055.905613</td>
      <td>5978.637219</td>
    </tr>
    <tr>
      <th>Decision Tree</th>
      <td>0.860714</td>
      <td>0.836862</td>
      <td>4578.104656</td>
      <td>4684.505601</td>
    </tr>
    <tr>
      <th>Random Forest</th>
      <td>0.865829</td>
      <td>0.845451</td>
      <td>4493.268535</td>
      <td>4559.522879</td>
    </tr>
    <tr>
      <th>Support Vector Machine</th>
      <td>-0.099704</td>
      <td>-0.080650</td>
      <td>12863.832512</td>
      <td>12056.701488</td>
    </tr>
    <tr>
      <th>AdaBoost</th>
      <td>0.863211</td>
      <td>0.840023</td>
      <td>4536.886634</td>
      <td>4638.898958</td>
    </tr>
  </tbody>
</table>
</div>



## 4. Ideas for Further Research

* Try to gather more data and see if there are any other major predictors of charges.

## 5. Recommendations

* Consider having people who smoke pay higher premiums and lower the premiums of non-smokers. 
* Consider letting people with lower BMI and age pay less for health insurance.
