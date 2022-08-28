# 6301-Project-Group-26

# Credit Line Increase Model Card

### Basic Information

* **Person or organization developing model**: 
   - Brenden Moore, `brendenmoore@gwu.edu` 
   - Pavneet Singh, `pavneet@gwu.edu`
   - Sai Chaithanya Vadakattu, `saichaithanya.vadakattu@gwu.edu`
   - Bader Albaarrak, `bader.albaarrak@gwu.edu`
* **Model date**: August 28, 2022
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [DNSC_6301_Project_Group_26.ipynb](DNSC_6301_Project_Group_26.ipynb)

### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data

* Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

### Model details
* **Columns used as inputs in the final model**: 'LIMIT_BAL',
       'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1',
       'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6',
       'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: 'DELINQ_NEXT'
* **Type of model**: Decision Tree 
* **Software used to implement the model**: Python, scikit-learn
* **Version of the modeling software**: 0.22.2.post1
* **Hyperparameters or other settings of your model**: 
```
{'ccp_alpha': 0.0,
 'class_weight': None,
 'criterion': 'gini',
 'max_depth': 6,
 'max_features': None,
 'max_leaf_nodes': None,
 'min_impurity_decrease': 0.0,
 'min_samples_leaf': 1,
 'min_samples_split': 2,
 'min_weight_fraction_leaf': 0.0,
 'random_state': 12345,
 'splitter': 'best'}                      
```
### Quantitative Analysis


#### Correlation Heatmap
![heatmap](https://user-images.githubusercontent.com/111528985/186749712-2a383217-aa9d-4e53-92ab-71e203a34bee.png)

* Whiter color in the correlation heatmap represents that the variables are positively correlated.
Darker colors represent that variables are negetively correlated that is if one variable value goes up, other variable value will go down

* The heatmat represents the correlation between the race and outcome and this is a ethical issue of the data provided

![iteration plot](https://user-images.githubusercontent.com/111528985/186750717-67c8d6f3-65ac-45ac-ae99-c1b7d9ea8029.png)

* The iteration graph shows that till the tree depth 6, the graph line of Training AUC and Validation AUC have little error which is feasible model. As the tree depth increases then the error is increasing and both the curves are having more deviation.

![variable importance](https://user-images.githubusercontent.com/111528985/186750828-b5d82249-9db2-405f-91ad-4e4f1e0f1540.png)

![iteration plot 2](https://user-images.githubusercontent.com/111528985/186750922-9d3b59c7-07d5-443d-a5cc-cd1ce32bcbb2.png)


### Ethical Considerations 
* Potential Negative Impacts 
   - Math or software problems:
      - Google Collaborate has questions regarding privacy, but only users with permission to view/edit the file can use it
      - With a large reputation to uphold, Google has invested heavily into making their Open Source software safe and private
      - Possibility of data points either being missing, misinterpreted, or purposely altered
      - Thousands of possible data set combinations lead to questions about output validity and optimacy 
   - Real-world risks: who, what, when or how
      - Data set relies heavily on September data 
      - The data outcome is heavily correlated to race

* Potential Uncertainties
   - Math or software problems
   - Real-world risks: who, what, when or how
      - With a data set that centers around demographical data, uncertainties around implicit biases arise
      - Each population should be treated fairly, and when it comes to decision making, a person should not be approved or denied based on the previous actions of people of the similar demographic
      - 
* Unexpected Results 
     - The data outcome is heavily correlated to race

