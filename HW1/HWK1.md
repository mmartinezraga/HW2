Authors: Dorothy Gay, Monica Martinez-Raga, Patrick Sinclair

Question 3 - Dice Roll
----------------------

### Part 1 - A Fair Die

By setting the interval 1:6 as an R Object **die**, we were able to
write a function that generates a random sample of numbers from the
interval. We allowed the sample to replace outcomes so the function
simulates a roll of a fair die and set the sample size to 20.

The command **dice** will produce the same set of randomly generated
numbers each time it is executed. If we wish to view different outcomes,
we can execute the function **roll**.

    dice

    ##  [1] 6 2 3 2 5 5 5 2 6 6 1 3 3 4 6 3 3 1 2 2

    roll()

    ##  [1] 3 4 3 5 4 5 4 6 4 4 5 5 6 6 5 6 5 6 3 2

Using classical probability, we would expect to see a 6 from the roll of
a fair die 1/6 times. For 20 trials, we would expect 6 to be the result
20\*(1/6) = 3.33 times.

In our **dice** trial, we saw a 6 on 4 occasions, or 1/5 times.

### Part 2 - Adjusted Dice

To adjust our die, we created a new function for sampling the object
“die” and adjusted the probability within the function. Initially we had
changed the sample size and prevented the sample from replacing outcomes
but adjusting the probability of each outcome made for a more
challenging and interesting learning experience!

    # rollw <- function(die = 1:6){
    #   dice <- sample(die, size = 20, replace = TRUE, prob = c(1/10, 1/10, 1/10, 1/10, 1/10, 1/2))
    #   dice
    #   }
    # dicew <- sample(die, size = 20, replace = TRUE, prob = c(1/10, 1/10, 1/10, 1/10, 1/10, 1/2)) 

As with our fair die, the object *dicew* will return the same set of
weighted outcomes. *rollw* will produce a new set of outcomes each time
it is executed.

    dicew

    ##  [1] 5 4 3 2 5 1 4 3 3 5 6 6 2 4 6 4 6 2 6 6

    rollw()

    ##  [1] 6 6 6 6 4 6 5 6 5 3 6 6 1 1 5 2 6 3 2 4

In *dicew*, the probability of rolling a 6 has been adjusted to 1/2,
well above the probability of 1/6 for a fair die. We would expect to see
a 6 rolled 10 times in 20 trials. The results from *dicew* showed 6
appearing 9 times out of 20, just below what we expected but more than
twice as often as we saw in out **dice** trial.

The code used to create the dice trials was written from Grolemund,
Garrett (2014). Hands-On Programming with R, 1st edition, Sebastopol:
O’Reilly Media.

Question 4 - PUMS Data
----------------------

### Part 1 - Replicating Commands from R Basics for Lecture I

Below is a summary of all the data.

    summary(acs2017_ny)

    ##       AGE            female         educ_nohs        educ_hs      
    ##  Min.   : 0.00   Min.   :0.0000   Min.   :0.000   Min.   :0.0000  
    ##  1st Qu.:22.00   1st Qu.:0.0000   1st Qu.:0.000   1st Qu.:0.0000  
    ##  Median :42.00   Median :1.0000   Median :0.000   Median :0.0000  
    ##  Mean   :41.57   Mean   :0.5156   Mean   :0.271   Mean   :0.2804  
    ##  3rd Qu.:60.00   3rd Qu.:1.0000   3rd Qu.:1.000   3rd Qu.:1.0000  
    ##  Max.   :95.00   Max.   :1.0000   Max.   :1.000   Max.   :1.0000  
    ##                                                                   
    ##  educ_somecoll    educ_college     educ_advdeg                  SCHOOL      
    ##  Min.   :0.000   Min.   :0.0000   Min.   :0.000   N/A              :  5569  
    ##  1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:0.000   No, not in school:144968  
    ##  Median :0.000   Median :0.0000   Median :0.000   Yes, in school   : 46048  
    ##  Mean   :0.173   Mean   :0.1567   Mean   :0.119   Missing          :     0  
    ##  3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:0.000                             
    ##  Max.   :1.000   Max.   :1.0000   Max.   :1.000                             
    ##                                                                             
    ##                         EDUC      
    ##  Grade 12                 :55119  
    ##  4 years of college       :30802  
    ##  5+ years of college      :23385  
    ##  1 year of college        :19947  
    ##  Nursery school to grade 4:14240  
    ##  2 years of college       :14065  
    ##  (Other)                  :39027  
    ##                                           EDUCD      
    ##  Regular high school diploma                 :35689  
    ##  Bachelor's degree                           :30802  
    ##  1 or more years of college credit, no degree:19947  
    ##  Master's degree                             :17010  
    ##  Associate's degree, type not specified      :14065  
    ##  Some college, but less than 1 year          : 9086  
    ##  (Other)                                     :69986  
    ##                                      DEGFIELD     
    ##  N/A                                     :142398  
    ##  Business                                :  9802  
    ##  Education Administration and Teaching   :  6708  
    ##  Social Sciences                         :  4836  
    ##  Medical and Health Sciences and Services:  3919  
    ##  Fine Arts                               :  3491  
    ##  (Other)                                 : 25431  
    ##                                   DEGFIELDD     
    ##  N/A                                   :142398  
    ##  Psychology                            :  2926  
    ##  Business Management and Administration:  2501  
    ##  Accounting                            :  2284  
    ##  General Education                     :  2238  
    ##  English Language and Literature       :  2202  
    ##  (Other)                               : 42036  
    ##                                  DEGFIELD2     
    ##  N/A                                  :190425  
    ##  Business                             :   972  
    ##  Social Sciences                      :   853  
    ##  Education Administration and Teaching:   611  
    ##  Fine Arts                            :   465  
    ##  Communications                       :   352  
    ##  (Other)                              :  2907  
    ##                                                            DEGFIELD2D    
    ##  N/A                                                            :190425  
    ##  Psychology                                                     :   284  
    ##  Economics                                                      :   260  
    ##  Political Science and Government                               :   243  
    ##  Business Management and Administration                         :   217  
    ##  French, German, Latin and Other Common Foreign Language Studies:   205  
    ##  (Other)                                                        :  4951  
    ##       PUMA            GQ           OWNERSHP       OWNERSHPD        MORTGAGE    
    ##  Min.   : 100   Min.   :1.000   Min.   :0.000   Min.   : 0.00   Min.   :0.000  
    ##  1st Qu.:1500   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:12.00   1st Qu.:0.000  
    ##  Median :3201   Median :1.000   Median :1.000   Median :13.00   Median :1.000  
    ##  Mean   :2713   Mean   :1.148   Mean   :1.266   Mean   :14.95   Mean   :1.453  
    ##  3rd Qu.:3902   3rd Qu.:1.000   3rd Qu.:2.000   3rd Qu.:22.00   3rd Qu.:3.000  
    ##  Max.   :4114   Max.   :5.000   Max.   :2.000   Max.   :22.00   Max.   :4.000  
    ##                                                                                
    ##     OWNCOST           RENT         COSTELEC       COSTGAS        COSTWATR   
    ##  Min.   :    0   Min.   :   0   Min.   :   0   Min.   :   0   Min.   :   0  
    ##  1st Qu.: 1208   1st Qu.:   0   1st Qu.: 960   1st Qu.: 840   1st Qu.: 320  
    ##  Median : 2891   Median :   0   Median :1560   Median :2400   Median :1400  
    ##  Mean   :38582   Mean   : 393   Mean   :2311   Mean   :5032   Mean   :4836  
    ##  3rd Qu.:99999   3rd Qu.: 630   3rd Qu.:2520   3rd Qu.:9993   3rd Qu.:9993  
    ##  Max.   :99999   Max.   :3800   Max.   :9997   Max.   :9997   Max.   :9997  
    ##                                                                             
    ##     COSTFUEL       HHINCOME          FOODSTMP        LINGISOL    
    ##  Min.   :   0   Min.   : -11800   Min.   :1.000   Min.   :0.000  
    ##  1st Qu.:9993   1st Qu.:  41600   1st Qu.:1.000   1st Qu.:1.000  
    ##  Median :9993   Median :  81700   Median :1.000   Median :1.000  
    ##  Mean   :7935   Mean   : 114902   Mean   :1.147   Mean   :1.002  
    ##  3rd Qu.:9993   3rd Qu.: 140900   3rd Qu.:1.000   3rd Qu.:1.000  
    ##  Max.   :9997   Max.   :2030000   Max.   :2.000   Max.   :2.000  
    ##                 NA's   :10630                                    
    ##      ROOMS           BUILTYR2         UNITSSTR        FUELHEAT    
    ##  Min.   : 0.000   Min.   : 0.000   Min.   : 0.00   Min.   :0.000  
    ##  1st Qu.: 4.000   1st Qu.: 1.000   1st Qu.: 3.00   1st Qu.:2.000  
    ##  Median : 6.000   Median : 3.000   Median : 3.00   Median :2.000  
    ##  Mean   : 5.887   Mean   : 3.711   Mean   : 4.39   Mean   :2.959  
    ##  3rd Qu.: 8.000   3rd Qu.: 5.000   3rd Qu.: 6.00   3rd Qu.:4.000  
    ##  Max.   :16.000   Max.   :22.000   Max.   :10.00   Max.   :9.000  
    ##                                                                   
    ##       SSMC            FAMSIZE           NCHILD           NCHLT5       
    ##  Min.   :0.00000   Min.   : 1.000   Min.   :0.0000   Min.   :0.00000  
    ##  1st Qu.:0.00000   1st Qu.: 2.000   1st Qu.:0.0000   1st Qu.:0.00000  
    ##  Median :0.00000   Median : 3.000   Median :0.0000   Median :0.00000  
    ##  Mean   :0.01102   Mean   : 3.087   Mean   :0.5009   Mean   :0.08441  
    ##  3rd Qu.:0.00000   3rd Qu.: 4.000   3rd Qu.:1.0000   3rd Qu.:0.00000  
    ##  Max.   :2.00000   Max.   :19.000   Max.   :9.0000   Max.   :5.00000  
    ##                                                                       
    ##      RELATE          RELATED           MARST            RACE          RACED    
    ##  Min.   : 1.000   Min.   : 101.0   Min.   :1.000   Min.   :1.00   Min.   :100  
    ##  1st Qu.: 1.000   1st Qu.: 101.0   1st Qu.:1.000   1st Qu.:1.00   1st Qu.:100  
    ##  Median : 2.000   Median : 201.0   Median :5.000   Median :1.00   Median :100  
    ##  Mean   : 3.307   Mean   : 335.6   Mean   :3.742   Mean   :2.03   Mean   :205  
    ##  3rd Qu.: 3.000   3rd Qu.: 301.0   3rd Qu.:6.000   3rd Qu.:2.00   3rd Qu.:200  
    ##  Max.   :13.000   Max.   :1301.0   Max.   :6.000   Max.   :9.00   Max.   :990  
    ##                                                                                
    ##      HISPAN          HISPAND                  BPL        
    ##  Min.   :0.0000   Min.   :  0.00   New York     :128517  
    ##  1st Qu.:0.0000   1st Qu.:  0.00   West Indies  :  8481  
    ##  Median :0.0000   Median :  0.00   China        :  4964  
    ##  Mean   :0.4153   Mean   : 44.75   SOUTH AMERICA:  4957  
    ##  3rd Qu.:0.0000   3rd Qu.:  0.00   India        :  3476  
    ##  Max.   :4.0000   Max.   :498.00   Pennsylvania :  3303  
    ##                                    (Other)      : 42887  
    ##                  BPLD                            ANCESTR1    
    ##  New York          :128517   Not Reported            :32021  
    ##  China             :  4116   Italian                 :20577  
    ##  Dominican Republic:  3517   Irish, various subheads,:16388  
    ##  Pennsylvania      :  3303   German                  :12781  
    ##  New Jersey        :  3127   African-American        : 9559  
    ##  Puerto Rico       :  2272   United States           : 8209  
    ##  (Other)           : 51733   (Other)                 :97050  
    ##                                    ANCESTR1D             ANCESTR2     
    ##  Not Reported                           :32021   Not Reported:141487  
    ##  Italian (1990-2000, ACS, PRCS)         :20577   German      :  9476  
    ##  Irish                                  :15651   Irish       :  9238  
    ##  German (1990-2000, ACS/PRCS)           :12605   English     :  4895  
    ##  African-American (1990-2000, ACS, PRCS): 9559   Italian     :  4531  
    ##  United States                          : 8209   Polish      :  3113  
    ##  (Other)                                :97963   (Other)     : 23845  
    ##                           ANCESTR2D         CITIZEN          YRSUSA1      
    ##  Not Reported                  :141487   Min.   :0.0000   Min.   : 0.000  
    ##  German (1990-2000, ACS, PRCS) :  9441   1st Qu.:0.0000   1st Qu.: 0.000  
    ##  Irish                         :  8809   Median :0.0000   Median : 0.000  
    ##  English                       :  4895   Mean   :0.4793   Mean   : 5.377  
    ##  Italian (1990-2000, ACS, PRCS):  4531   3rd Qu.:0.0000   3rd Qu.: 0.000  
    ##  Polish                        :  3113   Max.   :3.0000   Max.   :92.000  
    ##  (Other)                       : 24309                                    
    ##     HCOVANY         HCOVPRIV         SEX            EMPSTAT     
    ##  Min.   :1.000   Min.   :1.000   Male  : 95222   Min.   :0.000  
    ##  1st Qu.:2.000   1st Qu.:1.000   Female:101363   1st Qu.:1.000  
    ##  Median :2.000   Median :2.000                   Median :1.000  
    ##  Mean   :1.951   Mean   :1.691                   Mean   :1.514  
    ##  3rd Qu.:2.000   3rd Qu.:2.000                   3rd Qu.:3.000  
    ##  Max.   :2.000   Max.   :2.000                   Max.   :3.000  
    ##                                                                 
    ##     EMPSTATD        LABFORCE          OCC              IND       
    ##  Min.   : 0.00   Min.   :0.000   0      : 79987   0      :79987  
    ##  1st Qu.:10.00   1st Qu.:1.000   2310   :  3494   7860   : 9025  
    ##  Median :10.00   Median :2.000   5700   :  3235   8680   : 6354  
    ##  Mean   :15.16   Mean   :1.331   430    :  3025   770    : 6279  
    ##  3rd Qu.:30.00   3rd Qu.:2.000   4720   :  2666   8190   : 5873  
    ##  Max.   :30.00   Max.   :2.000   4760   :  2563   7870   : 4041  
    ##                                  (Other):101615   (Other):85026  
    ##     CLASSWKR       CLASSWKRD        WKSWORK2        UHRSWORK    
    ##  Min.   :0.000   Min.   : 0.00   Min.   :0.000   Min.   : 0.00  
    ##  1st Qu.:0.000   1st Qu.: 0.00   1st Qu.:0.000   1st Qu.: 0.00  
    ##  Median :2.000   Median :22.00   Median :1.000   Median :12.00  
    ##  Mean   :1.116   Mean   :13.03   Mean   :2.701   Mean   :19.77  
    ##  3rd Qu.:2.000   3rd Qu.:22.00   3rd Qu.:6.000   3rd Qu.:40.00  
    ##  Max.   :2.000   Max.   :29.00   Max.   :6.000   Max.   :99.00  
    ##                                                                 
    ##      INCTOT           FTOTINC           INCWAGE          POVERTY     
    ##  Min.   :  -7300   Min.   : -11800   Min.   :     0   Min.   :  0.0  
    ##  1st Qu.:   8000   1st Qu.:  35550   1st Qu.:     0   1st Qu.:159.0  
    ##  Median :  25000   Median :  74000   Median : 10000   Median :351.0  
    ##  Mean   :  45245   Mean   : 107111   Mean   : 33796   Mean   :318.7  
    ##  3rd Qu.:  56500   3rd Qu.: 132438   3rd Qu.: 47000   3rd Qu.:501.0  
    ##  Max.   :1563000   Max.   :2030000   Max.   :638000   Max.   :501.0  
    ##  NA's   :31129     NA's   :10817     NA's   :33427                   
    ##     MIGRATE1       MIGRATE1D        MIGPLAC1         MIGCOUNTY1     
    ##  Min.   :0.000   Min.   : 0.00   Min.   :  0.000   Min.   :  0.000  
    ##  1st Qu.:1.000   1st Qu.:10.00   1st Qu.:  0.000   1st Qu.:  0.000  
    ##  Median :1.000   Median :10.00   Median :  0.000   Median :  0.000  
    ##  Mean   :1.122   Mean   :11.51   Mean   :  6.184   Mean   :  4.117  
    ##  3rd Qu.:1.000   3rd Qu.:10.00   3rd Qu.:  0.000   3rd Qu.:  0.000  
    ##  Max.   :4.000   Max.   :40.00   Max.   :900.000   Max.   :810.000  
    ##                                                                     
    ##     MIGPUMA1        VETSTAT          VETSTATD         PWPUMA00    
    ##  Min.   :    0   Min.   :0.0000   Min.   : 0.000   Min.   :    0  
    ##  1st Qu.:    0   1st Qu.:1.0000   1st Qu.:11.000   1st Qu.:    0  
    ##  Median :    0   Median :1.0000   Median :11.000   Median :    0  
    ##  Mean   :  277   Mean   :0.8621   Mean   : 9.412   Mean   : 1255  
    ##  3rd Qu.:    0   3rd Qu.:1.0000   3rd Qu.:11.000   3rd Qu.: 3100  
    ##  Max.   :70100   Max.   :2.0000   Max.   :20.000   Max.   :59300  
    ##                                                                   
    ##     TRANWORK         TRANTIME         DEPARTS           in_NYC      
    ##  Min.   : 0.000   Min.   :  0.00   Min.   :   0.0   Min.   :0.0000  
    ##  1st Qu.: 0.000   1st Qu.:  0.00   1st Qu.:   0.0   1st Qu.:0.0000  
    ##  Median : 0.000   Median :  0.00   Median :   0.0   Median :0.0000  
    ##  Mean   : 9.725   Mean   : 14.75   Mean   : 373.3   Mean   :0.3615  
    ##  3rd Qu.:10.000   3rd Qu.: 20.00   3rd Qu.: 732.0   3rd Qu.:1.0000  
    ##  Max.   :70.000   Max.   :138.00   Max.   :2345.0   Max.   :1.0000  
    ##                                                                     
    ##     in_Bronx       in_Manhattan       in_StatenI       in_Brooklyn   
    ##  Min.   :0.0000   Min.   :0.00000   Min.   :0.00000   Min.   :0.000  
    ##  1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000  
    ##  Median :0.0000   Median :0.00000   Median :0.00000   Median :0.000  
    ##  Mean   :0.0538   Mean   :0.04981   Mean   :0.02084   Mean   :0.126  
    ##  3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000  
    ##  Max.   :1.0000   Max.   :1.00000   Max.   :1.00000   Max.   :1.000  
    ##                                                                      
    ##    in_Queens      in_Westchester      in_Nassau          Hispanic     
    ##  Min.   :0.0000   Min.   :0.00000   Min.   :0.00000   Min.   :0.0000  
    ##  1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.0000  
    ##  Median :0.0000   Median :0.00000   Median :0.00000   Median :0.0000  
    ##  Mean   :0.1111   Mean   :0.04413   Mean   :0.07032   Mean   :0.1387  
    ##  3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.0000  
    ##  Max.   :1.0000   Max.   :1.00000   Max.   :1.00000   Max.   :1.0000  
    ##                                                                       
    ##     Hisp_Mex          Hisp_PR         Hisp_Cuban         Hisp_DomR      
    ##  Min.   :0.00000   Min.   :0.0000   Min.   :0.000000   Min.   :0.00000  
    ##  1st Qu.:0.00000   1st Qu.:0.0000   1st Qu.:0.000000   1st Qu.:0.00000  
    ##  Median :0.00000   Median :0.0000   Median :0.000000   Median :0.00000  
    ##  Mean   :0.01626   Mean   :0.0436   Mean   :0.003403   Mean   :0.02827  
    ##  3rd Qu.:0.00000   3rd Qu.:0.0000   3rd Qu.:0.000000   3rd Qu.:0.00000  
    ##  Max.   :1.00000   Max.   :1.0000   Max.   :1.000000   Max.   :1.00000  
    ##                                                                         
    ##      white             AfAm          Amindian            Asian        
    ##  Min.   :0.0000   Min.   :0.000   Min.   :0.000000   Min.   :0.00000  
    ##  1st Qu.:0.0000   1st Qu.:0.000   1st Qu.:0.000000   1st Qu.:0.00000  
    ##  Median :1.0000   Median :0.000   Median :0.000000   Median :0.00000  
    ##  Mean   :0.6997   Mean   :0.125   Mean   :0.003779   Mean   :0.08656  
    ##  3rd Qu.:1.0000   3rd Qu.:0.000   3rd Qu.:0.000000   3rd Qu.:0.00000  
    ##  Max.   :1.0000   Max.   :1.000   Max.   :1.000000   Max.   :1.00000  
    ##                                                                       
    ##     race_oth        unmarried       veteran        has_AnyHealthIns
    ##  Min.   :0.0000   Min.   :0.00   Min.   :0.00000   Min.   :0.0000  
    ##  1st Qu.:0.0000   1st Qu.:0.00   1st Qu.:0.00000   1st Qu.:1.0000  
    ##  Median :0.0000   Median :0.00   Median :0.00000   Median :1.0000  
    ##  Mean   :0.1324   Mean   :0.45   Mean   :0.04443   Mean   :0.9513  
    ##  3rd Qu.:0.0000   3rd Qu.:1.00   3rd Qu.:0.00000   3rd Qu.:1.0000  
    ##  Max.   :1.0000   Max.   :1.00   Max.   :1.00000   Max.   :1.0000  
    ##                                                                    
    ##  has_PvtHealthIns  Commute_car      Commute_bus      Commute_subway   
    ##  Min.   :0.0000   Min.   :0.0000   Min.   :0.00000   Min.   :0.00000  
    ##  1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000  
    ##  Median :1.0000   Median :0.0000   Median :0.00000   Median :0.00000  
    ##  Mean   :0.6906   Mean   :0.2997   Mean   :0.02162   Mean   :0.07468  
    ##  3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:0.00000  
    ##  Max.   :1.0000   Max.   :1.0000   Max.   :1.00000   Max.   :1.00000  
    ##                                                                       
    ##   Commute_rail     Commute_other     below_povertyline below_150poverty
    ##  Min.   :0.00000   Min.   :0.00000   Min.   :0.000     Min.   :0.0000  
    ##  1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000     1st Qu.:0.0000  
    ##  Median :0.00000   Median :0.00000   Median :0.000     Median :0.0000  
    ##  Mean   :0.01332   Mean   :0.05506   Mean   :0.122     Mean   :0.1965  
    ##  3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000     3rd Qu.:0.0000  
    ##  Max.   :1.00000   Max.   :1.00000   Max.   :1.000     Max.   :1.0000  
    ##                                                                        
    ##  below_200poverty   foodstamps    
    ##  Min.   :0.0000   Min.   :0.0000  
    ##  1st Qu.:0.0000   1st Qu.:0.0000  
    ##  Median :0.0000   Median :0.0000  
    ##  Mean   :0.2676   Mean   :0.1465  
    ##  3rd Qu.:1.0000   3rd Qu.:0.0000  
    ##  Max.   :1.0000   Max.   :1.0000  
    ## 

The following code shows there are 196,585 rows in the dataset.

    print(NN_obs <- length(AGE))

    ## [1] 196585

The mean age of women in NYC is 42.72 years.

    summary(AGE[female == 1])

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    0.00   23.00   44.00   42.72   61.00   95.00

The mean age of men in NYC is 40.35 years.

    summary(AGE[!female])

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    0.00   21.00   40.00   40.35   59.00   95.00

Alternative ways to access summary figures: Female age statistics

    mean(AGE[female == 1])

    ## [1] 42.71629

    sd(AGE[female == 1])

    ## [1] 23.72012

Male age statistics

    mean(AGE[!female])

    ## [1] 40.35398

    sd(AGE[!female])

    ## [1] 23.1098

### Part 2 - Interesting Finds

For the purpose of exploring interesting statistics in the data, we
wanted to find differences in education attainment levels in men and
women. The results indicate that women generally attain more and higher
levels of formal education, and men had lower rates of high school
completion.

    educ_indx <- factor((educ_nohs + 2*educ_hs + 3*educ_somecoll + 4*educ_college + 5*educ_advdeg), levels=c(1,2,3,4,5),labels = c("No HS","HS","SmColl","Bach","Adv"))
    table(educ_indx,female)

    ##          female
    ## educ_indx     0     1
    ##    No HS  27180 26087
    ##    HS     27309 27810
    ##    SmColl 15847 18165
    ##    Bach   14632 16170
    ##    Adv    10254 13131

Question 5 - SP500 Index
------------------------

### Part 1 - Mean for time frame February 20, 2020 - September 1, 2020

Here we load in the SP500 data from 2-20-2020 to 9-1-2020

    library(readr)
    library(dplyr)
    library(ggplot2)

    S_P <- read_csv("S&P.csv")

    knitr::kable(summary(S_P))

<table>
<colgroup>
<col style="width: 2%" />
<col style="width: 18%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 17%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: left;">Date</th>
<th style="text-align: left;">Open</th>
<th style="text-align: left;">High</th>
<th style="text-align: left;">Low</th>
<th style="text-align: left;">Close</th>
<th style="text-align: left;">Adj Close</th>
<th style="text-align: left;">Volume</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"></td>
<td style="text-align: left;">Min. :2020-02-20</td>
<td style="text-align: left;">Min. :2291</td>
<td style="text-align: left;">Min. :2301</td>
<td style="text-align: left;">Min. :2192</td>
<td style="text-align: left;">Min. :2237</td>
<td style="text-align: left;">Min. :2237</td>
<td style="text-align: left;">Min. :3.193e+09</td>
</tr>
<tr class="even">
<td style="text-align: left;"></td>
<td style="text-align: left;">1st Qu.:2020-04-07</td>
<td style="text-align: left;">1st Qu.:2839</td>
<td style="text-align: left;">1st Qu.:2868</td>
<td style="text-align: left;">1st Qu.:2803</td>
<td style="text-align: left;">1st Qu.:2845</td>
<td style="text-align: left;">1st Qu.:2845</td>
<td style="text-align: left;">1st Qu.:4.473e+09</td>
</tr>
<tr class="odd">
<td style="text-align: left;"></td>
<td style="text-align: left;">Median :2020-05-27</td>
<td style="text-align: left;">Median :3064</td>
<td style="text-align: left;">Median :3090</td>
<td style="text-align: left;">Median :3014</td>
<td style="text-align: left;">Median :3054</td>
<td style="text-align: left;">Median :3054</td>
<td style="text-align: left;">Median :5.123e+09</td>
</tr>
<tr class="even">
<td style="text-align: left;"></td>
<td style="text-align: left;">Mean :2020-05-27</td>
<td style="text-align: left;">Mean :3018</td>
<td style="text-align: left;">Mean :3047</td>
<td style="text-align: left;">Mean :2985</td>
<td style="text-align: left;">Mean :3018</td>
<td style="text-align: left;">Mean :3018</td>
<td style="text-align: left;">Mean :5.499e+09</td>
</tr>
<tr class="odd">
<td style="text-align: left;"></td>
<td style="text-align: left;">3rd Qu.:2020-07-15</td>
<td style="text-align: left;">3rd Qu.:3225</td>
<td style="text-align: left;">3rd Qu.:3242</td>
<td style="text-align: left;">3rd Qu.:3205</td>
<td style="text-align: left;">3rd Qu.:3226</td>
<td style="text-align: left;">3rd Qu.:3226</td>
<td style="text-align: left;">3rd Qu.:6.373e+09</td>
</tr>
<tr class="even">
<td style="text-align: left;"></td>
<td style="text-align: left;">Max. :2020-09-01</td>
<td style="text-align: left;">Max. :3510</td>
<td style="text-align: left;">Max. :3528</td>
<td style="text-align: left;">Max. :3495</td>
<td style="text-align: left;">Max. :3527</td>
<td style="text-align: left;">Max. :3527</td>
<td style="text-align: left;">Max. :9.045e+09</td>
</tr>
</tbody>
</table>

Here we will add in a column called “Return”, calculated from the day’s
(Close-Open). Here are the concatenated results.

    S_P$Return <- S_P$Close-S_P$Open
    knitr::kable(head(S_P, n = 5))

<table>
<thead>
<tr class="header">
<th style="text-align: left;">Date</th>
<th style="text-align: right;">Open</th>
<th style="text-align: right;">High</th>
<th style="text-align: right;">Low</th>
<th style="text-align: right;">Close</th>
<th style="text-align: right;">Adj Close</th>
<th style="text-align: right;">Volume</th>
<th style="text-align: right;">Return</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">2020-02-20</td>
<td style="text-align: right;">3380.45</td>
<td style="text-align: right;">3389.15</td>
<td style="text-align: right;">3341.02</td>
<td style="text-align: right;">3373.23</td>
<td style="text-align: right;">3373.23</td>
<td style="text-align: right;">4007320000</td>
<td style="text-align: right;">-7.219971</td>
</tr>
<tr class="even">
<td style="text-align: left;">2020-02-21</td>
<td style="text-align: right;">3360.50</td>
<td style="text-align: right;">3360.76</td>
<td style="text-align: right;">3328.45</td>
<td style="text-align: right;">3337.75</td>
<td style="text-align: right;">3337.75</td>
<td style="text-align: right;">3899270000</td>
<td style="text-align: right;">-22.750000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">2020-02-24</td>
<td style="text-align: right;">3257.61</td>
<td style="text-align: right;">3259.81</td>
<td style="text-align: right;">3214.65</td>
<td style="text-align: right;">3225.89</td>
<td style="text-align: right;">3225.89</td>
<td style="text-align: right;">4842960000</td>
<td style="text-align: right;">-31.720214</td>
</tr>
<tr class="even">
<td style="text-align: left;">2020-02-25</td>
<td style="text-align: right;">3238.94</td>
<td style="text-align: right;">3246.99</td>
<td style="text-align: right;">3118.77</td>
<td style="text-align: right;">3128.21</td>
<td style="text-align: right;">3128.21</td>
<td style="text-align: right;">5591510000</td>
<td style="text-align: right;">-110.729980</td>
</tr>
<tr class="odd">
<td style="text-align: left;">2020-02-26</td>
<td style="text-align: right;">3139.90</td>
<td style="text-align: right;">3182.51</td>
<td style="text-align: right;">3108.99</td>
<td style="text-align: right;">3116.39</td>
<td style="text-align: right;">3116.39</td>
<td style="text-align: right;">5478110000</td>
<td style="text-align: right;">-23.510009</td>
</tr>
</tbody>
</table>

From “Return” we can calculate the mean.

    knitr::kable(mean(S_P$Return))

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">0.1786087</td>
</tr>
</tbody>
</table>

### Part 2 - Mean Return On The Day After a Previous Day’s Return Was Positive or Negative

Here we will utilize a Lead/Lag function to determine “Previous Return”
based on a previous day’s return.

    S_P$PreviousReturn <- lag(S_P$Return)
    knitr::kable(head(S_P, 5))

<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 8%" />
<col style="width: 8%" />
<col style="width: 8%" />
<col style="width: 8%" />
<col style="width: 10%" />
<col style="width: 12%" />
<col style="width: 13%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Date</th>
<th style="text-align: right;">Open</th>
<th style="text-align: right;">High</th>
<th style="text-align: right;">Low</th>
<th style="text-align: right;">Close</th>
<th style="text-align: right;">Adj Close</th>
<th style="text-align: right;">Volume</th>
<th style="text-align: right;">Return</th>
<th style="text-align: right;">PreviousReturn</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">2020-02-20</td>
<td style="text-align: right;">3380.45</td>
<td style="text-align: right;">3389.15</td>
<td style="text-align: right;">3341.02</td>
<td style="text-align: right;">3373.23</td>
<td style="text-align: right;">3373.23</td>
<td style="text-align: right;">4007320000</td>
<td style="text-align: right;">-7.219971</td>
<td style="text-align: right;">NA</td>
</tr>
<tr class="even">
<td style="text-align: left;">2020-02-21</td>
<td style="text-align: right;">3360.50</td>
<td style="text-align: right;">3360.76</td>
<td style="text-align: right;">3328.45</td>
<td style="text-align: right;">3337.75</td>
<td style="text-align: right;">3337.75</td>
<td style="text-align: right;">3899270000</td>
<td style="text-align: right;">-22.750000</td>
<td style="text-align: right;">-7.219971</td>
</tr>
<tr class="odd">
<td style="text-align: left;">2020-02-24</td>
<td style="text-align: right;">3257.61</td>
<td style="text-align: right;">3259.81</td>
<td style="text-align: right;">3214.65</td>
<td style="text-align: right;">3225.89</td>
<td style="text-align: right;">3225.89</td>
<td style="text-align: right;">4842960000</td>
<td style="text-align: right;">-31.720214</td>
<td style="text-align: right;">-22.750000</td>
</tr>
<tr class="even">
<td style="text-align: left;">2020-02-25</td>
<td style="text-align: right;">3238.94</td>
<td style="text-align: right;">3246.99</td>
<td style="text-align: right;">3118.77</td>
<td style="text-align: right;">3128.21</td>
<td style="text-align: right;">3128.21</td>
<td style="text-align: right;">5591510000</td>
<td style="text-align: right;">-110.729980</td>
<td style="text-align: right;">-31.720214</td>
</tr>
<tr class="odd">
<td style="text-align: left;">2020-02-26</td>
<td style="text-align: right;">3139.90</td>
<td style="text-align: right;">3182.51</td>
<td style="text-align: right;">3108.99</td>
<td style="text-align: right;">3116.39</td>
<td style="text-align: right;">3116.39</td>
<td style="text-align: right;">5478110000</td>
<td style="text-align: right;">-23.510009</td>
<td style="text-align: right;">-110.729980</td>
</tr>
</tbody>
</table>

    ggplot(data=S_P, aes(x=Date, y=Close), name="Close over time") + geom_point() + geom_smooth()

![](EconometricsHW1---Copy_files/figure-markdown_strict/unnamed-chunk-15-1.png)

Here we filter “PreviousReturn” to find the previous day’s return values
that are positive. In the summary we can see the mean return on a
previous day’s positive return is -7.9192.

    summary(filter(S_P, PreviousReturn >= 0) $Return)

    ##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
    ## -127.0200  -22.4602   -0.4399   -7.9192   14.4600  128.7800

Similarly, we can filter by and summarize negative “PreviousReturn”
values to find the mean returns on days where the previous day’s return
values were negative. As shown, the mean returns on these days are
11.06.

    summary(filter(S_P, PreviousReturn <= 0) $Return)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ## -150.22  -23.15   19.18   11.06   36.53  141.03

### Part 3 - Mean Return On The Day After a Previous Two Day’s Returns Were Positive or Negative

To determine mean on days where the previous two day’s returns were
negative we simply set another conditional to consider values where
returns on both days prior were negative - where the mean is 10.67:

    S_P$PreviousTwoDayReturn <- lag(S_P$PreviousReturn)
    summary(filter(S_P, PreviousReturn <= 0 & PreviousTwoDayReturn <= 0) $Return)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ## -121.43  -28.17   16.64   10.67   52.80  141.03

And when returns on two days prior are positive where the mean is 2.295:

    S_P$PreviousTwoDayReturn <- lag(S_P$PreviousReturn)
    summary(filter(S_P, PreviousReturn >= 0 & PreviousTwoDayReturn >= 0) $Return)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ## -93.090 -13.027   4.310   2.295  15.713 128.780

### Part 4 - The Hot Hands Fallacy and How It Relates To Our Findings

    ReturnsBasedOnHistory <- matrix(c(-7.9192,11.0600,2.2950,10.6700
    ), ncol=2)
    colnames(ReturnsBasedOnHistory) <- c('Past Day Return', 'Past Two Days Return')
    rownames(ReturnsBasedOnHistory) <- c('Positive', 'Negative')
    ReturnsBasedOnHistory.table <- as.table(ReturnsBasedOnHistory)
    ReturnsBasedOnHistory

    ##          Past Day Return Past Two Days Return
    ## Positive         -7.9192                2.295
    ## Negative         11.0600               10.670

Based on the data from SP500 spanning from February 20, 2020 - September
1, 2020, we notice that the day after a positive return, the mean return
is strongly negative. However, the day after two positive returns, the
mean return comes up slightly back to positive. Similarly, the day after
a negative return, the mean return is starkly positive but after two
days the positivity of the return decreases. From here we can infer that
with a larger sample size, the returns based on historical movement
begin to normalize, approaching the mean of the entire time frame’s
return of 0.1786.

The time frame we chose was remarkably volatile. During this time, we
can define short-term investment as investment based on one day’s
historical data and longer term investment as based on historical data
of greater than one day. According to the Hot Hands Fallacy, short term
investors may perceive the market’s movement as “hot” if the previous
day’s returns were either wildly positive or negative, depending on
whether they were choosing to buy or sell in relation to the market’s
movements. According to our data, if they were to act on this perception
of a “hot” movement in the short term, they would benefit from the hot
hands fallacy so long as they made their moves within the day. However,
if they acted on the perception over a period of days, their returns in
either direction would have gone down over the amount of time in which
they held. Similarly, a long-term investor may be lured by the prospect
of making moves and the perception of a “hot” deal, but they were found
not to have lost tremendously nor gained tremendously if they were to
wait out the high market volatility as the returns approach the slightly
positive 9 month mean over time.

### Part 5 - A Question For Discussion

Given institutions have greater ability to be selective in making their
predictions when assessing streaks in the market, are they able to
leverage trading large volumes to manipulate whether positive return
streaks continue or cease?
