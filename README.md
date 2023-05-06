# Multiclass-Classification-Model

<h2>Description: Predicting Users' Approved Risk Class</h2>
<p>
<b>Problem</b>: most users who come to our site generate a quote for life insurance before starting an application.  The only information a user provides at quote is age, height, weight, gender, and whether they use tobacco.  We use Body Mass Index (BMI) based on height and weight to put a user into a risk class, which along with gender drives pricing.  The problem is that based on this limited information, over half of our users are put into the best risk class, but less than 15% stay in this risk class after their application is approved.  As risk class drives price, this results in a mismatch between the quoted price and the price users see after completing an application and being approved.
<br>

An ideal solution would involve finding a better prediction of approved risk class at quote, since this the is driver of price.  Right now, only 33% of users are in the same risk class once approved.  The challenge is identifying user inputs in the application that could potentially be moved to the quote portion of the user experience to better predict approved risk class earlier in the process.
</p>

<b>Solution</b>:
After exploring various approaches to the problem, including multiclass classification, binary classification, and regression, I found that the best solution was a two-model solution using XGBoost:
1.	Binary classification: predicting approved vs. declined.  This was important as most (~60-70%) users who receive a quote are not approved.  
2.	Multiclass classification: for users predicted to be approved, we predict a user’s approved risk class, which directly drives price given their age and gender.

This solution improved upon the way that we were currently generating quotes in the following ways: 
-	Accuracy is improved by 16%
-	Users seeing a lower price at quote than approved is reduced by 42%
-	Users classified in a risk class more than one risk class below what they were quoted (indicating a larger price increase) was reduced from 45%  to 7.4%
-	Users predicted to be declined will be shown the price associated with the riskiest risk class, which may deter them from starting an application and could save significant underwriting costs
-	Six of the Top 20 features in terms of importance to the model are already collected in the current quote experience (five are in the Top 10).  This makes the solution actionable, as this is a reasonable amount of data collection to move to the 

<h2>Languages Used</h2>

- <b>SQL</b> 
- <b>Python</b>

<h2>Models Used </h2>

- <b>Random Forest Classifier</b>
- <b>Random Forest Regressor</b>
- <b>Catboost</b>
- <b>XGBoost</b>

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
