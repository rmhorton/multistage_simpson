Here we implement the "[Multistage Simpson's Paradox Macine](http://ftp.cs.ucla.edu/pub/stat_ser/r414-reprint.pdf)" described by Professor Judea Pearl (see Figure 3).

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
-1.715871 
 4.335489 
-2.161678 
 3.938613 
-0.329377 
 3.771129
```
