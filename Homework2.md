Homework 2
================
M. Martinez-Raga, P. Sinclair, D. Gay
9/20/2020

### Experiment Protocol Analysis

**Possible Protocols**  

*PP1*  
A single die has a sample space of 6 mutually exclusive outcomes, each valued 1-6. We will roll the die once and draw a conclusion based on the outcome being (X = 6) or (X = 1:5).

```{r, echo=FALSE}
set.seed(5)  
die <- (1:6)  
  die.roll <- sample(die,1)  
  die.roll
```  

**Decision Rule**  
Null hypothesis **H~0~**: Our die is not unfair;  
Alternative hypothesis **H~0~**: Our die is unfair;

If a single roll yields a value of 6, we reject H~0~ of a fair die. If the roll yields any value inclusive of 1 to 5,  we will fail to reject H~0~.

The probability of failing to reject H~0~ is 0.8333, conversely the probability of rejecting Ho is 0.1667.  

*Analysis*  
Theoretically, if the die is fair prior to the experiment, there is a 0.1667 probability of the die being considered unfair and a 0.8333 probability of the die being considered fair. Conversely, if the die were unfair prior to the experiment, the probability that we would deem it to be fair is  <0.8333. Depending on the weightiness of the die, that probability would be a value between 0 and 0.8333.  

*Edit*  
We came to the conclusion that an unfair die would have a <0.8333 probability of being determined to be fair, based on the assumption that the die was weighted to the outcome (X = 6). However, we have not been given any information to make this assumption. Hence, if the die is unfair to begin with, and weighted to any outcome **other** that (X = 6), then the probability it will be deemed fair under this decision protocol is >0.8333 and depending on the weightedness of the die would approach 1.

______


*PP2*  
Our number of trials (n) is 30; we will roll the die 30 times. To determine the interval of the number outcomes with the value of 6 that would indicate the die should be considered fair, we are applying a 90% confidence level. If the number of outcomes with a value of 6 is outside this interval, we will consider the die unfair. 

______


**Decision Rule**  
E(X = 6) = 1/6 * 30 = 5. If we observe 6 approximately five times, we can conclude that the die is fair.

______


***Theoretical Calculation***  
**H~0~**: Our die is not unfair; not fixed toward 6.  
**H~A~**: Our die is unfair; fixed toward 6.

***Mean, Variance, Standard Deviation***

μ = np0 = 30 * 1/6 = 5

σ^2 = np0(1 - p0) = 30 * 1/6 * 5/6 = 25/6

σ = sqrt(np0(1-p0)) = sqrt(25/6)  ≈ 2.041241

***Significance Level***

α = 0.10; α/2 = 0.05

***Critical P***

P1 = 1.645

***Decision Criteria***

μ - P1σ = 5 - (1.645 * 2.041241) = 1.642159

μ + P1σ = 5 + (1.645 * 2.041241) = 8.357841

***Test Criteria***

μ - P1σ = 1.642159 -> 1

μ + P1σ = 8.357841 -> 9

If the number of successes $\leq 1$  or $\geq 9$, we reject H~0~ as false. 

If the number of successes $\geq 2$  or $\leq 8$ , we fail to reject H~0~.

***Conclusion***

For n = 30, with a confidence level of 90%, if a value of 6 occurs between 2 and 8 times, the dice is considered to be fair.

***R-Simulated Calculation***

Our number of trials (n) is 30; we will roll the die 30 times. We used a 90% confidence interval to determine the threshold of occurrences of rolling a value of 6 where the die would be considered fair. Statistically significant deviation from the expected number of outcomes with a value of 6 will render the die unfair.

______



Below we determine expected occurrences of 6 in a trial of 30 rolls.
```{r}
theoretical_prob = 1/6
n_pp2 = 30
occurences_pp2 = theoretical_prob * n_pp2
occurences_pp2
```

______


Now, we determine standard error for this trial.
```{r}
se_pp2 = sqrt(n_pp2*(theoretical_prob*(1-theoretical_prob)))
se_pp2
```

______


In order to determine the range of fair occurrences of 6 with confidence level of 90%, we use a z-score of 1.645.
```{r}
z_90 = 1.645
distance_pp2 = se_pp2 * z_90
floor_pp2 = occurences_pp2 - distance_pp2
ceiling_pp2 = occurences_pp2 + distance_pp2
range_pp2 = c(floor_pp2, ceiling_pp2)
```


```{r}
range_pp2
```

______


If a fair die is rolled 30 times, the likely amount of occurrences for 6 should be between 2 and 8 times, inclusive. We will reject H~0~ if 6 is drawn less than 2 times or more than 8 times.


______


```{r}
dice.roll <- sample(1:6, size = 30, replace = TRUE)
test_pp2 <- table(dice.roll)
test_pp2
```

Given an outcome of 4 occurrences of value 6, we fail to reject H~0~ for PP2. All other sides also had an outcome within the range of 2 and 8.


______


PP3

For our third possible protocol, n = 100. To determine the interval of the number outcomes with the value of 6 that would indicate the die should be considered fair, we are applying a 90% confidence level. If the number of outcomes with a value of 6 is outside this interval, we will consider the die unfair. We kept a 90% confidence level to maintain consistency across our experiments.

______


Below we determine expected occurrences of 6 in a trial of 100 rolls.
```{r}
theoretical_prob = 1/6
n_pp3 = 100
occurences_pp3 = theoretical_prob * n_pp3
occurences_pp3
```

______


Now, we determine standard error for this trial.
```{r}
se_pp3 = sqrt(n_pp3*(theoretical_prob*(1-theoretical_prob)))
se_pp3
```

______


In order to determine the range of fair occurrences of 6 with confidence level of 90%, we use a z-score of 1.645.
```{r}
z_90 = 1.645
distance_pp3 = se_pp3 * z_90
floor_pp3 = occurences_pp3 - distance_pp3
ceiling_pp3 = occurences_pp3 + distance_pp3
range_pp3 = c(floor_pp3, ceiling_pp3)
range_pp3
```


______



If a fair die is rolled 100 times, the likely amount of occurrences for 6 should be between 10 and 23 times. We reject H~0~ if the the number of occurrences of value 6 proves $\leq 10$ or $\geq 23$.


______


Hypothesis test PP3: 
```{r}
dice.roll <- sample(1:6, size = 100, replace = TRUE)
test_pp3 <- table(dice.roll)
test_pp3
```


Our results from the test yield a number of occurrences of 6 within the identified range, thus we fail to reject H~0~.