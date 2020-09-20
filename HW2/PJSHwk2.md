Homework 2
================
Patrick Sinclair

### Experiment Protocol Analysis

**Possible Protocols**

*PP1*  
Roll die once, if \(X = 6\), then conclude the die is unfair. If
\(X = 1, 2, 3, 4, 5\), then conclude the die is fair.

With such a small sample, the probability that we would determine what
is actually a fair die to be unfair is (1/6). Conversely, if the die
were unfair, the probability that we would deem it to be fair is \< 5/6.
Depending on the weightedness of the die, that probability could even be
zero.

*PP2*  
Roll die 30 times.

Decision Rule: E(X = 6) = 1/6 \* 30 = 5. If we observe 6 approximately
five times, we can conclude that the die is fair.

Were we to roll a fair die, we would expect to observe a 6 on five
occasions. We can approach the problem using a binomial distribution -
we either observe a 6, classified as a success, or we do not observe a
6, a failure. We would expect to roll a 6 on five occasions 19.211% of
the time. Rolling one more or one less 6 would occur 18.468% and 16.013%
of the time, respectively.

Below is a table of probabilities from the binomial distribution:

    ##   X...6 Probability
    ## 1     2      0.0732
    ## 2     3      0.1368
    ## 3     4      0.1847
    ## 4     5      0.1921
    ## 5     6      0.1601
    ## 6     7      0.1098
    ## 7     8      0.0632

Our sample size and probability of success is large enough to let us
approximate the binomial using the normal distribution. Rolling a 6 from
four to six times would occur 37.6% of the time. I conclude that it is
not particularly unusual to roll one more or one less 6.

As with one more or less, rolling a 6 on two more or two less occasions
sits within 1 standard deviation of the mean. We would expect
approximately 68% of our samples to produce a 6 on 3, 4, 5, 6 or 7
occasions. These results are not particularly unusual. Rolling a 6 three
more or less times is less common - a 6 occurring twice or eight times
are approximately 1.47 standard deviations from the mean of five.

###### Frequency Histogram of PP2 Experiement

    ##  [1] 1 4 1 2 5 3 6 2 3 3 1 5 5 2 6 6 2 1 5 5 1 1 6 5 5 2 2 6 1 4

![](PJSHwk2_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

Referring back to our decision protocol, we determine that the die is
fair, having produced a 6 on five occasions. If we have a fair die,
using this protocol we have a 62.4% chance of mistakenly classing it as
an unfair die.

*PP3*  
Roll die 100 times.

Decision Rule: As above, E(X=6) = 1/6 \* 100 = 16.667. If we observe 6
approximately seventeen times, we can conclude that the die is fair.

Any conclusion we arrive at does require a level of confidence. Which
level of confidence one should use depends on the context. Are we
rolling to see who takes first turn at the annual family Monopoly
showdown or are we involved in a high stakes craps game?

Let’s assume we’re facing off against Uncle Joe after the turkey has
been carved and we’re ok with a confidence level of 80%.

Our sample size lets us approximate a binomial distribution using a
normal distribution. Our E(X=6) = 16.667. We take the critical z-score
of alpha = 0.2, multiply by the sampling standard deviation and then add
and subtract from out mean: 16.667 +/- 0.476. Our fair die would produce
a 6 between 16.191 and 17.143 occasions, 80% of the time.

While the sample size is sufficiently large, focusing solely on one
outcome, rolling a 6, is too myopic to truly determine whether the die
is fair or not. If the die was weighted to another number, rolling a 6
may still occur enough times to satisfy the protocol yet we remain
ignorant to the fact that other numbers may be occurring at
statistically significantly high rates.
