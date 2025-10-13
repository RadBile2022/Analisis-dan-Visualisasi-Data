
<img width="1455" height="923" alt="image" src="https://github.com/user-attachments/assets/e097d5cc-1961-48b1-acd4-7c65f8d11fae" />
## MODUL II TRANSFORMASI PANGKAT

1. TRANSFORMASI RECIPROCAL

a. input data ke R
```
\\masukan data menggunakan foreign
> data_wind_speed <- foreign::read.dta("http://www.unm.edu/~schrader/biostat/bio2/Spr06/windspeed.dta")

\\optional untuk menggunakan pack knitr
install.packages("knitr")
knitr::kable(head(data_wind_speed,25))
\\ Jika tanpa menambkahkan variable angka di knitr::kable, maka otomatis hanya akan menampilkan 6 data saja
\\ | speed|    dc|
|-----:|-----:|
|  5.00| 1.582|
|  6.00| 1.822|
|  3.40| 1.057|
|  2.70| 0.500|
| 10.00| 2.236|
|  9.70| 2.386|
|  9.55| 2.294|
|  3.05| 0.558|
|  8.15| 2.166|
|  6.20| 1.866|
|  2.90| 0.653|
|  6.35| 1.930|
|  4.60| 1.562|
|  5.80| 1.737|
|  7.40| 2.088|
|  3.60| 1.137|
|  7.85| 2.179|
|  8.80| 2.112|
|  7.00| 1.800|
|  5.45| 1.501|
|  9.10| 2.303|
| 10.20| 2.310|
|  4.10| 1.194|
|  3.95| 1.144|
|  2.45| 0.123|

```
b. Analisi regresi linear sederhana menggunakan summary
```
\\ Coder Program
<- summary(lm(dc~speed, data = data_wind_speed))
\\ Maka akan keluar hasil seperti ini
\\Call:
lm(formula = dc ~ speed, data = data_wind_speed)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.59869 -0.14099  0.06059  0.17262  0.32184 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.13088    0.12599   1.039     0.31    
speed        0.24115    0.01905  12.659 7.55e-12 ***
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.2361 on 23 degrees of freedom
Multiple R-squared:  0.8745,	Adjusted R-squared:  0.869 
F-statistic: 160.3 on 1 and 23 DF,  p-value: 7.546e-12


