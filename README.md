# LAB3

*MICHELA PIROZZI - 732531
FERIOLI SARA - 733105*

## Creazione dataframe.ipynb 
This file is used to create the DataFrame 'transformed.csv' needed to be able to run 'LAB3.ipynb'. 
(Some parts refer to the second lab.)

We extract the macro categories for the economic sectors and also we decided to set only two macro categories for the type of contract, 
i.e., INDETERMINATO or NON-INDETERMINATO. Then we proceed to Label Econcoding, using principally two methodologies:
  * Label Encoder;
  * Encoding Manually Ordinal Categorical Features. 

We remove the outliers, for the features ETA and ANNO. 

We transformed the features we want to get as output, into a single new feature, called 'output'. 

*This notebook creates a new DataFrame, which will be downloaded with the name 'transformed.csv', and then loaded into the 'LAB3.ipynb' notebook.
We provide this new DataFrame by email, to speed up the execution of the 'LAB3.ipynb' notebook.*

## LAB3.ipynb

### Goal

1. Given the features in the dataset, what is the best combination to have a new contract? Was the feature combination the same even before covid?

2. Predict number of contracts. Is the number of contracts predicted for the future in 2019 the same or similar to the actual data given the occurrence of COVID?

### The code

As a first point, it is evaluated whether the DataFrame is balanced, according to the contract type. 
We note that it is not and therefore proceed with balancing by 'Random Undersampling'. We use undersampling instead of oversampling because we care more about the INDETERMINATO's contracts which have less occurencies, even if there are the possibilities to lose some informations.

We used the *'train_test_split'* method to split the dataset into train set (70%) and test set (30%). 

In order to solve the first goal, we needed a classification model, so we chose to use the Decision Tree and the K-Nearest Neighbors Classifiers. 

As for the Decision Tree, we implemented two different methods to identify the best parameters: 
 * Find the best max_depth
 * Best Depth Tree \n
The complexity of the Decision Tree is very high, so we implemented tree pruning to reduce or avoid overfitting.
This last part we were not able to execute because they took too long (we never got an output).

Regarding the second goal, we used several models, to determine which one is best for our dataset, through a section of Compare. 
The used models are:
 * ARIMA/SARIMAX
 * Holt winter
     * Simple exponential smoothing - ses
     * Double exponential smoothing - des
     * Triple exponential smoothing - tes
 * Extra trees regressor
 * Linear regression
 * Support Vector Regressor - svm
 
To compare the models, we use:
* MAE: Mean Absolute Error is the average over the verification sample of the absolute values of the differences between forecast and the corresponding observation.
* RMSE: Root Mean Squared Error is the square root of the mean of the square of all of the error.
* MAPE: Mean Absolute Percentage Error is a measure of prediction accuracy of a forecasting method in statistics.

As a last step, we selected only pre-COVID years (before 2019) and made the predictions on them, without the influence of the test set, then compared the result with what actually happened. 

As we can see in the graph, the COVID situation led to decrease in the number of contracts, compared to the prediction based on data through 2019.





