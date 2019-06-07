---
title: "Advanced Bioinformatics 2019 assessment"
author: "1806284"
date: "09/05/2019"
output:
  html_document:
    keep_md: yes
---


"Task 1"

```r
sum(5:55)
```

```
## [1] 1530
```




"Task 2"

```r
sumfun <- function(n){
  return(sum(5:n))
}

sumfun(10)
```

```
## [1] 45
```

```r
sumfun(20)
```

```
## [1] 200
```

```r
sumfun(100)
```

```
## [1] 5040
```




"Task 3"

```r
vector<-c()
vector[1:2]=1
for (i in 3:12){
  vector[i]=vector[i-1]+vector[i-2]
}
 
vector 
```

```
##  [1]   1   1   2   3   5   8  13  21  34  55  89 144
```




"Task 4"

```r
data(mtcars)
library(ggplot2)

ggplot(mtcars, aes(x=factor(gear),y=mpg,fill=factor(gear)))+
  geom_boxplot(notch=F) +scale_x_discrete("Gear")+
  scale_y_continuous("Miles per Gallon")+ggtitle("MPG by Gears")
```

![](AdvBio_2019_Assessment_files/figure-html/unnamed-chunk-4-1.png)<!-- -->





"Task 5"

```r
data(cars)
lmodel <- lm(dist ~ speed, data = cars)

slope <- lmodel$coefficients[2]
slope[[1]]
```

```
## [1] 3.932409
```

```r
intercept <- lmodel$coefficients[1]
intercept[[1]]
```

```
## [1] -17.57909
```

```r
sd_slope <- summary(lmodel)$coefficients[2,2]
sd_slope
```

```
## [1] 0.4155128
```

```r
sd_intercept <- summary(lmodel)$coefficients[1,2]
sd_intercept
```

```
## [1] 6.75844
```





"Task 6"

```r
ggplot(cars, aes(x=speed, y=dist)) + geom_point() + labs(y="Breaking Distance [feet]", x="Speed [mph]") +
  geom_smooth(method="lm", se=F)
```

![](AdvBio_2019_Assessment_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

```r
  #geom_abline(intercept = 8.28, slope=0.16)
```





"Task 7"

```r
speed_t <- cars$speed * (5280/3600)

lmodel_2 <- lm(dist ~ 0 + speed_t + I(speed_t^2), cars)
summary(lmodel_2)
```

```
## 
## Call:
## lm(formula = dist ~ 0 + speed_t + I(speed_t^2), data = cars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -28.836  -9.071  -3.152   4.570  44.986 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)   
## speed_t       0.84479    0.38180   2.213  0.03171 * 
## I(speed_t^2)  0.04190    0.01366   3.067  0.00355 **
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.02 on 48 degrees of freedom
## Multiple R-squared:  0.9133,	Adjusted R-squared:  0.9097 
## F-statistic: 252.8 on 2 and 48 DF,  p-value: < 2.2e-16
```

```r
# The average value is 0.84479 seconds, which seems a reasonable time

x <- cars$spped_t
y <- cars$dist

ggplot(cars,aes(speed_t, dist)) +
  geom_point()+
  geom_smooth(method="lm", formula = "y~0+x+I(x^2)")+
  labs(title="Average reaction time", x="Speed [feets/s]", y="Breaking distance [feet]")
```

![](AdvBio_2019_Assessment_files/figure-html/unnamed-chunk-7-1.png)<!-- -->


When you save the notebook, an HTML file containing the code and output will be saved alongside it (click the *Preview* button or press *Cmd+Shift+K* to preview the HTML file). 

The preview shows you a rendered HTML copy of the contents of the editor. Consequently, unlike *Knit*, *Preview* does not run any R code chunks. Instead, the output of the chunk when it was last run in the editor is displayed.

