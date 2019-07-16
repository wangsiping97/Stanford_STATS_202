# Homework 2

<center>
  Siping Wang 006405652
</center>

## Problem 1

If we know that
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}
$$
then,
$$
1-p(X) = 1- \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}} = \frac{1}{1+e^{\beta_0+\beta_1\textbf{x}}}
$$
So
$$
\frac{p(X)}{1-p(X)} = e^{\beta_0+\beta_1\textbf{x}}.
$$


Similarly, if we know that
$$
\frac{p(X)}{1-p(X)} = e^{\beta_0+\beta_1\textbf{x}},
$$
we can solve that
$$
p(X) =e^{\beta_0+\beta_1\textbf{x}} \times (1-p(X))
$$
then
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}.
$$

## Problem 2

**(a)**

We can conclude from the question that:

- If $x \isin [0.05, 0.95]$, then the observations we will use are in the interval $[x-0.05, x-0.95]$. 
- If $x\isin [0, 0.05)$, then the observations we will use are in the interval $[0, x+0.05]$. 
- If $x \isin (0.95, 1]$, then the observations we will use are in the interval $[x-0.05, 1]$. 

So the average fraction is, 
$$
\int\limits_{0.05}^{0.95}10dx+\int\limits_{0}^{0.05}(100x+5)dx+\int\limits_{0.95}^{1} (105-100x)dx = 9.75.
$$
**(b)**

The fraction of the available observations will we use is
$$
9.75\% \times 9.75\% = 0.950625\%.
$$
**(c)**

We will use $(9.75\%)^{100} \approx 0$ of the observations to make the prediction. 

**(d)**

The fraction of observations available with $p$ features or parameters is $(9.75\%)^{p}$.

So when $p$ is very large, the fraction will be
$$
\lim_{p\to\infty}(9.75\%)^p = 0.
$$
**(e)**

- Given $p=1$, we have $l=0.1$. 
- Given $p=2$, we have $l= (0.1)^{\frac{1}{2}}$. 
- Given $p=100$, we have $l=(0.1)^{\frac{1}{100}}$.

Comment: 

When the number of features is high, to use on average 10% of the training observations would mean that we would need to include almost the entire range of each individual feature.

## Problem 3

**(a)**
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}=\frac{e^{-6+0.05\times 40+1\times3.5}}{1+e^{-6+0.05\times 40+1\times3.5}} = 0.3775.
$$
**(b)**

Let $x_1$ denotes the amount of hours the student would need to study.

Then we have
$$
p(X) = \frac{e^{\beta_0+\beta_1\textbf{x}}}{1+e^{\beta_0+\beta_1\textbf{x}}}=\frac{e^{-6+0.05\times x_1+1\times3.5}}{1+e^{-6+0.05\times x_1+1\times3.5}} =0.5,
$$
which is equivalent to 
$$
e^{-6+0.05\times x_1+1\times3.5} = 1.
$$
Solving the equation above, we can get that $x_1 = 50$. 

## Problem 4

The **logistic regression model** is better for classification of new observations. 

When using 1-nearest neighbors, the training error is 0. However, in the question, an average error rate of 18% means a test error rate of 36%, which is greater than the test error rate of  logistic regression model, which is 30%.  

## Problem 5

**(a)**

**Numerical summaries:** 

```R
> library(ISLR)
> summary(Weekly)
```

output:

```R
      Year           Lag1               Lag2               Lag3         
 Min.   :1990   Min.   :-18.1950   Min.   :-18.1950   Min.   :-18.1950  
 1st Qu.:1995   1st Qu.: -1.1540   1st Qu.: -1.1540   1st Qu.: -1.1580  
 Median :2000   Median :  0.2410   Median :  0.2410   Median :  0.2410  
 Mean   :2000   Mean   :  0.1506   Mean   :  0.1511   Mean   :  0.1472  
 3rd Qu.:2005   3rd Qu.:  1.4050   3rd Qu.:  1.4090   3rd Qu.:  1.4090  
 Max.   :2010   Max.   : 12.0260   Max.   : 12.0260   Max.   : 12.0260  
      Lag4               Lag5              Volume            Today         
 Min.   :-18.1950   Min.   :-18.1950   Min.   :0.08747   Min.   :-18.1950  
 1st Qu.: -1.1580   1st Qu.: -1.1660   1st Qu.:0.33202   1st Qu.: -1.1540  
 Median :  0.2380   Median :  0.2340   Median :1.00268   Median :  0.2410  
 Mean   :  0.1458   Mean   :  0.1399   Mean   :1.57462   Mean   :  0.1499  
 3rd Qu.:  1.4090   3rd Qu.:  1.4050   3rd Qu.:2.05373   3rd Qu.:  1.4050  
 Max.   : 12.0260   Max.   : 12.0260   Max.   :9.32821   Max.   : 12.0260  
 Direction 
 Down:484  
 Up  :605  
```

```R
> cor(Weekly[,-9])
```

output: 

```R
              Year         Lag1        Lag2        Lag3         Lag4
Year    1.00000000 -0.032289274 -0.03339001 -0.03000649 -0.031127923
Lag1   -0.03228927  1.000000000 -0.07485305  0.05863568 -0.071273876
Lag2   -0.03339001 -0.074853051  1.00000000 -0.07572091  0.058381535
Lag3   -0.03000649  0.058635682 -0.07572091  1.00000000 -0.075395865
Lag4   -0.03112792 -0.071273876  0.05838153 -0.07539587  1.000000000
Lag5   -0.03051910 -0.008183096 -0.07249948  0.06065717 -0.075675027
Volume  0.84194162 -0.064951313 -0.08551314 -0.06928771 -0.061074617
Today  -0.03245989 -0.075031842  0.05916672 -0.07124364 -0.007825873
               Lag5      Volume        Today
Year   -0.030519101  0.84194162 -0.032459894
Lag1   -0.008183096 -0.06495131 -0.075031842
Lag2   -0.072499482 -0.08551314  0.059166717
Lag3    0.060657175 -0.06928771 -0.071243639
Lag4   -0.075675027 -0.06107462 -0.007825873
Lag5    1.000000000 -0.05851741  0.011012698
Volume -0.058517414  1.00000000 -0.033077783
Today   0.011012698 -0.03307778  1.000000000
```

**Graphical summaries:**  

```R
> pairs(Weekly)
```

output: 

![ch4_q10_a](/Users/wangsiping/Documents/GitHub/Stanford_STATS_202/HW2/ch4_q10_a.png)

```R
> attach(Weekly)
> plot(Volume)
```

output:

![ch4_q10_a2](/Users/wangsiping/Documents/GitHub/Stanford_STATS_202/HW2/ch4_q10_a2.png)

The above graph shows an increasing trend in the data set. 

**(b)**

```R
> fit.glm = glm(Direction~Lag1+Lag2+Lag3+Lag4+Lag5+Volume, data=Weekly, family=binomial)
> summary(fit.glm)
```

output: 

```R
Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-1.6949  -1.2565   0.9913   1.0849   1.4579  

Coefficients:
            Estimate Std. Error z value Pr(>|z|)   
(Intercept)  0.26686    0.08593   3.106   0.0019 **
Lag1        -0.04127    0.02641  -1.563   0.1181   
Lag2         0.05844    0.02686   2.175   0.0296 * 
Lag3        -0.01606    0.02666  -0.602   0.5469   
Lag4        -0.02779    0.02646  -1.050   0.2937   
Lag5        -0.01447    0.02638  -0.549   0.5833   
Volume      -0.02274    0.03690  -0.616   0.5377   
---
Signif. codes:  0 ‘*** 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 1496.2  on 1088  degrees of freedom
Residual deviance: 1486.4  on 1082  degrees of freedom
AIC: 1500.4
```

The predictor *Lag2* is the only statistially significant one. 

**(c)**

```R
> probs=predict(fit.glm, type="response")
> pred.glm=rep("Down", length(probs))
> pred.glm[probs>0.5]="Up"
> table(pred.glm, Direction)
```

output: 

```R
        Direction
pred.glm Down  Up
    Down   54  48
    Up    430 557
```

explain: 

- The percentage of correct predictions is 
  $$
  \frac{54+577}{1089}=56.11\%,
  $$
  thus the training error is 43.89%. 

- When the market goes up, the percentage of correct classifications is
  $$
  \frac{557}{557+48} = 92.07\%.
  $$

- However, when the market goes down, the model is right only 
  $$
  \frac{54}{54+430}=11.16\%.
  $$

Thus, the model has higher accuracy when the prediction is “Up”. 

**(d)**

```R
> train=(Year<2009)
> Weekly.20092010=Weekly[!train,]
> Direction.20092010=Direction[!train]
> fit.glm2=glm(Direction~Lag2, data=Weekly, family=binomial, subset=train)
> summary(fit.glm2)
```

output: 

```R
Deviance Residuals: 
   Min      1Q  Median      3Q     Max  
-1.536  -1.264   1.021   1.091   1.368  

Coefficients:
            Estimate Std. Error z value Pr(>|z|)   
(Intercept)  0.20326    0.06428   3.162  0.00157 **
Lag2         0.05810    0.02870   2.024  0.04298 * 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 1354.7  on 984  degrees of freedom
Residual deviance: 1350.5  on 983  degrees of freedom
AIC: 1354.5
```

```R
> probs2=predict(fit.glm2, Weekly.20092010, type="response")
> pred.glm2=rep("Down", length(probs2))
> pred.glm2[probs2>0.5]="Up"
> table(pred.glm2, Direction.20092010)
```

output:

```R
         Direction.20092010
pred.glm2 Down Up
     Down    9  5
     Up     34 56
```

The overall fraction of correct predictions for the held out data is:
$$
\frac{9+56}{104} = 62.5\%.
$$
**(e)**

```R
> library(MASS)
> fit.lda=lda(Direction~Lag2, data=Weekly, subset=train)
> fit.lda
```

output: 

```R
Prior probabilities of groups:
     Down        Up 
0.4477157 0.5522843 

Group means:
            Lag2
Down -0.03568254
Up    0.26036581

Coefficients of linear discriminants:
           LD1
Lag2 0.4414162
```

```R
> pred.lda=predict(fit.lda, Weekly.20092010)
> table(pred.lda$class, Direction.20092010)
```

output: 

```R
      Direction.20092010
       Down Up
  Down    9  5
  Up     34 56
```

The overall fraction of correct predictions for the held out data is:
$$
\frac{9+56}{104} = 62.5\%.
$$
**(f)**

```R
> fit.qda=qda(Direction~Lag2, data=Weekly, subset=train)
> fit.qda
```

output: 

```R
Prior probabilities of groups:
     Down        Up 
0.4477157 0.5522843 

Group means:
            Lag2
Down -0.03568254
Up    0.26036581
```

```R
> pred.qda=predict(fit.qda, Weekly.20092010)
> table(pred.qda$class, Direction.20092010)
```

output:

```R
      Direction.20092010
       Down Up
  Down    0  0
  Up     43 61
```

The overall fraction of correct predictions for the held out data is:
$$
\frac{61}{43+61}=58.65\%.
$$
**(g)**

```R
> library(class)
> train.X=as.matrix(Lag2[train])
> test.X=as.matrix(Lag2[!train])
> train.Direction=Direction[train]
> set.seed(1)
> pred.knn=knn(train.X, test.X, train.Direction, k=1)
> table(pred.knn, Direction.20092010)
```

output: 

```R
        Direction.20092010
pred.knn Down Up
    Down   21 30
    Up     22 31
```

The overall fraction of correct predictions for the held out data is:
$$
\frac{21+31}{104}=50\%.
$$
**(h)**

From the percentage of correct predictions above, we can conclude that the logistic regression model and the LDA model have the maximum correct predictions, so these two models provide the best results on this data. 

**(i)**

Using a cubic model: 

```R
> fit.glm=glm(Direction~Lag2+I(Lag2^2)+I(Lag2^3),data=Weekly,subset=train, family="binomial")
> probs=predict(fit.glm, Weekly.20092010, type="response")
> pred.glm=rep("Down", length(probs))
> pred.glm[probs>0.5]="Up"
> table(pred.glm, Direction.20092010)
```

output:

```R
        Direction.20092010
pred.glm Down Up
    Down   13 14
    Up     30 47
```

The overall fraction of correct predictions for the held out data is:
$$
\frac{13+47}{104}=57.69\%.
$$
Using $KNN$ method wirh $k=10$. 

```R
> pred.knn2=knn(train.X, test.X, train.Direction, k=10)
> table(pred.knn2, Direction.20092010)
```

output: 

```R
         Direction.20092010
pred.knn2 Down Up
     Down   16 17
     Up     27 44
```

The overall fraction of correct predictions for the held out data is:
$$
\frac{16+44}{104}=57.69\%.
$$

## Problem 6

**(a)**

The probability that the first bootstrap observation is the $j$th oberservation is $\frac{1}{n}$, 

so the probability that the oberservation is not the $j$th oberservation is $1-\frac{1}{n}$.

**(b)**

The probability that the first bootstrap observation is the $j$th oberservation is
$$
\frac{(n-1)!}{n!}=\frac{1}{n},
$$
so the probability that the oberservation is not the $j$th oberservation is $1-\frac{1}{n}$.

**(c)**

From (a) and (b), we can conclude that the probability that a particular observation is not the $j$th observation is $1-\frac{1}{n}$, so the probability that the $j$th observation is not in the sample is $(1-\frac{1}{n})^n$. 

**(d)**

From (c), we can conclude that the probability that the $j$th observation is in the sample is $1-(1-\frac{1}{n})^n$. 

Given $n=5$, the probability is $1-(1-0.2)^5=0.672$.

**(e)**

Similar to (d), given $n=100$, the probability is $1-(1-0.01)^{100}=0.634$.

**(f)**

Similar to (e), given $n=10000$, the probability is $1-(1-\frac{1}{10000})^{10000}=0.632$.

**(g)**

```R
> x=1:100000
> plot(x, 1-(1-1/x)^x)
```

output:

![ch5_q2_g](/Users/wangsiping/Documents/GitHub/Stanford_STATS_202/HW2/ch5_q2_g.png)

The probability decreases quickly as $n$ increases, and seems to converge to around 0.63. 

**(h)**

The output for the codes is 0.6332. 

We may have a mathematically proof of this finding. Since
$$
\lim_{n\to\infty}(1+\frac{1}{n})^n=e,
$$

the probability may finally reach $1-\frac{1}{e}$ as $n\to\infty$.

## Problem 7

**(a)**

```R
> library(ISLR)
> attach(Default)
> set.seed(1)
> fit.glm=glm(default~income+balance, data=Default, family="binomial")
> summary(fit.glm)
```

output:

```R
Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-2.4725  -0.1444  -0.0574  -0.0211   3.7245  

Coefficients:
              Estimate Std. Error z value Pr(>|z|)    
(Intercept) -1.154e+01  4.348e-01 -26.545  < 2e-16 ***
income       2.081e-05  4.985e-06   4.174 2.99e-05 ***
balance      5.647e-03  2.274e-04  24.836  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 2920.6  on 9999  degrees of freedom
Residual deviance: 1579.0  on 9997  degrees of freedom
AIC: 1585
```

**(b)**

```R
> train=sample(dim(Default)[1], dim(Default)[1]/2)
> fit.glm=glm(default~income+balance, data=Default, family="binomial", subset=train)
> summary(fit.glm)
```

output:

```R
Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-2.3583  -0.1268  -0.0475  -0.0165   3.8116  

Coefficients:
              Estimate Std. Error z value Pr(>|z|)    
(Intercept) -1.208e+01  6.658e-01 -18.148   <2e-16 ***
income       1.858e-05  7.573e-06   2.454   0.0141 *  
balance      6.053e-03  3.467e-04  17.457   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 1457.0  on 4999  degrees of freedom
Residual deviance:  734.4  on 4997  degrees of freedom
AIC: 740.4

Number of Fisher Scoring iterations: 8
```

```R
> probs=predict(fit.glm, newdata=Default[-train,], type="response")
> pred.glm=rep("No", length(probs))
> pred.glm[probs>0.5]="Yes"
> mean(pred.glm!=Default[-train,]$default)
```

output: 

```R
[1] 0.0286
```

**(c)**

```R
> train=sample(dim(Default)[1], dim(Default)[1]/2)
> fit.glm=glm(default~income+balance, data=Default, family="binomial", subset=train)
> probs=predict(fit.glm, newdata=Default[-train,], type="response")
> pred.glm=rep("No", length(probs))
> pred.glm[probs>0.5]="Yes"
> mean(pred.glm != Default[-train,]$default)
[1] 0.0236
> train=sample(dim(Default)[1], dim(Default)[1]/2)
> fit.glm=glm(default~income+balance, data=Default, family="binomial", subset=train)
> probs=predict(fit.glm, newdata=Default[-train,], type="response")
> pred.glm=rep("No", length(probs))
> pred.glm[probs>0.5]="Yes"
> mean(pred.glm != Default[-train,]$default)
[1] 0.028
> train=sample(dim(Default)[1], dim(Default)[1]/2)
> fit.glm=glm(default~income+balance, data=Default, family="binomial", subset=train)
> probs=predict(fit.glm, newdata=Default[-train,], type="response")
> pred.glm=rep("No", length(probs))
> pred.glm[probs>0.5]="Yes"
> mean(pred.glm != Default[-train,]$default)
[1] 0.0268
```

We see that the test error rate can be variable, depending on which observations are included in the training set and which observations are included in the validation set.

**(d)**

```R
> train=sample(dim(Default)[1], dim(Default)[1]/2)
> fit.glm=glm(default~income+balance+student, data=Default, family="binomial", subset=train)
> pred.glm=rep("No", length(probs))
> probs=predict(fit.glm, newdata=Default[-train,], type="response")
> pred.glm[probs>0.5]="Yes"
> mean(pred.glm != Default[-train,]$default)
```

output:

```R
[1] 0.0264
```

Including a dumming variable for `student` does not lead to a reduction in the test error rate. 

## Problem 8

**(a)**

```R
> set.seed(1)
> attach(Default)
> fit.glm=glm(default~income+balance, data=Default, family="binomial")
> summary(fit.glm)
```

output: 

```R
Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-2.4725  -0.1444  -0.0574  -0.0211   3.7245  

Coefficients:
              Estimate Std. Error z value Pr(>|z|)    
(Intercept) -1.154e+01  4.348e-01 -26.545  < 2e-16 ***
income       2.081e-05  4.985e-06   4.174 2.99e-05 ***
balance      5.647e-03  2.274e-04  24.836  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 2920.6  on 9999  degrees of freedom
Residual deviance: 1579.0  on 9997  degrees of freedom
AIC: 1585

Number of Fisher Scoring iterations: 8
```

**(b)**

```R
> boot.fn=function(data, index) {
+ fit=glm(default~income+balance, data=data, family="binomial", subset=index)
+ return(coef(fit))
+ }
```

**(c)**

```R
> library(boot)
> boot(Default, boot.fn, 1000)
```

output: 

```R
Bootstrap Statistics :
         original        bias     std. error
t1* -1.154047e+01 -8.008379e-03 4.239273e-01
t2*  2.080898e-05  5.870933e-08 4.582525e-06
t3*  5.647103e-03  2.299970e-06 2.267955e-04
```

**(d)**

Using the `glm()` function and `boot`, we can obtain close estimated standard errors. 

## Problem 9

**(a)**

n is $y$, p is $x$. The model is
$$
y=x-2x^2+\epsilon.
$$
**(b)**

```R
plot(x, y)
```

output: 

![ch5_q8_b](/Users/wangsiping/Documents/GitHub/Stanford_STATS_202/HW2/ch5_q8_b.png)

**(c)**

```R
> library(boot)
> set.seed(1)
> Data=data.frame(x, y)
> fit.glm.1=glm(y~x)
> cv.glm(Data, fit.glm.1)$delta[1]
[1] 5.890979
> fit.glm.2=glm(y~poly(x, 2))
> cv.glm(Data, fit.glm.2)$delta[1]
[1] 1.086596
> fit.glm.3=glm(y~poly(x, 3))
> cv.glm(Data, fit.glm.3)$delta[1]
[1] 1.102585
> fit.glm.4=glm(y~poly(x, 4))
> cv.glm(Data, fit.glm.4)$delta[1]
[1] 1.114772
```

**(d)**

```R
> for(i in 1:4)
+ print(cv.glm(Data, glm(y~poly(x, i)))$delta[1])
[1] 5.890979
[1] 1.086596
[1] 1.102585
[1] 1.114772
```

The result is the same. This is because there is no sampling involved in LOOCV; the model is trained with the same observations for each cross validation test.

**(e)**

The model $Y=\beta_0+\beta_1X+\beta_2X^2+\epsilon$ had the smallest LOOCV error. This is easy to expect since we can saw in (b) that the relation between $x$ and $y$ is quadratic. 

**(f)**

```R
> summary(fit.glm.4)
```

output: 

```R
Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-2.8914  -0.5244   0.0749   0.5932   2.7796  

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -1.8277     0.1041 -17.549   <2e-16 ***
poly(x, 4)1   2.3164     1.0415   2.224   0.0285 *  
poly(x, 4)2 -21.0586     1.0415 -20.220   <2e-16 ***
poly(x, 4)3  -0.3048     1.0415  -0.293   0.7704    
poly(x, 4)4  -0.4926     1.0415  -0.473   0.6373    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for gaussian family taken to be 1.084654)

    Null deviance: 552.21  on 99  degrees of freedom
Residual deviance: 103.04  on 95  degrees of freedom
AIC: 298.78

Number of Fisher Scoring iterations: 2
```

It can be seen from the summary above that the linear and quadratic terms are statistically significant and that the cubic and 4th degree terms are not statistically significant. This agree strongly with our cross-validation results which were minimum for the quadratic model.

## Problem 10

**(a)**

```R
> library(MASS)
> attach(Boston)
> mu.hat=mean(medv)
> mu.hat
[1] 22.53281
```

$\hat\mu=22.53$.

**(b)**

```R
> se.hat=sd(medv)/sqrt(dim(Boston)[1])
> se.hat
[1] 0.4088611
```

$\hat{se(\hat\mu)}=0.409$, which reflects the accuracy of the estimate of $\mu$.

**(c)**

```R
> set.seed(1)
> boot.fn=function(data, index) {}
> boot.fn=function(data, index) {
+ mu=mean(data[index])
+ return(mu)
+ }
> boot(medv, boot.fn, 1000)
```

output:

```R
ORDINARY NONPARAMETRIC BOOTSTRAP


Call:
boot(data = medv, statistic = boot.fn, R = 1000)


Bootstrap Statistics :
    original      bias    std. error
t1* 22.53281 0.008517589   0.4119374
```

It can be seen from above that the standard error got from bootstrap is 0.412, which is different but close to the answer got in (b). 

**(d)**

```R
> t.test(medv)
```

output: 

```R
	One Sample t-test

data:  medv
t = 55.111, df = 505, p-value < 2.2e-16
alternative hypothesis: true mean is not equal to 0
95 percent confidence interval:
 21.72953 23.33608
sample estimates:
mean of x 
 22.53281 
```

```R
> CI.mu.hat <- c(22.53281 - 2 * 0.4119, 22.53281 + 2 * 0.4119)
> CI.mu.hat
```

output:

```R
[1] 21.70901 23.35661
```

The 95% confidence intercal for the mean of `medv` is different but close to the results obtained by ` t.test`. 

**(e)**

```R
> med.hat=median(medv)
> med.hat
[1] 21.2
```

$\hat\mu_{med}=21.2$.

**(f)**

```R
> boot.fn=function(data, index) {
+ mu=median(data[index])
+ return(mu)
+ }
> boot(medv, boot.fn, 1000)
```

output: 

```R
ORDINARY NONPARAMETRIC BOOTSTRAP


Call:
boot(data = medv, statistic = boot.fn, R = 1000)


Bootstrap Statistics :
    original  bias    std. error
t1*     21.2 -0.0098   0.3874004
```

The estimated median value, which is 21.2, is equal to the value obtained in (e), while the standard error, which is 0.3874, is relatively small compared to (c).

**(g)**

```R
> mu0.1.hat=quantile(medv, c(0.1))
> mu0.1.hat
  10% 
12.75 
```

$\hat\mu_{0.1}=12.75$.

**(h)**

```R
> boot.fn=function(data, index) {
+ mu=quantile(data[index], c(0.1))
+ return(mu)
+ }
> boot(medv, boot.fn, 1000)
```

output:

```R
Bootstrap Statistics :
    original  bias    std. error
t1*    12.75  0.0261   0.4912231
```

The estimated tenth percentile value, which is 12.75, is equal to the value obtained in (g), while the standard error, which is 0.4912, is relatively small compared to percentile value.