## MODUL 2 TRANSFORMASI DATA
  ### A. TRANSFORMASI ALGORITMA
**2. TRANSFORMASI X2 =LN(X)**

**a. input data ke R**
```
\\masukan data menggunakan delim di variable data_word_recall
data_word_recall<-
+ read.delim("https://online.stat.psu.edu/onlinecourses/sites/stat501/files/data/wordrecall.txt",header=TRUE,sep="\t")

\\optional untuk menggunakan pack knitr
install.packages("knitr")
knitr::kable(head(data_word_recall,10))  


```

> data_word_recall adalah variable
> read => object
> .delim() => function bertujuan untuk mendapatkan data

**b. Analisis Regresi Linier Sederhana**
menggunakan fungsi lm (linear models) yang berasal dari package stats otomatis dari software R.

```
\\menampilkan data dengan menggunakan fungsi lm()
summary(lm(prop~time,data=data_word_recall))

\\maka akan keluar output
Call:
lm(formula = prop ~ time, data = data_word_recall)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.18564 -0.11913 -0.04495  0.08496  0.31418 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.259e-01  4.881e-02  10.774 3.49e-07 ***
time        -5.571e-05  1.457e-05  -3.825  0.00282 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1523 on 11 degrees of freedom
Multiple R-squared:  0.5709,	Adjusted R-squared:  0.5318 
F-statistic: 14.63 on 1 and 11 DF,  p-value: 0.002817
```

**c. Membuat Diagram Pencar**
menggunakan fungsi plot pada package graphics otomatis dari software R.
> terdapat data_word_recall$time,data_word_recall$prop untuk mengambil data time dan prop dari variable data_word_recall
> terdapat main="diagram pencar" untuk menambahkan judul diagram
> terdapat ylab="ingatan benar (proporsisi)" untuk menamakan sumbu y (vertikal/tegak)
> terdapat xlab="waktu (menit)" untuk menamakan sumbu x (horizontal/datar)
> terdapat col="blue" untuk memberi warna pada kolom

```
\\diagram pencar menggunakan fungsi plot()
plot(data_word_recall$time,data_word_recall$prop,main="diagram pencar",ylab="ingatan benar (proporsisi)", xlab="waktu (menit)", col="blue")

```

**c. Melakukan Transformasi Data**
menggunakan fungsi log pada package base otomatis dari software R.
> log() akan mengembalikan nilai logaritma natural (ln)


```
\\menggunkana transformasi data menggunakan log()
data_word_recall$ln_time<-log(data_word_recall$time)
```
**2. TRANSFORMASI Y^* =LN(Y)**
**a. input data ke R**
```
# Membuat data
y <- c(80, 61, 52, 46, 42, 39, 37, 35, 33, 32)
x <- c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

```
**b. menggabungkan  x dan y kedalam suata data frame**
```
# Menggabungkan x dan y ke dalam Data Frame
data_kurva_pengalaman <- as.data.frame(cbind(y, x))

```
**c. Analisis Regresi Linier Sederhana**
```
# Analisis Regresi Linier Sederhana
summary(lm(y ~ x, data = data_kurva_pengalaman))

```

**d. Memeriksa sebaran data**
```
# Membuat diagram pencar (scatter plot)
plot(x, y,
     main = "Diagram Pencar",
     ylab = "biaya marginal per unit (US$)",
     xlab = "produksi kumulatif (juta unit)",
     col = "darkmagenta")

```

**e. Melakukan transformasi data (logaritma natural)**
```
# Melakukan transformasi data (logaritma natural)
ln_y <- log(y)
ln_x <- log(x)

# Menggabungkan hasil transformasi ke dalam Data Frame
data_ln <- as.data.frame(cbind(ln_y, ln_x))

# Menampilkan tabel hasil transformasi
knitr::kable(data_ln)

```

**f. Analisis Regresi Linier Sederhana dengan data hasil transformasi**
```
# Analisis Regresi Linier Sederhana dengan data hasil transformasi
summary(lm(ln_y ~ ln_x, data = data_ln))

```
**g. perbandingan model**
```
# Model regresi awal (tanpa transformasi)
model_awal <- lm(y ~ x, data = data_kurva_pengalaman)
summary(model_awal)

# Model regresi setelah transformasi (menggunakan log natural)
model_transformasi <- lm(ln_y ~ ln_x, data = data_ln)
summary(model_transformasi)

# Membandingkan nilai R-squared dari kedua model
r2_awal <- summary(model_awal)$r.squared
r2_transformasi <- summary(model_transformasi)$r.squared

# Menampilkan hasil perbandingan
data.frame(
  Data = c("Awal", "Transformasi"),
  Persamaan_Regresi = c("y = 70.467 - 4.503x", "ln y = 4.386 - 0.401ln x"),
  R_Square = c(r2_awal, r2_transformasi)
)


```


