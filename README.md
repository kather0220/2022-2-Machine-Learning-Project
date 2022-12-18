# 💻2022-2-Machine-Learning-Project💻
2022-2 Machine Learning Project ( Team Crong )


## 4. Results
### 4-1. Hyperparameter tuning
To improve our Random Forest classifier’s performance, we do hyperparameter tuning. The target parameters and values are as below.

![image](https://user-images.githubusercontent.com/76741915/208284557-02c7e6ba-234a-4109-9a81-68c83a56a687.png)

After tuning, we get best parameters and best accuracy.

![image](https://user-images.githubusercontent.com/76741915/208284566-56e9ecc2-927f-4479-91e7-98c4a992f07b.png)

The accuracy of our model with best parameters is about 0.902. The initial accuracy of the model is about 0.879. Therefore, after hyperparameter tuning, we can get the better model.

### 4-2. Compare the results before & after hyperparameter tuning
Now, let’s compare the results before and after hyperparameter tuning.
The accuracy, precision, recall and f1-score changed as follows. As you can see, all values increased slightly. If you want to check the exact code, please refer to the our ipynb file.

![image](https://user-images.githubusercontent.com/76741915/208284589-cca64666-363d-41c3-883f-37baad663d1b.png)

Here is the confusion matrix. There was no significant change, but the accurate predictions corresponding to the diagonal elements increased slightly.

![image](https://user-images.githubusercontent.com/76741915/208284593-63f7302b-5d11-4379-b7bb-d60cf8b1b3ec.png)

Next is the ROC curves. The closer the graph is to the upper left, the better the performance. You can see that some graphs have gone up to the upper left after hyperparameter tuning.

![image](https://user-images.githubusercontent.com/76741915/208284604-784256d7-ecf7-49a7-a780-6cafac20a005.png)

Here is the PR curves. The closer the graph is to the upper right, the better the performance. You can see the graph have gone up to the upper right after hyperparameter tuning.

![image](https://user-images.githubusercontent.com/76741915/208284607-a0292054-6b9b-4be3-b7ed-8509d6ad63d8.png)

These are the feature Ranking. As you can see, after hyperparameter tuning, “Na_to_K_binned_20-30” got more importance. But overall, “Blood Pressure” is still the most important feature. Besides that, “Cholesterol_NORMAL” and “Na_to_K_binned_10-20” is less important than before. The yellow features are the ones that have changed.

![image](https://user-images.githubusercontent.com/76741915/208284615-d62d09e9-71aa-4b31-af2c-7a1b33d490af.png)

As a result of comparing performance using evaluation metrics, it can be said that performance has improved after hyperparameter tuning.

### 4-3. Predicting New Data
We wil check if our new model prescribes to new patient properly. Let’s set the new patient’s feature list, and predict on that data.

![image](https://user-images.githubusercontent.com/76741915/208284624-4c42784c-5912-476e-a4ed-5fa480940860.png)

As we expected, the drugY is prescribed to the new patient. This shows that our new model presribed well enough to new patients.

## 5. Interpretation
### 5-1. Correlation between features and the type of drug predicted by the model
Now let's look at the relationship between our model's predictions and the input features. The correlation graphs between each feature and drug type are as follows.

![image](https://user-images.githubusercontent.com/76741915/208284638-f3126136-80df-4bc8-b7c9-28e527cff93b.png)

- drugC and drugA are not taken by the children and teenager, whose ages are between 0 and 19.
- drugA is taken only by the younger than 50 years old.
- drugB is taken only by the older than 50 years old.
- DrugY is taken by all ages.

![image](https://user-images.githubusercontent.com/76741915/208284647-c39f74cf-0ace-4ed9-aa95-cac528da39a7.png)

- Male people got drugA, drugB and drugC more than female people did.
- Female people got DrugY and drugX more than male people did.
- Just by this, 'sex' becomes quite appropriate feature for classification compared to beginning.

![image](https://user-images.githubusercontent.com/76741915/208284658-c62833a5-03e7-477a-8c83-7056d87f70b2.png)

- drugA and drugB were given only to people with HIGH blood pressure.
- drugC was given to people with LOW blood pressure.
- drugX was Not given to people with HIGH blood pressure.
- Still, BP is an important feature for classification.

![image](https://user-images.githubusercontent.com/76741915/208284670-d513417a-3225-4ae8-949a-37803709e029.png)

- People with Na_to_K ratio bigger than 20, got DrugY.
- Still, Na to K is an important feature for DrugY classification.

![image](https://user-images.githubusercontent.com/76741915/208284677-5f841b98-eabd-4373-a328-63bd5dbdab9f.png)

- drugC was only given to people with HIGH cholesterol.
- Cholesterol is an important feature to classify drugC.
- Compared to the beginning, drugA and drugB is almost given to the people who have Normal cholesterol.
- Therefore, drugA and drugB become an important feature to classify drugA and drugB.

### 5-2. Cause of misclassification
As shown below, 9 misclassifications occurred for a total of 60 test sets.

![image](https://user-images.githubusercontent.com/76741915/208284692-c64a3f76-eecb-4429-bc1d-1dd06a9af335.png)

Then, let’s see the feature distributions of misclassified data.

![image](https://user-images.githubusercontent.com/76741915/208284701-90d9a0be-97d1-4580-9ae1-1a3454ccce86.png)

There was no significant difference between the misclassified data, and the predicted result values did not show any obvious tendencies.
One notable point was that Na_to_K 10-20 took a substantial proportion. This seems to be due to the ambiguity that can be classified into all drug types if they belong to this group. Also, people who should have been prescribed DrugY were likely to be misclassified, which is suspected to be due to the universal range of data.
Therefore, the cause of the misclassified data is thought to be the ambiguity of classifying boundary values.

### 5-3. Conclusion

![image](https://user-images.githubusercontent.com/76741915/208284705-da83e591-c08f-4f1b-80d2-8b20b5dcd7e0.png)
