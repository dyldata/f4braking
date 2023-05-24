# Formula 4 Performance
Analysis of Formula 2 driving styles in a singular corner.
Little is understood about the key motor skills in race car driving. Thus, this analyis took two essential aspects of braking performance: the peak  force (PF) and the rate of force development of braking (RFD) and analyzed their overall impact on corning performance. The braking data was assembled from the SMP Formula 4 championship, which is a junior formula series to develop young drivers to the single-seater categories such as Formula 3 and Formula 2. 

##
Visualizations and models were built out using R and RStudio.

## Time on Pedal
<p align="center">
<img width="700" height="500" src=images/timepedal.jpg
</p>

## Statistical Analysis:
Data was acquired from seven races and 21 young race drivers (insert anthropometrics here if possible) during the 2018 SMP Formula 4 Championship Series. Data and results were reported as means+/-SD and analyzed with R statistical software (R Core Team, 2014; version 4.0.4) using LM (Bates et al., 2015) to perform a multiple linear regression. Normality was analyzed using Shapiro-Wilk test. The data that did not pass normality were transformed using the natural logarithm. This was done to meet the assumptions of the statistical model utilized to stabilize the variance seen among the outcome variables and the standard of errors. A stepwise regression was conducted by process of elimination, where independent (predictor) variables were added and/or removed based on the variance seen in cornering times that could be explained by the model. In summary, if a predictor variable made the model worse (lower R squared) and was not significant (p > 0.05), it was removed from the model. Pearson’s product correlation coefficients were defined as, r=0-0.1 (trivial), r=0.1-0.3 (small), r=0.3-0.5 (moderate), r=0.5-0.7 (large), r=0.7-0.9 (very large) and r=0.9-1.0 (almost perfect) (Hinkle et al., 2003). Data that were statistically analyzed utilizing log-transformed data were presented as means+/-SD of non-transformed data within tables and results. F ratios were found significant at p ≤ 0.05. 

  ## Packages Used
```
install.packages("ggplot2")
install.packages("tidyverse")
install.packages("dplyr")
install.packages("ggpubr")
install.packages("corrplot")
install.packages("car")
```
  
  
  ## Example Code for Model
```
model8=lm(cornertime~avgs+maxs+ttpedal+track, data=f1seconds_a)
summary(model8)
extractAIC(model8)
head(fulldata)
```
  ## Example Code for Plots
  ```
  ggplot(f1seconds_p, aes(x=ttpedal, y=cornertime)) + geom_point(aes(color = track)) + 
  scale_x_continuous("Time on Pedal (seconds)") +
  scale_y_continuous("Corner Time (seconds)") + 
  theme(panel.grid.major=element_line(NA), panel.grid.minor=element_line(NA), legend.position="bottom") + 
  labs(title="Time on Pedal on Corner Times") + facet_wrap( ~ track) + stat_smooth(method="lm", col="red") + labs(color="Track:")
```
