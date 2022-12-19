# 💻2022-2-Machine-Learning-Project💻
2022-2 Machine Learning Project ( Team Crong )

## 0. Instruction
✅ We wrote the code on Google Colab. Here is our Colab notebook.

https://colab.research.google.com/drive/1zJUm-ulgHRSWLjiItuUfvvxZxjyxWD3K?usp=sharing

✅ You can reproduce our code in this notebook.

✅ Each time the runtime is restarted, the value of performance metric may change.

## 1. Problem Statement
### 1-1. Problem Definition
![image](https://user-images.githubusercontent.com/78165538/208300424-e75a7501-2a45-45d2-b645-357763577883.png)

We noticed the main cause of medication errors as medical staff’s mistake. To prevent such accidents, we decided to apply a model that prescribes medications that are appropriate for a specific patient.

### 1-2. Project Outline
![image](https://user-images.githubusercontent.com/78165538/208300440-9a4c73d6-0098-4eb6-b4c2-6ed5c93eb6bb.png)

## 2. Chosen Model
![image](https://user-images.githubusercontent.com/78165538/208300467-de763799-1220-4ba2-a09e-93eaba5075cc.png)

To examine the highest accuracy, we compared 4 candidates, including decision tree, random forest, svm, and naïve bayes.

![image](https://user-images.githubusercontent.com/78165538/208300525-46b7ccad-914a-4823-8d02-2501c71e95de.png)

This graph shows training and testing scores. We finally chose random forest because it showed the highest accuracy.

### 2-1. Chose Hyper Parameters
![image](https://user-images.githubusercontent.com/78165538/208300579-5b08cd9f-187e-400d-a60a-997ccb3dd640.png)

At first, we used given representative parameters as default values, and tuned them later on at the hyperparameter tuning process referring to the model performance.

## 3. Experimental Setting 
### 3-1. Dataset Settings
![image](https://user-images.githubusercontent.com/78165538/208300800-3276831f-633a-45fe-a76b-b0c44a2936da.png)

There are five input features, and the outputs are classified into 5 different types. The dataset size is 200, and we used 5-fold cross validation  for more efficient use of data.

### 3-2. Data Categorization & Splitting the Dataset
![image](https://user-images.githubusercontent.com/78165538/208300901-1fad984c-8484-4418-b2ad-e72eaff57a2a.png)

For more efficient learning, we categorized the features ourselves. Age and Na_to_K are categorized by the range as shown, and others are set as binary as we can see in the result. The dataset was split into 70% of train set and 30% of test set.

### 3-3. Smote Technique
![image](https://user-images.githubusercontent.com/78165538/208301065-2ed15a30-64bd-46cd-8fdb-1b72d495e767.png)

A problem of our dataset is that the number of drugY cases was too many. To avoid overfitting, we applied smote technique. By applying smote technique, we can conduct oversampling for our dataset.

### 3-4. Resource
![image](https://user-images.githubusercontent.com/78165538/208301096-b8fccdb3-c871-40e1-9759-9e4f57b87e77.png)

The cpu and memory was normal size, and for our project, the resource was enough.

## 4. Results
### 4-1. Hyperparameter tuning
To improve our Random Forest classifier’s performance, we do hyperparameter tuning. The target parameters and values are as below.

![image](https://user-images.githubusercontent.com/76741915/208284557-02c7e6ba-234a-4109-9a81-68c83a56a687.png)

After tuning, we get best parameters and best accuracy.

![image](https://user-images.githubusercontent.com/76741915/208284566-56e9ecc2-927f-4479-91e7-98c4a992f07b.png)

The accuracy of our model with best parameters is about 0.91. The initial accuracy of the model is about 0.879. Therefore, after hyperparameter tuning, we can get the better model.

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
