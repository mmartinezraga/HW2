# Homework 2

M. Martinez-Raga, P. Sinclair, D. Gay 9/20/2020

### Experiment Protocol Analysis

**Possible Protocols**

*PP1*  
A single die has a sample space of 6 mutually exclusive outcomes, each
valued 1-6. We will roll the die once and draw a conclusion based on the
outcome being (X = 6) or (X = 1:5).

``` r
set.seed(5)  
die <- (1:6)  
die.roll <- sample(die,1)  
die.roll
```

    ## [1] 2

**Decision Rule**  
Null hypothesis **H<sub>0</sub>**: Our die is not unfair;  
Alternative hypothesis **H<sub>0</sub>**: Our die is unfair;

If a single roll yields a value of 6, we reject H<sub>0</sub> of a fair
die. If the roll yields any value inclusive of 1 to 5, we will fail to
reject H<sub>0</sub>.

The probability of failing to reject H<sub>0</sub> is 0.8333, conversely
the probability of rejecting Ho is 0.1667.

*Analysis*  
Theoretically, if the die is fair prior to the experiment, there is a
0.1667 probability of the die being considered unfair and a 0.8333
probability of the die being considered fair. Conversely, if the die
were unfair prior to the experiment, the probability that we would deem
it to be fair is \<0.8333. Depending on the weightiness of the die, that
probability would be a value between 0 and 0.8333.

*Edit*  
We came to the conclusion that an unfair die would have a \<0.8333
probability of being determined to be fair, based on the assumption that
the die was weighted to the outcome (X = 6). However, we have not been
given any information to make this assumption. Hence, if the die is
unfair to begin with, and weighted to any outcome **other** that (X =
6), then the probability it will be deemed fair under this decision
protocol is \>0.8333 and depending on the weightedness of the die would
approach 1.

-----

*PP2*  
Our number of trials (n) is 30; we will roll the die 30 times. To
determine the interval of the number outcomes with the value of 6 that
would indicate the die should be considered fair, we are applying a 90%
confidence level. If the number of outcomes with a value of 6 is outside
this interval, we will consider the die unfair.

-----

**Decision Rule**  
E(X = 6) = 1/6 \* 30 = 5. If we observe 6 approximately five times, we
can conclude that the die is fair.

-----

***Theoretical Calculation***  
**H<sub>0</sub>**: Our die is not unfair; not fixed toward 6.  
**H<sub>A</sub>**: Our die is unfair; fixed toward 6.

***Mean, Variance, Standard Deviation***

μ = np0 = 30 \* 1/6 = 5

σ^2 = np0(1 - p0) = 30 \* 1/6 \* 5/6 = 25/6

σ = sqrt(np0(1-p0)) = sqrt(25/6) ≈ 2.041241

***Significance Level***

α = 0.10; α/2 = 0.05

***Critical P***

P1 = 1.645

***Decision Criteria***

μ - P1σ = 5 - (1.645 \* 2.041241) = 1.642159

μ + P1σ = 5 + (1.645 \* 2.041241) = 8.357841

***Test Criteria***

μ - P1σ = 1.642159 -\> 1

μ + P1σ = 8.357841 -\> 9

If the number of successes \(\leq 1\) or \(\geq 9\), we reject
H<sub>0</sub> as false.

If the number of successes \(\geq 2\) or \(\leq 8\) , we fail to reject
H<sub>0</sub>.

***Conclusion***

For n = 30, with a confidence level of 90%, if a value of 6 occurs
between 2 and 8 times, the dice is considered to be fair.

***R-Simulated Calculation***

Our number of trials (n) is 30; we will roll the die 30 times. We used a
90% confidence interval to determine the threshold of occurrences of
rolling a value of 6 where the die would be considered fair.
Statistically significant deviation from the expected number of outcomes
with a value of 6 will render the die unfair.

-----

Below we determine expected occurrences of 6 in a trial of 30 rolls.

``` r
theoretical_prob = 1/6
n_pp2 = 30
occurences_pp2 = theoretical_prob * n_pp2
occurences_pp2
```

    ## [1] 5

-----

Now, we determine standard error for this trial.

``` r
se_pp2 = sqrt(n_pp2*(theoretical_prob*(1-theoretical_prob)))
se_pp2
```

    ## [1] 2.041241

-----

In order to determine the range of fair occurrences of 6 with confidence
level of 90%, we use a z-score of 1.645.

``` r
z_90 = 1.645
distance_pp2 = se_pp2 * z_90
floor_pp2 = occurences_pp2 - distance_pp2
ceiling_pp2 = occurences_pp2 + distance_pp2
range_pp2 = c(floor_pp2, ceiling_pp2)
```

``` r
range_pp2
```

    ## [1] 1.642158 8.357842

-----

If a fair die is rolled 30 times, the likely amount of occurrences for 6
should be between 2 and 8 times, inclusive. We will reject H<sub>0</sub>
if 6 is drawn less than 2 times or more than 8 times.

-----

``` r
dice.roll <- sample(1:6, size = 30, replace = TRUE)
test_pp2 <- table(dice.roll)
test_pp2
```

    ## dice.roll
    ## 1 2 3 4 5 6 
    ## 5 6 7 3 5 4

Given an outcome of 4 occurrences of value 6, we fail to reject
H<sub>0</sub> for PP2. All other sides also had an outcome within the
range of 2 and 8.

-----

PP3

For our third possible protocol, n = 100. To determine the interval of
the number outcomes with the value of 6 that would indicate the die
should be considered fair, we are applying a 90% confidence level. If
the number of outcomes with a value of 6 is outside this interval, we
will consider the die unfair. We kept a 90% confidence level to maintain
consistency across our experiments.

-----

Below we determine expected occurrences of 6 in a trial of 100 rolls.

``` r
theoretical_prob = 1/6
n_pp3 = 100
occurences_pp3 = theoretical_prob * n_pp3
occurences_pp3
```

    ## [1] 16.66667

-----

Now, we determine standard error for this trial.

``` r
se_pp3 = sqrt(n_pp3*(theoretical_prob*(1-theoretical_prob)))
se_pp3
```

    ## [1] 3.72678

-----

In order to determine the range of fair occurrences of 6 with confidence
level of 90%, we use a z-score of 1.645.

``` r
z_90 = 1.645
distance_pp3 = se_pp3 * z_90
floor_pp3 = occurences_pp3 - distance_pp3
ceiling_pp3 = occurences_pp3 + distance_pp3
range_pp3 = c(floor_pp3, ceiling_pp3)
range_pp3
```

    ## [1] 10.53611 22.79722

-----

If a fair die is rolled 100 times, the likely amount of occurrences for
6 should be between 10 and 23 times. We reject H<sub>0</sub> if the the
number of occurrences of value 6 proves \(\leq 10\) or \(\geq 23\).

-----

Hypothesis test PP3:

``` r
dice.roll <- sample(1:6, size = 100, replace = TRUE)
test_pp3 <- table(dice.roll)
test_pp3
```

    ## dice.roll
    ##  1  2  3  4  5  6 
    ## 17 14 17 21 13 18

Our results from the test yield a number of occurrences of 6 within the
identified range, thus we fail to reject H<sub>0</sub>.

-----

*EP1*

For our experimental protocol, we calculated the theoretical and tested
programmatic statistical values for rolling the die 100, 100,000 and
1,000,000. We sought to determine how the increase in sample size
affected the rate of our experiment yield approaching the calculated
theoretical yield at a confidence level of 90%. We expect to see that as
the number of samples increases, the closer our yield will approach our
theoretical yield.

-----

***Theoretical Sample Size of 100***

***Hypotheses***

Null hypothesis (Ho): Our die is not unfair; not fixed toward 6

Alternative hypothesis (Ha): Our die is unfair; fixed toward 6.

***Mean, Variance, Standard Deviation***

μ = np0 = 100 \* 1/6 = 50/3 = 16.666667

σ^2 = np0(1 - p0) = 100 \* 1/6 \* 5/6 = 125/9

σ = sqrt(np0(1-p0)) = sqrt(125/9) ≈ 3.726780

***Significance Level***

α = .05

***Critical P***

P1 = 1.645

***Decision Criteria***

μ - P1σ = 50/3 - (1.645 \* 3.726780) = 10.536114

μ + P1σ = 50/3 + (1.645 \* 3.726780) = 22.797220

***Test Criteria***

μ - P1σ = 10.536114 -\> 10

μ + P1σ = 22.797220 -\> 23

If the number of successes is less than or equal to 10 or greater than
or equal to 23, we reject the null hypothesis as false

If the number of success is at least 11 and at most 22, we accept the
null hypothesis as true.

***Conclusion***

For a confidence of 90% and rolling a die 100 times, if a value of 6
occurs between 11 and 22 times, the dice is fair.

-----

***Experimental Sample Size of 100***

``` r
frequency.test <- replicate(10, sample(1:6, 100, replace = TRUE))
freq_test <- as.data.frame(frequency.test)
s <- 0
for (game in colnames(freq_test)){
  s <- sum(s, table(freq_test[, game])[6])
}
m <- s/ncol(freq_test)
print(m)
```

    ## [1] 15.5

``` r
z <- ((m - 16.666667)/3.726780)
z
```

    ## [1] -0.3130496

-----

***Theoretical Sample Size of 100,000***

***Hypotheses***

Null hypothesis (Ho): Our die is not unfair; not fixed toward 6

Alternative hypothesis (Ha): Our die is unfair; fixed toward 6.

***Mean, Variance, Standard Deviation***

μ = np0 = 100000 \* 1/6 = 50000/3 = 16666.666667

σ^2 = np0(1 - p0) = 100000 \* 1/6 \* 5/6 = 13888.888889

σ = sqrt(np0(1-p0)) = sqrt(13888.888889) ≈ 117.851130

***Significance Level***

α = .05

***Critical P***

P1 = 1.645

***Decision Criteria***

μ - P1σ = 50000/3 - (1.645 \* 117.851130) = 16472.801558

μ + P1σ = 50000/3 + (1.645 \* 117.851130) = 16860.531776

***Test Criteria***

μ - P1σ = 16472.801558 -\> 16472

μ + P1σ = 16860.531776 -\> 16861

If the number of successes is less than or equal to 16472 or greater
than or equal to 16861, we reject the null hypothesis as false

If the number of success is at least 16473 and at most 16860, we accept
the null hypothesis as true.

***Conclusion***

For a confidence of 90% and rolling a die 100,000 times, if a value of 6
occurs between 16473 and 16860 times, the dice is fair.

-----

***Experimental Sample Size of 100,000***

``` r
frequency.test <- replicate(10, sample(1:6, 100000, replace = TRUE))
freq_test <- as.data.frame(frequency.test)
s <- 0
for (game in colnames(freq_test)){
  s <- sum(s, table(freq_test[, game])[6])
}
m <- s/ncol(freq_test)
print(m)
```

    ## [1] 16586.7

``` r
z <- ((m - 16666.666667)/117.851130)
z
```

    ## [1] -0.6785397

-----

***Theoretical Sample Size of 1,000,000***

***Hypotheses***

Null hypothesis (Ho): Our die is not unfair; not fixed toward 6

Alternative hypothesis (Ha): Our die is unfair; fixed toward 6.

***Mean, Variance, Standard Deviation***

μ = np0 = 1000000 \* 1/6 = 500000/3 = 166666.666667

σ^2 = np0(1 - p0) = 1000000 \* 1/6 \* 5/6 = 1250000/9

σ = sqrt(np0(1-p0)) = sqrt(1250000/9) ≈ 372.677996

***Significance Level***

α = .05

***Critical P***

P1 = 1.645

***Decision Criteria***

μ - P1σ = 500000/3 - (1.645 \* 372.677996) = 166053.611363

μ + P1σ = 500000/3 + (1.645 \* 372.677996) = 167279.721970

***Test Criteria***

μ - P1σ = 166053.611363 -\> 166053

μ + P1σ = 167279.721970 -\> 167280

If the number of successes is less than or equal to 166053 or greater
than or equal to 167280, we reject the null hypothesis as false

If the number of success is at least 166053 and at most 167279, we
accept the null hypothesis as true.

***Conclusion***

For a confidence of 90% and rolling a die 1,000,000 times, if a value of
6 occurs between 166053 and 167279 times, the dice is fair.

-----

***Experimental Sample Size of 1,000,000***

``` r
frequency.test <- replicate(10, sample(1:6, 1000000, replace = TRUE))
freq_test <- as.data.frame(frequency.test)
s <- 0
for (game in colnames(freq_test)){
  s <- sum(s, table(freq_test[, game])[6])
}
m <- s/ncol(freq_test)
print(m)
```

    ## [1] 166826.7

``` r
z <- ((m - 166666.666667)/372.677996)
z
```

    ## [1] 0.4294145

-----

*Analysis of EP1*

We expected to see the Z-scores decrease as the sample size increased to
prove a tighter relationship of the sample mean to the theoretical mean.
However, we did not observe in any meaningful or systematic way the
lowering of the scores with larger sample sizes. Perhaps the difference
would become more apparent with a significantly larger dataset, more
than 10 repetitions of the dice rolls at the sample intervals, or a
better understanding of how to manage the different types of random
number generators used by our respective operating systems.
