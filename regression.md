# Linear Regression 

Linear regression is one of *the simplest and most common* machine learning algorithms. It is used to predict continuous/real variables, by **evaluating and quantifying the relationship between dependent and independent variables**. 

>Despite being simple, we have to observe some details that are requirements for the model to work well and also understand what to do in case the model suffers from overfitting.

First of all, for this model to work there must be a correlation between measurable characteristics and the target variable. In descriptive statistics, the correlation between variables is given by **Pearson's correlation coefficient**, or simply "Pearson's ρ". It measures the degree of correlation (and the direction of that correlation - whether positive or negative) between two variables metric scale (interval or ratio/ratio). This coefficient only takes on values between -1 and 1, and cannot be used to find cause relationships.

Some regression models are:
-	**Simple linear regression** 
There is only one independent variable 𝑦 = β0 +β1𝑥 + ε
-	**Multivariate linear regression (MLR)**
There is a number of explanatory variables 𝑦 = β0 + β1 x1 + ⋯ +β𝑚 x𝑚 + ε
-   **Polinomial regression**
It is a special case of MLR, performs well with no linear data 𝑦 = β0 + β1𝑥 + β2𝑥² + β3𝑥³ + ⋯ + ε

Where 𝑦 is the dependet variable (the target), x is the independent variable, β0 is the intercept, βs are the angular coefficients and ε is the error. 

The regression models used **the least square method (LSM)** to find the best fit curve or line for the set of data given by reducing the sum of the squared errors. This method looks for the values of βs so that the predicted values are closer to the actual values. A highlight of this method is that the error is penalized by being computed its squared value.

Another way to find the best fit for the model is by using **descending gradients**. This method finds the regression parameters that give the smallest error value by analyzing the slope of the error curve (that is, its derivative) in an automatic way.

## How do we know we can use linear regression models?

To use linear regression, **we need to assess four assumptions**, which are illustrated in Figure 1. The violations of these requirements can lead to various types of problematic situations such as estimates can become biased, the least square method may not be efficient anymore and the confidence intervals might become untrustworthy.

*Figure 1 – Assumptions of linear regression* 

<img src="images\regression\assumptions.png" /> 

*From: SuperDataScience*

**1.    Linearity**: The relationship between every independent variable Xi and the dependent variable Y is assumed to be linear when the other variables are held constant;<br>
**2.	Homoscedasticity:** The variance of the errors is the same for any combination of values of the independent variables;<br>
**3.	Normality:**  All errors are normally distributed around zero;<br>
**4.	Independence:** The errors ε1, ε2, …, should be independent of one another, that is, they have no correlation. <br>
- *No multicollinearity*: It is an extension of the linearity assumption, the independent variables cannot be correlated to one another;
- *Outlier check*: Analyze discrepant observations as they impair the efficiency of the model.


**Breaches of linearity and independence assumptions may result in biased, inconsistent, and inefficient estimates, making it crucial to verify these assumptions.** While violations of the other two assumptions have less severe consequences, as estimates remain consistent and unbiased. For instance, when the normality of errors is not checked, the least squares method is most efficient within the class of linear estimators that provide consistent outcomes, but the p-values could be biased.

Various methods are available to examine the four assumptions of the regression model, with graphical approaches being preferred. Linearity can be assessed through scatterplots or residual plots, while residual plots also offer an excellent visual evaluation for homoscedasticity. Normal probability plots, or QQ plots, offer a good method for checking normality and lastly, the independence assumption can be verified by examining the autocorrelation function of the residuals.

>Note that **residuals** are the differences between the observed values and the values predicted by the sample regression model, whereas **errors** denote the difference with the values predicted by the population regression model.
 
*Figure 2 – Residual plots*
*a) good residual plot, b) no homoscedasticity, c) no linearity.* 

<img src="images\regression\residuos.jpg" /> 

## The model is perfect in training, but awful in testing. What to do?

Usually, to get a good fit for the data, we increase the complexity of the regression model. However, by doing so, we run the risk of **overfitting** the model. In this case, the model decorates the training set in a way that it cannot make good predictions for unseen data, it does not generalize, showing bad results on the testing set. That difference between testing and training results is called **high variance**.

To *avoid* overfitting, we can add some parameters that penalize complexity, forcing the model to increase bias, by using **regularization techniques**. In this way, it is good to keep in mind that the test metrics will be improved, but the training metrics could became worse. The regularization techniques are ridge (L1) and lasso (L2), and they basically work by shrinking very high coefficients (βs). 

>*The regularization increases the bias of the model and consequently, decreases its variance.*  

The regularization process functions by applying an extra penalty to the model while it is training. Besides attempting to minimize the sum of squared differences between the actual y and the predicted y using least squares, the training also aims to lower this penalty. 

The primary distinctions between L1 and L2 regularization are:
- **Lasso** (L1): The penalty is equal to the sum of the absolute values of Bs. In this case, the coefficients βs can reach zero, thereby eliminating such features from the model.
- **Ridge** (L2): The penalty is equal to the sum of the squared values of Bs. In this case, the coefficients βs cannot reach zero. 

The **lambda parameter** (also known as alpha) controls the magnitude of the penalty applied to the coefficients. The higher the alpha, the lower these coefficients' values. Alpha must be selected with caution since it can lead to underfitting if chosen incorrectly. The best approach for determining the alpha value is through *cross-validation*, where multiple alpha values are tested, and the one yielding the lowest error in predictions is chosen.



**References**:

MAULUD, D. 2020. A Review on Linear Regression Comprehensive in Machine Learning.

ERNST AF, ALBERS CJ. 2017. Regression assumptions in clinical psychology research practice—a systematic review of common misconceptions. PeerJ 5:e3323 https://doi.org/10.7717/peerj.3323



	
