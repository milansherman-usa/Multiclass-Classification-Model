# Multiclass-Classification-Model

<h2>Languages Used</h2>

- <b>SQL</b> 
- <b>Python</b>

<h2>Models Used </h2>

- <b>Random Forest Classifier</b>
- <b>Random Forest Regressor</b>
- <b>Catboost</b>
- <b>XGBoost</b>


<h2>Description: Predicting Users' Approved Risk Class</h2>
<p>
<b>Problem</b>: most users generate a quote for life insurance before starting an application.  The only information a user provides at quote is age, height, weight, gender, and whether they use tobacco.  A user is put into a risk class based on Body Mass Index (BMI) which is derived from height and weight, and drives pricing. The problem is that based on this limited information most users are put into the best risk class, but less than 15% stay in this risk class after their application is approved.  This results in a mismatch between the quoted price and the price users see after completing an application and being approved. Part of the challenge is identifying user inputs in the application that could potentially be moved to the quote portion of the user experience to better predict approved risk class earlier in the process.
</p>

<b>Solution</b>:
After exploring various approaches to the problem, including multiclass classification, binary classification, and regression, I found that the best solution was a two-model solution using XGBoost:
1.	Binary classification: predicting approved vs. declined.  This was important as most (~60-70%) users who receive a quote are not approved.  
2.	Multiclass classification: for users predicted to be approved, we predict a user’s approved risk class, which directly drives price given their age and gender.

This solution improved upon the way that we were currently generating quotes in the following ways: 
-	Accuracy is improved by 16%
-	Users seeing a lower price at quote than approved is reduced by 42%
-	Users classified in a risk class more than one risk class below what they were quoted (indicating a larger price increase) was reduced from 45%  to 7.4%
-	Users predicted to be declined could be shown the price associated with the riskiest risk class, i.e., the largest price, which may deter them from starting an application and could save significant underwriting costs
-	Six of the Top 20 features in terms of importance to the model are already collected in the current quote experience (five are in the Top 10).  This makes the solution actionable, as this is a reasonable amount of data collection to move to the quote portion of the user experience.
