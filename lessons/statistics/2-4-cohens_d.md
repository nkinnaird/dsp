[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Problem: Do first born babies weigh more or less than other babies?**

In order to answer this question, I modified A. Downey's *first.py* program to use the variable `totalwgt_lb` instead of `prglngth`. This program calculates the means and standard deviations of a pregnancy related variable from a 2002 NSFG survey, and produces the relevant difference statistic, Cohen's *d*.

First babies have a mean weight of 7.201 lbs, other babies have a mean weight of 7.326 lbs, resulting in a mean difference of -0.125 lbs. With standard deviations of 1.421 and 1.394 lbs respectively, Cohen's *d* is **-0.089**. This is very small, though larger than the difference in mean pregnancy length between first born babies and others as calculated by A. Downey. At this stage, without a deeper dive into the data, it can be said that first born babies probably weigh the same as other babies. 

The figure below shows a histogram of the total weights of first born babies as compared to others. By eye, there is no significant difference between the two distributions, which Cohen's *d* reflects. (Note, the colors aren't great for this plot, they are too similar. Looking in to the source code it looks like *thinkplot*'s colors are hardcoded, and I decided against changing them.)

Below the figure is the relevant code for the problem solution.

![Baby weights, first born vs others](Images/first_weight_nsfg_hist.png)

```
{
def Summarize(live, firsts, others):
    """Print various summary statistics."""

    mean = live.totalwgt_lb.mean()
    var = live.totalwgt_lb.var()
    std = live.totalwgt_lb.std()

    print('Live mean', mean)
    print('Live variance', var)
    print('Live std', std)

    mean1 = firsts.totalwgt_lb.mean()
    mean2 = others.totalwgt_lb.mean()

    var1 = firsts.totalwgt_lb.var()
    var2 = others.totalwgt_lb.var()

    print('Mean')
    print('First babies', mean1)
    print('Others', mean2)

    print('Variance')
    print('First babies', var1)
    print('Others', var2)

    print('Difference in lbs', mean1 - mean2)

    d = thinkstats2.CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
    print('Cohen d', d)


def MakeComparison(firsts, others):
    """Plots histograms of total weight for first babies and others.

    firsts: DataFrame
    others: DataFrame
    """
    first_hist = thinkstats2.Hist(firsts.totalwgt_lb, label='first')
    other_hist = thinkstats2.Hist(others.totalwgt_lb, label='other')

    width = 0.05
    thinkplot.PrePlot(2)
    thinkplot.Hist(first_hist, align='right', width=width)
    thinkplot.Hist(other_hist, align='left', width=width)

    thinkplot.Save(root='first_weight_nsfg_hist', 
                   title='Histogram',
                   xlabel='lbs',
                   ylabel='frequency')#,

}
```






