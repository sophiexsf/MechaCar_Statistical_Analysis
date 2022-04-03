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

## T-Tests on Suspension Coils

Performing a T-test on the entire population, we cannot determine whether the PSI across all lots is statistically different from the population mean of 1500 as it falls within the 95 percent confidence interval and the p-value of 0.06 is higher than the normal threshold of 0.05.

    	One Sample t-test
    
    data:  sc$PSI
    t = -1.8931, df = 149, p-value = 0.06028
    alternative hypothesis: true mean is not equal to 1500
    95 percent confidence interval:
     1497.507 1500.053
    sample estimates:
    mean of x 
      1498.78 

Breaking down the data by lots, we can see that the mean for Lot 1 is exactly the population mean of 1500:

    	One Sample t-test
    
    data:  lot1$PSI
    t = 0, df = 49, p-value = 1
    alternative hypothesis: true mean is not equal to 1500
    95 percent confidence interval:
     1499.719 1500.281
    sample estimates:
    mean of x 
         1500 

For Lot 2 the sample mean is higher than the population mean but not significantly so, with its p-value of 0.6 much higher than the 0.05 significance level:

    	One Sample t-test
    
    data:  lot2$PSI
    t = 0.51745, df = 49, p-value = 0.6072
    alternative hypothesis: true mean is not equal to 1500
    95 percent confidence interval:
     1499.423 1500.977
    sample estimates:
    mean of x 
       1500.2 
  
However, Lot 3 does appear to have a different mean PSI, with its p-value of 0.04 being lower than the 0.05 significance level:

    	One Sample t-test
    
    data:  lot3$PSI
    t = -2.0916, df = 49, p-value = 0.04168
    alternative hypothesis: true mean is not equal to 1500
    95 percent confidence interval:
     1492.431 1499.849
    sample estimates:
    mean of x 
      1496.14 

Therefore we cannot conclude that lots 1 and 2 have a different mean PSI than the population, but lot 3 does.

## Study Design: MechaCar vs Competition

To compare the MechaCar against the competition, I believe consumers would be most interested in the cost (including maintenance), city fuel efficiency, passenger or luggage capacity, and safety. We want to understand if the MechaCar will be considered too costly or inefficient (or too cheap or efficient) compared to other, similar cars. The null hypothesis would be that there is no difference between the MechaCar and its competitors. Therefore one possibility would be comparing the MechaCar against other cars of a similar class using an ANOVA test, with the city MPG rating as our dependent variable and capacity and safety measures as the categorical independent variables.

To run such tests we would need to gather consistent data about the characteristics and performance of the MechaCar and its competition. For the ANOVA test proposed, we would need city MPG measurements, seating capacity, and safety ratings.