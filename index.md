---
title       : Vacation Savings Calculator 
subtitle    : How and why to use the Vacation Savings Calculator app
author      : Matthew Fergusson
job         : Assignment for Developing Data Products class through Johns Hopkins
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Why use the Vacation Savings Calculator

#### Have you ever thought about a trip you saw in a magazine, but wondered whether or not you could ever really afford it?


#####  If you have then this is your opporunity to see what it would take to make that dream a reality.


#### All you have to do is:

1. Decide when you want to take the vacation
2. Estimate how much the vacation will cost
3. Know a little bit about your own financial and credit situation

--- .class #id 

## Step 1: Entering Your Information

#### For an example lets start off with some sample Inputs.

##### Below are sample inputs that reflect the actual entry fields of the app


```r
Vacation_Cost <- 3000  #Cost of Vacation
Weeks_till_Trip <- 25  #Weeks Until the Planned Trip
Cash_in_Bank <- 500    #Cash in the bank that can be used for the trip
Total_Credit <- 5000   #Total Credit from All Credit Lines
Credit_Used <- 250     #Total Credit Used from All Credit Lines
Pct_Credit_Used <- 25  #The % of your total credit that you are willing to use for vacation
Weekly_Earnings <- 500 #Weekly takehome pay after pre-tax deductions
Monthly_Rent <- 1000   #Monthly rent or mortgage payment
Other_Exp <- 500       #Other Monthly Mandatory Expenses
Pref_Budget <- 250     #How much you normally spend in a week
```

--- .class #id 

## Step 2: What is being calculated

#### The app calculates your maximum weekly budget for normal spending under 3 scenarios to pay for vacation:

1. Maxing out your credit card 
2. Using only the amount of credit you are comfortable with
3. not using any credit at all for the vacation


```r
#1)
MaxOUT_Credit <- ((Total_Credit - Credit_Used) + Cash_in_Bank + Weekly_Earnings * Weeks_till_Trip - (Monthly_Rent * (12/52) + Other_Exp * (12/52)) * Weeks_till_Trip) / Weeks_till_Trip - Vacation_Cost / Weeks_till_Trip
#2)
Comfortable_Credit <- (max(Total_Credit * (Pct_Credit_Used/100) - Credit_Used,0) + Cash_in_Bank + Weekly_Earnings * Weeks_till_Trip -  (Monthly_Rent * (12/52) + Other_Exp * (12/52)) * Weeks_till_Trip)/Weeks_till_Trip - Vacation_Cost/Weeks_till_Trip
#3)
No_Credit <- (Cash_in_Bank + Weekly_Earnings * Weeks_till_Trip - (Monthly_Rent * (12/52) + Other_Exp * (12/52)) * Weeks_till_Trip)/Weeks_till_Trip - Vacation_Cost/Weeks_till_Trip
```



--- .class #id 


## Step 3: Explaining the results

#### Here you can see what the output of the app will be given the previous inputs

1. Maxing out your credit card 

```
## [1] 243.8462
```
2. Using only the amount of credit you are comfortable with

```
## [1] 93.84615
```
3. not using any credit at all for the vacation

```
## [1] 53.84615
```

#### Summary:

```
## [1] "You can barely afford the vacation. You will have to cut back your weekly budget. The YOLO attitude is in vogue, but now you are starting to get reckless."
```

--- .class #id 

## Step 4: Flying, Driving, or Sailing Away to Your Dream Come True

### With the information provided by this app you will be off to visit whatever place you may desire. That is asa long as it's in the budget

### Thank you for your attention, please let me know if you have any questions
