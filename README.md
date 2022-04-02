# MechaCar Statistical Analysis

## Linear Regression to Predict MPG

See MechaCarChallenge.RScript

Creating a multiple linear regression from the variables in the MechaCar_mpg.csv file produced the following result:

    Call:
    lm(formula = mpg ~ vehicle_length + vehicle_weight + spoiler_angle + 
        ground_clearance + AWD, data = mechacar)
    
    Residuals:
        Min       1Q   Median       3Q      Max 
    -19.4701  -4.4994  -0.0692   5.4433  18.5849 
    
    Coefficients:
                      Estimate Std. Error t value Pr(>|t|)    
    (Intercept)      -1.040e+02  1.585e+01  -6.559 5.08e-08 ***
    vehicle_length    6.267e+00  6.553e-01   9.563 2.60e-12 ***
    vehicle_weight    1.245e-03  6.890e-04   1.807   0.0776 .  
    spoiler_angle     6.877e-02  6.653e-02   1.034   0.3069    
    ground_clearance  3.546e+00  5.412e-01   6.551 5.21e-08 ***
    AWD              -3.411e+00  2.535e+00  -1.346   0.1852    
    ---
    Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
    
    Residual standard error: 8.774 on 44 degrees of freedom
    Multiple R-squared:  0.7149,	Adjusted R-squared:  0.6825 
    F-statistic: 22.07 on 5 and 44 DF,  p-value: 5.35e-11

From the summary we can see that the vehicle length and ground clearance provided a non-random amount of variance to the MPG values. The slope of the regression is not zero because the p-value of 5.35e-11 is smaller than the normal significance level of 0.05 and therefore we can reject the null hypothesis.

Furthermore, the multiple R-squared value of 0.71 is above the "strong" threshold of 0.7, suggesting that the model has strong predictive power for the vehicle's MPG rating.

## Summary Statistics on Suspension Coils

By summarizing the suspension coil PSI data we can see that the data appears normally distributed (mean and median are very similar).

![Total Summary](<./total_summary.png>)

Looking at the data by manufacturing lot, however, it appears the output from lot 1 is very consistent and the output from lot 3 is highly variable in comparison.

![Lot Summary](<./lot_summary.png>)

Since the design specifications require that the variance of suspension coils not exceed 100 PSI, manufacturing data meets this standard overall but not when examining output by manufacturing lot. Lots 1 and 2 achieve this standard, but Lot 3 shows a variance of 170.2 which is beyond the specified tolerance.
