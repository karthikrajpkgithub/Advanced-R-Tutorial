# Weight Prediction Using Height Value

## Linear regression

Linear regression is used to predict the value of an outcome variable y on the basis of one or more input predictor variables x. 

Used to establish a linear relationship between the predictor and response variables.

Predictor and response variables are related through an equation in which the exponent of both these variables is 1. 

Mathematically, a linear relationship denotes a straight line, when plotted as a graph.

### Equation for linear regression:
``` 
y = ax + b  
```
> y is a response variable.
> 
> x is a predictor variable.
> 
> a and b are constants that are called the coefficients.
### Let's gather values of height and weight & create vectors x & y.
```
> x <- c(141, 134, 178, 156, 108, 116, 119, 143, 162, 130)  
> y <- c(62, 85, 56, 21, 47, 17, 76, 92, 62, 58)  
```
### Then, We will use the lm() function and pass the x and y input vectors and store the result in a variable named relation_model.
```
> relation_model <- lm(y~x)
> print(relation_model)
```
### Output
Call:
lm(formula = y ~ x)

Coefficients:
(Intercept)       x  
47.50833      0.07276  

### Now, let's use the summary() function to get a summary of the relation_model to understand the average error in prediction, known as residuals.
```
> print(summary(relation_model))
```
### Output
Call:
lm(formula = y ~ x)

Residuals:
    Min      1Q  Median      3Q     Max 
-38.948  -7.390   1.869  15.933  34.087 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept) 47.50833   55.18118   0.861    0.414
x            0.07276    0.39342   0.185    0.858

Residual standard error: 25.96 on 8 degrees of freedom
Multiple R-squared:  0.004257,	Adjusted R-squared:  -0.1202 
F-statistic: 0.0342 on 1 and 8 DF,  p-value: 0.8579

### Finally, Let's predict the weight of a "ashok" with height 175cm using the predict() function.
```
> ashok <- data.frame(x=175)
> weight_of_ashok <- predict(relation_model,ashok)
> print(weight_of_ashok)
```
### Output
       1 
60.24115 
### Prediction results plot with the help of the plot() function.
```
plot(y,x,col = "red",main = "Height and Weight Regression",abline(lm(y~x)),cex=1.4,pch = 16,xlab = "Weight in Kg",ylab = "Height in cm")
```
![Rplot](https://user-images.githubusercontent.com/65169267/112146681-dddc7280-8c01-11eb-98dd-2f348fd5111a.png)
