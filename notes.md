# Supervised Learning
* Training ML models using data that is labelled
* Categorical and Numerical Data
    Numerical Data : continous form like price of stock
    Categorical Data : grouped data like gender, race etc
* Handle Categorical Data in SL?
    Label Encoding done -> categorical data is mapped to some numericl data and hence replaced by it 
* Handle missing values in data:
    Understand the pattern of the data and then use techniques like average filling, forward filling etc
* Imputation of missing data:
    Replacing the missing data w a certain value.
    Can remove the entire row if volume of such missing data is v less
    Can fill the missing values using avg or mean of the col, or the min, max or mode values
* Outliers in dataset:
    Points that are out of the general data distribution
    Unlike missing values or wrong values, outliers will run perfectly on the model but will cause the model to have huge variance and further bring instability and reduce the general performance of the model
*How to deal with outliers:
    1. interquartile reange (IQR): 
        identify the first quartile and the third quartile , calculate the IQR by :(Q3-Q1) and then remove all the points that are beneath:
        (Q1-1.5) * IQR or the points that are above 
        (Q3+1.5)*IQR
    2. Z-score technique: 
        Calculate the z score by the formlule :
            z-score for point X = (X-u)/sigma where u = is the mean and sigma is the std deviation

        we remove all the points that have z-scores more/less than +3/-3 as they are considered as an outlier
    3. Percentile Method: Anything above as 99%ile and below the 1%ile is taken out as outlier

* Curse of dimensionality : 
    > size of feature set increases -> model's performance and the compute performance averages out with no further improvement and eventually the performance decreases

* Data Scaling:
    Put data in the range of certain values
    Make sure data follows a certain format
    1-100 million units of data -> 1-100 or even 0-1
    helps model to process things faster and effeciently
    The features with large values cannot dominate the model's learning process
    L1 and L2 are used as regularizatoin where they reduce or penalize the large coefficient values

    > L1 and L2
    L1: Lasso : adds the sum of the absolute values of the coefficients to the loss function, effectively penalizing the magnitude of coefficients linearly. This causes some coefficients to shrink exactly to zero, promoting sparsity in the model and performing implicit feature selection.

    L2: Ridge :  adds the sum of the squares of the coefficients to the loss function. It penalizes large coefficients more strongly than small ones (quadratically), shrinking all coefficients toward zero but without setting any exactly to zero. This keeps all features but controls their scale.

    L1 -> used in high dimensionlity data
    L2 ->  when you want to keep all features contributing but want to shrink their coefficients smoothly towards zero without eliminating any.

* One Hot encoding: 
    Cat variable -> model friendly format 

    Feature gender has male, female and others
    OHE: will split into three more cols

* When label encoding and when OHE?
    Label Encoding -> Oridnal data, where the data has a natural order or ranking -> Low medium and high
    Only one column replaces the original column

    Use in tree based algos

    OHE -> Converts each cat to separate binary feature column marking presence w 1 and absence w 0.
    Use in lr, knns etc

* How to handle class imbalance in the dataset:
    1. Random Undersampling reduces imbalance by randomly removing samples from the majority class, making class distributions more balanced but risking loss of valuable information.
    2.Random Oversampling duplicates samples from the minority class randomly with replacement, increasing minority class representation but potentially causing overfitting by replicating identical points.​
    3. Synthetic Oversampling (SMOTE):Synthesizes new minority class samples by interpolating between existing minority instances and their nearest neighbors.

* What is Bias?
    Bias is a systematic error caused by incorrect assumptions in the model, such as assuming a linear relationship when the actual relationship is more complex.

    High bias means the model oversimplifies the data—it can't capture important patterns and thus performs poorly on both training and new data.

    Bias can result from model choice (using a simple model that can't represent complex data), as well as from incomplete or unrepresentative data.

    It causes the model to consistently deviate from the true values because it "ignores" some relevant information or relationships present in the dataset.


* Feature engg / data pre processing:
    Process of deriving or enriching the existing features of the model in  way so that it can be consumable by the model

    eg., there is column -> age and this age is required to know the fact that whether the customer is eligible for loan or not. So it is beteer to convert the age col into a cat binary column if the customer ` is_eligible_for_loran_yes_or_no` and pass the col to the model for training

* How to determine the imp of features in SL task?
    1. Permutation Importance: This method measures the decrease in model performance when values of a feature are randomly shuffled. A large drop in performance indicates the feature is important.
    2. Filter Methods: Use statistical measures such as correlation or mutual information between features and target to rank and select features before model training.

# Regression
* What is p-value?
    First let us understand what is null hypothesis in regression.
        In regression analysis, the null hypothesis typically states that there is no effect, or in more technical terms, that a specific coefficient is equal to zero.
        A low p-value (typically less than 0.05) indicates that you can reject the null hypothesis, suggesting there is a meaningful relationship between the independent variable and the dependent variable.
        A high p-value means there is not enough evidence to reject the null hypothesis, implying the variable may not have a significant effect on the target. 

* Homoscedasticity?
    It means the residuals (differences between observed and predicted values) have the same amount of variability no matter the value of the predictor.


* What is Multicollinearity and how to remove it
    Multicollinearity in multiple linear regression occurs when two or more independent variables are highly correlated, making it difficult to isolate the individual effect of each variable on the dependent variable. This can lead to unstable coefficient estimates and reduce the model's interpretability.

    Remove it using:

    Remove Highly Correlated Variables: Identify variables with strong correlations (using correlation matrix or Variance Inflation Factor (VIF) scores) and remove some of them to reduce redundancy.

    Combine Variables: Use techniques like Principal Component Analysis (PCA) to transform correlated variables into a smaller set of uncorrelated components.

    Regularization Techniques: Apply methods like Ridge Regression or LASSO, which add penalty terms to the regression to shrink coefficients and handle multicollinearity effectively.

* Variance Inflation Factor
    Measure multicollinearity in multiple regression models
    
    > VIF = 1/(1-R^2)
    where R is the coefficient of determination
    VIF -> 1  ~ no relation w other variables
    If R**2 is -> 1 ~ VIF -> large -> high multicollinearity

* What is Autocorrelation (serial correlation) and how it is checked?
    Situation in which the error terms of one observation are affected by error terms of nearby observation.

    test that is used to check it is called "Durbin-Watson Statistic".
    d<2: positive correlation -> errors depend positively on each other
    d ~= 2: no dependency
    d>2 : negative autocorrelation

* Polynomial regression
    variable depends on other variables, at least
    of a polynomial of some certain degree


// to study today:
GB Tress
ADABoost 
Model Eval
