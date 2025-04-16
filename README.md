Team Members:
- Mohammed Alsary (400387023) 
- Noah Paulos (400395592)

Contributions:
- Mohammed= Questions 1,2,3,4,5,6,7,8

1. 
In this project, I worked with the UCI Heart Disease dataset to solve a binary classification problem. The original target variable, num, had values from 0 to 4, representing different levels of heart disease. I simplified it into a binary outcome: 1 for any heart disease (values > 0) and 0 for no heart disease. This made the task clearer and easier to handle using standard classification methods.

2. 
I checked the structure of the dataset using .info() and saw that all the variables were numeric and clean. There were no string or object types, and the values seemed reasonable, so I didn’t apply any transformations like scaling or encoding at this point.

3. 
The dataset had 303 observations and 13 features. Most were integers, with a few floats. Using .describe(), I found that the average age was around 54, and cholesterol levels varied a lot. A couple of features like ca and thal had missing values, but overall the data looked manageable.

4. 
To prepare for binary classification, I created a new column called target. I set it to 1 for any value of num greater than 0, and left it as 0 if the value was 0. This gave me a clear target variable to use in training the models.

5. 
To understand the relationships between features and the target, I created a heatmap of correlations. I found that variables like ca (number of vessels colored) and thalach (max heart rate achieved) had strong associations with the target. This helped me identify features that might be important for prediction.

6. 
I removed rows with missing values using dropna(), which dropped 6 rows and left me with 297 observations. This was a small loss and allowed me to move forward with a clean dataset without needing to impute missing data.

7. 
To explore hidden patterns, I used PCA on the numerical features (excluding categorical ones and the target). I visualized the first two principal components in a scatter plot, which showed some separation and suggested possible sub-groups in the data.

8. 
I split the data into training and test sets using a 70/30 split with a fixed random seed for consistency. This gave me 207 training samples and 90 test samples to evaluate model performance fairly.

- Noah= Questions 9,10,11,12,13,14,15

9. 
I chose Logistic Regression as my interpretable model because it’s straightforward and easy to explain. I also chose Random Forest as a second model because it’s more powerful and can handle non-linear relationships and feature interactions.

10. 
To measure how well the models performed, I used accuracy and F1 score. Accuracy tells me how many predictions were correct overall, while F1 score balances precision and recall, which is especially useful when the classes might be slightly imbalanced.

11. 
I trained both classifiers using GridSearchCV to tune their hyperparameters. For Logistic Regression, I tested different regularization strengths (C values), and for Random Forest, I adjusted the number of trees and max depth. I used 5-fold cross-validation during tuning to avoid overfitting.

12. 
For the third model, I used Recursive Feature Elimination (RFE) with Logistic Regression to select the top five features. I then trained another logistic regression model using only these selected features and optimized it the same way as before.

13. 
I compared all three models on the test set. Random Forest had the best performance with the highest accuracy and F1 score. The RFE-based model performed slightly worse than the full logistic regression, which showed that reducing the number of features didn’t always help in this case.

14. 
Looking at the coefficients from the Logistic Regression model, I saw that sex and ca were the strongest positive predictors of heart disease. Features like thalach and fbs had negative coefficients, suggesting that higher values in those features were linked to lower risk.

15. 
To try improving performance further, I used K-Means clustering on the PCA-reduced data to find two sub-groups. I trained a separate Random Forest for each group, and the results showed small improvements in F1 scores compared to the general model. This showed that tailoring models to different sub-groups can be useful.
