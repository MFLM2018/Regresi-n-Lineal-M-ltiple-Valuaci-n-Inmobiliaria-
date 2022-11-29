# Regresi-n-Lineal-M-ltiple-Valuaci-n-Inmobiliaria-
Regresión Lineal Múltiple (Valuación Inmobiliaria)

##librerias
library(readxl)
library(ggplot2)
library(tidyr)
library(tidyverse)
library(tidyselect)
library(markdown)
library(rmarkdown)
library(dtplyr)
library(gclus)
library(PerformanceAnalytics)
library(psych)


##Creacion de data frame (RLM)
> nqn320<- lm(variables$Valor_Num~variables$Superficie + variables$Pua + variables$Ubc + variables$S2calles + variables$Ubz)
##Resmuen estadistico de RLM
> summary(nqn320)

Call:
lm(formula = variables$Valor_Num ~ variables$Superficie + variables$Pua + 
    variables$Ubc + variables$S2calles + variables$Ubz)

Residuals:
    Min      1Q  Median      3Q     Max 
-64.507 -32.219  -6.804  18.656 116.963 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)          1487.644    102.608  14.498 2.31e-16 ***
variables$Superficie  -20.220      8.194  -2.468 0.018634 *  
variables$Pua         -68.895     21.241  -3.243 0.002597 ** 
variables$Ubc         -94.153     24.366  -3.864 0.000462 ***
variables$S2calles    -42.868     18.135  -2.364 0.023770 *  
variables$Ubz         -30.072     26.740  -1.125 0.268423    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 44.02 on 35 degrees of freedom
Multiple R-squared:  0.7795,	Adjusted R-squared:  0.748 
F-statistic: 24.75 on 5 and 35 DF,  p-value: 1.39e-10

##llamado de coeficientes 
> nqn320$coefficients
         (Intercept) variables$Superficie        variables$Pua        variables$Ubc   variables$S2calles 
          1487.64427            -20.21992            -68.89542            -94.15266            -42.86783 
       variables$Ubz 
           -30.07164 
##calculo para la determinacion del valor del metro2 del inmueble objeto en estudio
> 1487.64427 + (-20.21992 * 2) + (  -68.89542 * 3.5) + (-94.15266 * 3) + ( -42.86783 * 3) + (-30.07164 * 3)
[1] 704.7941

> ##Valor de mtrs2*K Mercado*K Servicios Urbanos
> 707.79*0.80*1.21
[1] 685.1407

## valor homologado * superficie parcelaria
> 685.1407*825
[1] 565241.1



## grafico ID_Muestras

>ggplot(muestrascompl, aes(id,Valor_Num))+geom_point()+geom_line(linetype=1)+geom_point(aes(col=par_superf))+ labs(title = "Valor del Metro2 _ ID de Muestras_Area")

## grafico de correlacion y pearson

>chart.Correlation(variables, histogram = TRUE, method = "pearson", main="Pearson_Correlacion_Varibales")

>corPlot(variables, cex = 1.2, main = "Matriz de correlación")

#### coeficiente de variacion

> sd(muestrascompl$Valor_Num)/mean(muestrascompl$Valor_Num)
[1] 0.1165784




> ( 690 / 685.14 - 1 ) * 100
[1] 0.7093441
