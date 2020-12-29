[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

**Problem: What percentage of men have heights between 5'10'' and 6'1''?**

As given in the exercise, from the 2008 BRFSS survey, the heights of men follow a normal distribution with a mean of 178 cm and a standard deviation of 7.7 cm. By calculating the CDF distribution of this normal distribution, and evaluating it's values at the associated heights and taking the difference, the problem can be solved. Using the code below, the percentage of men with heights between 5'10'' and 6'1'' is **34.3%**.


```
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

feet_to_cm = 30.48
lowrange = (5+10/12)*feet_to_cm
highrange = (6+1/12)*feet_to_cm

dist.cdf(highrange) - dist.cdf(lowrange)
```
