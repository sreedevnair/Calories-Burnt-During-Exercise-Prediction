# Predicting Medical Insurance Cost

In this project, we will try to predict the calories burnt by a person after doing some physical exercises. 

We will be using XGBRegressor model to train and predict the calories burnt. 

`XGBRegressor` is a part of the **XGBoost library**, which stands for e**X**treme **G**radient **B**oosting. 

XGBoost is an optimized distributed gradient boosting library designed to be highly efficient, flexible, and portable. It implements machine learning algorithms under the Gradient Boosting framework.    

`XGBRegressor` is the **regression model** in the XGBoost library. It is mainly used for predicting continuous target variables.

## Notes :-

### 1. Files
Our data is present in 2 files :-
1. *calories.csv*
2. *exercise.csv*

In *calories.csv*, we have the **User_ID** column along with **Calories** column, which represents the calories burnt by the user.

In *exercise.csv*, we have 8 columns ['User_ID', 'Gender', 'Age', 'Height', 'Weight', 'Duration', 'Heart_Rate', 'Body_Temp']

Do concatenate these 2 files, we use Pandas' function `pd.concat()`. 

Inside, first we need to pass the list of DataFrames that we want to combine. We are passing the *exercise* DF and then **Calories** column from the *calories* DF (since the **User_ID** column is already present in the *exercise* DF).

Then we need to specify the **axis**. **axis=1** means the it will combine column after column, and **axis=0** means it will combine row after row.

### 2. Checking for Null values
While pre-procssing the dataset, we first check whether any of the features have any missing values. We do this by using `.isnull()` function. This is function will return the complete DataFrame with `True` or `False` values. If the value is not present (i.e. a Null value), it will show `True`, otherwise `False`.

To check the total number of Null values present in the DataFrame, we use `.isnull().sum()`. This will return Series with the number of Null values in each column (feature).

### 3. `sns.countplot()`
It is used for visualizing the count of observations in each category of a categorical variable, mainly through bar *graph*.

### 4. `sns.distplot()`
It stands for Distribution Plot and is used for plotting distributions of continuous variables, mainly through a *histogram*.

### 5. Finding Correlation
To find the correlation between each non-categorical features, we `DataFrame.corr()` function. But before using that, we first need to drop all the categorical values as Pandas can't find correlation between them.

It will return a matrix with correlation of each column with each other.

If it's a positive correlation, that means that the features are directly correlated. If it's a negative correlation, that means that the features are inversely correlated.

### 6. Using Heatmap
The to visualize the correlation in a better way, we use a heatmap. Heatmaps are used to show relationships between two variables, one plotted on each axis. 

We create heatmaps using `sns.heatmap()` function. If the correlation between each feature is more, the darker will be the color.

### 7. Encoding Data
Since we have a categorical feature *Gender* in our dataset, we can need to convert that before training our model. To to this, we use `DataFrame.replace()` function. 

Inside this function, first we need to pass a dictionary. Inside this dictionary, we use column name as keys and another set of dictionary as it's value. Inside the nested dictionary, we pass the original values of that column as keys and the new data that we want to replace it as the value. 


### 8. Data Splitting
First, we create the *feature DataFrame* by dropping the target column, which is **Calories** from the original DataFrame and saving it in a new DF. Then we create a *target Series* by only selecting the target column and saving it in a new DF.

Then we use the Seaborn's function `.train_test_split()` to split the dataset into training dataset and testing dataset.


### 9. Model Training
Once we have splitted our data, we will train our model using `XGBRegressor()` class. 


### 10. Prediction Evaluation
After predicting the target values, we evaluate our model by finding it's Mean Absolute Error. To find the MAE, we use the function mean_absolute_error() that we imported from sklearn.metrics.

<br>

---------
