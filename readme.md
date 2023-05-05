Here we implement the "[Multistage Simpson's Paradox Macine](http://ftp.cs.ucla.edu/pub/stat_ser/r414-reprint.pdf)" described by Professor Judea Pearl (see Figure 3). This made it possible for us to generate the 'multi_stage_simpsons_paradox_data' dataset ('mssp' for short) that demonstrates multiple Simpson's Paradox reversals of the sign of the coefficient of X, depending on which other covariates are included in the analysis. The system is designed so that as we add in co-variates 'Z1', 'Z2', 'Z3', 'Z4', and 'Z5', in that order, the coefficient of X for predicting Y repeatedly changes sign.

```
mssp <- read.csv("multi_stage_simpsons_paradox_data.csv")

coef( lm(Y ~ X, mssp) )['X']
coef( lm(Y ~ X + Z1, mssp) )['X']
coef( lm(Y ~ X + Z1 + Z2, mssp) )['X']
coef( lm(Y ~ X + Z1 + Z2 + Z3, mssp) )['X']
coef( lm(Y ~ X + Z1 + Z2 + Z3 + Z4, mssp) )['X']
coef( lm(Y ~ X + Z1 + Z2 + Z3 + Z4 + Z5, mssp) )['X']
```

You should see the coefficient of X take the following values, alternating between negative and positive depending on which co-variates are included:
```
 1.137793 
-0.998305 
 1.01994 
-1.034066 
 1.281207 
-1.007758 
```
