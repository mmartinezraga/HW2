Homework 2
================
M. Martinez-Raga, P. Sinclair, D. Gay
9/20/2020

### Experiment Protocol Analysis

**Possible Protocols**

*PP1*  
A single die has a sample space of 6 mutually exclusive outcomes (with
possible outcomes valued 1-6). For the purpose of this lab, we will
consider any outcome (X) with a value of 6 to render the die unfair.
Conversely, values of 1-5 will conclude to the die to be fair.

Roll die once, if \(X = 6\), then conclude the die is unfair. If
\(X = 1, 2, 3, 4, 5\), then conclude the die is fair.

Theoretically, there is a 1/6, or 16.667%, probability of the die being
considered unfair and a 5/6, or 83.333%, probability of the die being
considered fair.

With such a small sample, the probability that we would determine what
is actually a fair die to be unfair is (1/6). Conversely, if the die
were unfair, the probability that we would deem it to be fair is \<=
5/6. Depending on the weightiness of the die, that probability could
even be zero.

-----

**Decision Rule**

Null hypothesis (Ho): Our die is not unfair; not fixed toward 6

Alternative hypothesis (Ha): Our die is unfair; fixed toward 6.

The rule is as follows: If a single roll yields a value of 6, we reject
the null hypothesis of a fair die. A roll yielding any value between 1-5
inclusive will render an accepted null of a fair die.

The probabilities of our null hypothesis being accepted or rejected are
5/6 and 1/6, respectively.

-----

*PP2*

Our number of trials (n) is 30; we will roll the die 30 times. We used a
90% confidence interval to determine the threshold of occurrences of
rolling a value of 6 where the die would be considered fair.
Statistically significant deviation from this value will consider the
die unfair.

-----

**Decision Rule** E(X = 6) = 1/6 \* 30 = 5. If we observe 6
approximately five times, we can conclude that the die is fair.

-----

***Theoretical Calculation*** Null hypothesis (Ho): Our die is not
unfair; not fixed toward 6

Alternative hypothesis (Ha): Our die is unfair; fixed toward 6.

***Mean, Variance, Standard Deviation***

μ = np0 = 30 \* 1/6 = 5

σ^2 = np0(1 - p0) = 30 \* 1/6 \* 5/6 = 25/6

σ = sqrt(np0(1-p0)) = sqrt(25/6) ≈ 2.041241

***Significance Level***

α = .05

***Critical P***

P1 = 1.645

***Decision Criteria***

μ - P1σ = 5 - (1.645 \* 2.041241) = 1.642159

μ + P1σ = 5 + (1.645 \* 2.041241) = 8.357841

***Test Criteria***

μ - P1σ = 1.642159 -\> 1

μ + P1σ = 8.357841 -\> 9

If the number of successes is less than or equal to 1 or greater than or
equal to 9, we reject the null hypothesis as false

If the number of success is at least 2 and at most 8, we accept the null
hypothesis as true.

***Conclusion***

For a confidence of 90% and rolling a die 30 times, if a value of 6
occurs between 2 and 8 times, the dice is considered to be fair. Else,
the dice is considered to be unfair.

***R-Simulated Calculation***

Our number of trials (n) is 30; we will roll the die 30 times. We used a
90% confidence interval to determine the threshold of occurrences of
rolling a value of 6 where the die would be considered fair.
Statistically significant deviation from this value will consider the
die unfair.

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
should be between 2 and 8 times, inclusive. We will reject Ho if 6 is
drawn less than 2 times or more than 8 times.

-----

``` r
dice.roll <- sample(1:6, size = 30, replace = TRUE)
test_pp2 <- table(dice.roll)
test_pp2
```

    ## dice.roll
    ## 1 2 3 4 5 6 
    ## 9 5 2 5 3 6

Given an outcome of 4 occurrences of value 6, we accept the null
hypothesis for PP2. All other sides also had an outcome within the range
of 2 and 8.

-----

PP3

For our third possible protocol, our number of trials (n) is 100. We
used a 90% confidence interval to determine the range of occurrences of
6 where the die would be considered fair. Anything beyond that range
will be deemed unfair. We kept a 90% confidence level to maintain
homogeny in our experiments.

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
6 should be between 10 and 23 times. We reject the null hypothesis if
the the number of occurrences of value 6 proves less than 10 or more
than 23 times.

-----

Hypothesis test PP3:

``` r
dice.roll <- sample(1:6, size = 100, replace = TRUE)
test_pp3 <- table(dice.roll)
test_pp3
```

    ## dice.roll
    ##  1  2  3  4  5  6 
    ## 22 23 14 10 13 18

Our results from the test yield a number of occurrences of 6 within the
identified range, thus we fail to reject the null hypothesis.
