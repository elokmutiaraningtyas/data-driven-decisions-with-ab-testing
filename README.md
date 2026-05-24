# A/B Testing Search Ranking Algorithm

## 1) Data Background
We are testing a new search ranking algorithm for an online travel agency
The goal is to see if it improves how often users book trips without making them take longer to book
We have session data showing when users logged in and how long it took them to book
We also have user data splitting them into a control group and a variant group
The product team only wants to launch this if it clearly boosts conversions without hurting booking speed

## 2) Analysis Method
First we merged the session and user data to track the experiment groups
We created a new conversion column to flag if a session ended in a booking
We ran a sample ratio mismatch check to make sure the control and variant split was actually fair
We used a proportions Z-test to see if the new algorithm significantly increased conversion rates
We used a T-test to check our guardrail metric and ensure time to book did not get worse
Finally we calculated the effect sizes to measure the actual percentage impact

## 3) Libraries Used & Data Structure
We used pandas to join the tables and shape the data into binary flags and continuous variables
Scipy stats provided the chi-square test to verify our user split
Statsmodels gave us the proportions Z-test to evaluate the binary conversion goal
Pingouin provided the T-test to compare the continuous time to book data

## 4) Results & Conclusion
The sample ratio mismatch check passed meaning our experiment split was valid
The primary conversion metric showed a significant 14% increase with a p-value of 0.0002
The guardrail metric for time to book was not statistically significant and showed a tiny decrease in time
Since conversions went up and booking time did not get worse we met all criteria
The final recommendation is a confident yes to roll out the new search algorithm to all users
