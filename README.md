# Linear Regression


## Our Data
Practicing single linear regression on beer data set. 

## Plotting our Data
We will be trying to predict total calories wight grams of Carbohydrates. 

 ![Image!](Images/scatter-plot.png)

## Correlation of Variables

```
import scipy.stats

x = df['Carbohydrates']
y = df['Calories']
scipy.stats.pearsonr(x,y)
```


**Pearson's R: .7979**

## Checking For Normality

### Quantile-Quantile Plot

![Image!](Images/QQ%20Plot.png)
**Interpret QQ Plot**

We can try normalizing the data further by applying a **log function**?

## Train-Test-Split Data
```
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=.33,random_state=42)
```

## Create and Fit Linear Model
```
from sklearn import linear_model
reg = linear_model.LinearRegression()
reg.fit(x_train,y_train)
```

## Linear Model
### Calories = 69.158 + (Carbohydrates * 7.040)

## Manually Calculating RMSE
```
# append all residuals to a list
import math

residuals = []
for i in range(len(y_pred)):
    residual = abs(y_pred[i] - y_test[i])
    residuals.append(residual)
```

```
# calculate root mean squared of all residuals
import math
import statistics
def rmse(param):
    
    val = 0
    for each in residuals:
        val += each**2
    mean = val/len(residuals)
    return math.sqrt(mean)  
```
**RMSE** = 21.767

Checking MSE calculation
```
from sklearn.metrics import mean_squared_error
print(mean_squared_error(y_test,y_pred))
```
**MSE** = 473.779

Taking the root of **MSE** we can see that we correctly calculated it. 

## Plotting Model Over Our Data
![Image!](Images/plotted-model.png)

# Other

## Understanding Pearson's R vs Spearman's Rho?

- Correlation is the degree to which two variables are linearly related. 
- Important to remember that correlation doesn't imply causation.
- Pearson's R ranges from +1 to -1
- Spearman's rank correlation coefficient is a nonparametric measure of rank correlation
    - Spearman's rho explains how well two variables can be described using a montonic function


### What is a montonic relationship?

"A monotonic relationship is a relationship that does one of the following:

(1) as the value of one variable increases, so does the value of the other variable, OR,

(2) as the value of one variable increases, the other variable value decreases.

BUT, not exactly at a constant rate whereas in a linear relationship the rate of increase/decrease is constant."

#### Example of Monotonic Relationship
![Image!](Images/monotonic-relationship1.png)![Image!](Images/monotonic-relationship2.png)![Image!](Images/monotonic-relationship3.png)


## References

1. https://towardsdatascience.com/clearly-explained-pearson-v-s-spearman-correlation-coefficient-ada2f473b8

2. https://www.youtube.com/watch?v=LSmjQNsCbFs&ab_channel=SpencerPao

3. https://www.wikiwand.com/en/Monotonic_function