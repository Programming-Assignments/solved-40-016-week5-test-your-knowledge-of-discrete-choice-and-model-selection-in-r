Download Link: https://assignmentchef.com/product/solved-40-016-week5-test-your-knowledge-of-discrete-choice-and-model-selection-in-r
<br>



<ol>

 <li>This problem set uses data on the choice of the heating system in California houses. The dataset in the file Heating.csv consists of observations for 900 single-family houses in California that were newly built and had central air-conditioning. The choice is among heating systems. Five types of systems are considered to have been possible:</li>

</ol>

<ul>

 <li><strong>gas central </strong>(gc)</li>

 <li><strong>gas room </strong>(gr)</li>

 <li><strong>electric central </strong>(ec)</li>

 <li><strong>electric room </strong>(er)</li>

 <li><strong>heat pump </strong>(hp)</li>

</ul>

There are 900 observations where the variables are:

<ul>

 <li>idcase: observation number (1-900)</li>

 <li>depvar: identifies the chosen alternative (gc, gr, ec, er, hp)</li>

 <li>alt: installation cost for the 5 alternatives (alt = gc, gr, ec, er, hp)</li>

 <li>alt: annual operating cost for the 5 alternatives (alt = gc, gr, ec, er, hp)</li>

 <li>income: annual income of the household (in tens of thousands of dollars)</li>

 <li>agehed: age of the household head</li>

 <li>rooms: number of rooms in the house</li>

 <li>region: a factor with levels ncostl (northern coastal region), scostl (southern coastal region), mountn (mountain region), valley (central valley region)</li>

</ul>

Note that the attributes of the alternatives, namely, installation cost and operating cost, take a different value for each alternative. Therefore, there are 5 installation costs (one for each of the 5 systems) and 5 operating costs. To estimate the logit model, the researcher needs data on the attributes of all the alternatives, not just the attributes for the chosen alternative. For example, it is not sufficient for the researcher to determine how much was paid for the system that was actually installed (i.e., the bill for the installation). The researcher needs to determine how much it would have cost to install each of the systems if they had been installed. The importance of costs in the choice process (i.e., the coeffiicients of installation and operating costs) is determined through comparison of the costs of the chosen system with the costs of the non-chosen systems.

For these data, the costs were calculated as the amount the system would cost if it were installed in the house, given the characteristics of the house (such as size), the price of gas and electricity in the house location, and the weather conditions in the area (which determine the necessary capacity of the system and the amount it will be run.) These cost are conditional on the house having central air-conditioning. (That’s why the installation cost of gas central is lower than that for gas room: the central system can use the air-conditioning ducts that have been installed.)

You will see that the first household chose alternative 1 (gas central), has an income of $70,000, the head of household is 25 years old, the house has 6 rooms, and is located in the north coastal area.

<ul>

 <li>Run a logit model with installation cost and operating cost as the only explanatory variables, without intercepts.

  <ol>

   <li>Do the estimated coefficients have the expected signs? ii. Are both coefficients significantly different from zero?</li>

  </ol></li>

</ul>

<ul>

 <li>Use the average of the probabilities to compute the predicted share. Compute the actual shares of houses with each system. How closely do the predicted shares match the actual shares of houses with each heating system?</li>

</ul>

<ol>

 <li>The ratio of coefficients usually provides economically meaningful information in discrete choice models. The willingness to pay (<em>wtp</em>) through higher installation cost for a one-dollar reduction in operating costs is the ratio of the operating cost coefficient to the installation cost coefficients What is the estimated <em>wtp </em>from this model? Note that the annual operating cost recurs every year while the installation cost is a one-time payment. Does the result make sense?</li>

</ol>

<ul>

 <li>The present value of the future operating costs is the discounted sum of operating costs over the life of the system: is the discount rate and <em>L </em>is the life of the system. As <em>L </em>rises, the <em>PV </em>approaches <em>OC/r</em>. Therefore, for a system with a sufficiently long life (which we will assume these systems have), a one-dollar reduction in <em>OC </em>reduces the present value of future operating costs by (1<em>/r</em>). This means that if the person choosing the system were incurring the installation costs and the operating costs over the life of the system, and rationally traded-off the two at a discount rate of <em>r</em>, the decision-maker’s <em>wtp </em>for operating cost reductions would be (1<em>/r</em>). Define a new variable lcc (lifecycle cost) that is defined as the sum of the installation cost and the (operating cost)/<em>r</em>. Run a logit model with the lifecycle cost as the only explanatory variable. Estimate the model for <em>r </em>= 0<em>.</em> Comment on the value of log-likelihood of the models obtained in (a) as compared to (b).</li>

 <li>Add alternative-specific constants to the model in (a). With <em>K </em>alternatives, at most <em>K </em>−1 alternative specific constants can be estimated. The coefficient of <em>K </em>−1 constants are interpreted as relative to <em>K</em>th alternative. Normalize the constant for the alternative hp to 0.

  <ol>

   <li>How well do the estimated probabilities match the shares of customers choosing each alternative in this case?</li>

   <li>Calculate the <em>wtp </em>that is implied by the estimate. Is this reasonable?</li>

  </ol></li>

</ul>

<ul>

 <li>Suppose you had included constants for alternatives ec, er, gc, hp with the constant for alternative gr normalized to zero. What would be the estimated coeffiient of the constant for alternative gc? Can you figure this out logically rather than actually estimating the model?</li>

</ul>

<ul>

 <li>Now try some models with sociodemographic variables entering.

  <ol>

   <li>Enter installation cost divided by income, instead of installation cost. With this specification, the magnitude of the installation cost coefficient is inversely related to income, such that high-income households are less concerned with installation costs than lower-income households. Does dividing installation cost by income seem to make the model better or worse than the model in (c)?</li>

   <li>Instead of dividing installation cost by income, enter alternative-specific income effects. You can do this by using the | argument in the mlogit What do the estimates imply about the impact of income on the choice of central systems versus room system? Do these income terms enter significantly?</li>

  </ol></li>

 <li>We now are going to consider the use of the logit model for prediction. Estimate a model with installation costs, operating costs, and alternative specific constants. Calculate the probabilities for each house explicitly.

  <ol>

   <li>The California Energy Commission (CEC) is considering whether to offer rebates on heat pumps. The CEC wants to predict the effect of the rebates on the heating system choices of customers in California. The rebates will be set at 10% of the installation cost. Using the estimated coeffiients from the model, calculate predicted shares under this new installation cost instead of original value. How much do the rebates raise the share of houses with heat pumps?</li>

   <li>Suppose a new technology is developed that provides more efficient central heating. The new technology costs $200 more than the electric central heating system. However it saves 25% of the electricity such that its operating costs are 75% of the operating costs of ec. We want to predict the original market penetration of this technology. Note that there are now 6 alternatives instead of 5. Calculate the probability and predict the market share (average probability) for all 6 alternatives using the model that is estimated on the 5 alternatives. Use the original installation costs for the heat pumps rather than the reduced costs from the previous question. What is the predicted market share for the new technology? From which of the original five systems does the new technology draw the most customers?</li>

  </ol></li>

</ul>

<ol start="2">

 <li>A sample of residential electricity customers were asked a series of choice experiments. The data is provided in the file csv. In each experiment, four hypothetical electricity suppliers were described. The person was asked which of the four suppliers he/she would choose. As many as 12 experiments were presented to each person. Some people stopped before answering all 12. There are 361 people in the sample, and a total of 4308 experiments.</li>

</ol>

In the experiments, the characteristics of each supplier were stated.

<ul>

 <li>The price of the supplier was either one of these options:

  <ul>

   <li>a fixed price at a stated cents per kWh, with the price varying over suppliers and experiments (pf1, pf2, pf3, pf4)</li>

   <li>a time-of-day (tod) rate under which the price is 11 cents per kWh from 8am to 8pm and 5 cents per kWh from 8pm to 8am. These tod prices did not vary over suppliers or experiments: whenever the supplier was said to offer tod, the prices were stated as above (tod1, tod2, tod3, tod4)</li>

   <li>a seasonal rate under which the price is 10 cents per kWh in the summer, 8 cents per kWh in the winter, and 6 cents per kWh in the spring and fall. Like tod rates, these prices did not vary. Note that the price is for the electricity only, not transmission and distribution, which is supplied by the local regulated utility (seas1, seas2, seas3, seas4).</li>

  </ul></li>

 <li>The length of contract that the supplier offered was also stated, in years (such as 1 year or 5 years.) During this contract period, the supplier guaranteed the prices and the buyer would have to pay a penalty if he/she switched to another supplier. The supplier could offer no contract in which case either side could stop the agreement at any time. This is recorded as a contract length of 0 (cl1, cl2, cl3, cl4).</li>

 <li>Some suppliers were also described as being a local company or a “well-known” company. If the supplier was not local or well-known, then nothing was said about them in this regard (loc1, loc2, loc3, loc4, wk1, wk2, wk3, wk4).</li>

</ul>

The actual choices made are captured in choice with id capturing the customer identity.

<ul>

 <li>Run a mixed logit model without intercepts and a normal distribution for the 6 parameters of the model and taking into account the panel data structure.

  <ol>

   <li>Using the estimated mean coefficients, determine the amount that a customer with average coefficients for price and length is willing to pay for an extra year of contract length.</li>

   <li>Determine the share of the population who are estimated to dislike long term contracts (i.e. have a negative coefficient for the length.)</li>

  </ol></li>

 <li>The price coefficient is assumed to be normally distributed in these runs. This assumption means that some people are assumed to have positive price coefficients, since the normal distribution has support on both sides of zero. Using your estimates from before, determine the share of customers with positive price coefficients (Hint: Use the pnorm function to calculate this share). As you can see, this is pretty small share and can probably be ignored. However, in some situations, a normal distribution for the price coefficient will give a fairly large share with the wrong sign. Revise the model to make the price coefficient fixed rather than random. A fixed price coefficient also makes it easier to calculate the distribution of willingness to pay (<em>wtp</em>) for each non-price attribute. If the price coefficients fixed, the distribution of <em>wtp </em>for an attribute has the same distribution as the attribute’s coefficient, simply scaled by the price coefficient. However, when the price coefficient is random, the distribution of <em>wtp </em>is the ratio of two distributions, which is harder to work with. What is the estimated value of the price coefficient. Compare the log likelihood of the new model with the old model.</li>

 <li>You think that everyone must like using a known company rather than an unknown one, and yet the normal distribution implies that some people dislike using a known company. Revise the model to give the coefficient of wk a uniform distribution (do this with the price coefficient fixed). What is the estimated distribution for the coefficient of wk and the estimated price coefficient?</li>

</ul>

<ol start="3">

 <li>Suppose we perform best subset, forward stepwise, and backward stepwise selection on a single data set. For each approach, we obtain <em>p</em>+1 models, containing 0<em>,</em>1<em>,…,p </em> Provide your answers for the following questions:

  <ul>

   <li>Which of the three models with <em>k </em>predictors has the smallest training sum of squared errors?</li>

   <li>Which of the three models with <em>k </em>predictors has the smallest test sum of squared errors? (c) Are the following statements <strong>True </strong>or <strong>False</strong>:

    <ol>

     <li>The predictors in the <em>k</em>-variable model identified by forward stepwise selection are a subset of the predictors in the (<em>k </em>+ 1)-variable model identified by forward stepwise selection.</li>

     <li>The predictors in the <em>k</em>-variable model identified by backward stepwise selection are a subset of the predictors in the (<em>k</em>+1)-variable model identified by backward stepwise selection.</li>

    </ol></li>

  </ul></li>

</ol>

<ul>

 <li>The predictors in the <em>k</em>-variable model identified by backward stepwise selection are a subset of the predictors in the (<em>k</em>+1)-variable model identified by forward stepwise selection.</li>

</ul>

<ol>

 <li>The predictors in the <em>k</em>-variable model identified by forward stepwise selection are a subset of the predictors in the (<em>k</em>+1)-variable model identified by backward stepwise selection.</li>

 <li>The predictors in the <em>k</em>-variable model identified by best stepwise selection are a subset of the predictors in the (<em>k </em>+ 1)-variable model identified by best stepwise selection.</li>

</ol>

<ol start="4">

 <li>In this question, we will use the data in csv to investigate how well we can predict the number of applications received for universities and colleges in the US. The dataset has the following fields:

  <ul>

   <li>Private: Private/public indicator</li>

   <li>Apps: Number of applications received</li>

   <li>Accept: Number of applicants accepted</li>

   <li>Enroll: Number of new students enrolled</li>

   <li>Top10perc: New students from top 10</li>

   <li>Top25perc: New students from top 25</li>

   <li>Undergrad: Number of full-time undergraduate students</li>

   <li>Undergrad: Number of part-time undergraduate students</li>

   <li>Outstate: Out of state tuition</li>

   <li>Board: Room and board costs</li>

   <li>Books: Estimated book costs</li>

   <li>Personal: Estimated personal spending</li>

   <li>PhD: Percent of faculty with PhDs</li>

   <li>Terminal: Percent of faculty with a terminal degree</li>

   <li>F.Ratio: Student/faculty ratio</li>

   <li>alumni: Percent of alumni who donate</li>

   <li>Expend: Instructional expenditure per student</li>

   <li>Rate: Graduation rate</li>

  </ul></li>

</ol>

<ul>

 <li>Split the data set into a training set and a test set using the seed 1 and the sample() function with 80% in the training set and 20% in the test set. How many observations are there in the training and test sets?</li>

 <li>Fit a linear model using least squares on the training set. What is the average sum of squared error of the model on the training set? Report on the average sum of squared error on the test set obtained from the model.</li>

 <li>Use the backward stepwise selection method to select the variables for the regression model on the training set. Which is the first variable dropped from the set?</li>

 <li>Plot the adjusted-<em>R</em><sup>2 </sup>for all these models. If we choose the model based on the best adjusted-<em>R</em><sup>2 </sup>value, which variables should be included in the model?</li>

 <li>Use the model identified in part (d) to estimate the average sum of squared test error.</li>

</ul>

Does this improve on the model in part (b) in the prediction accuracy?

<ul>

 <li>Fit a LASSO model on the training set. Use the command to define the grid for <em>λ</em>:</li>

</ul>

grid&lt;- 10^seq(10,-2, length=100).

Plot the behavior of the coefficients as <em>λ </em>changes.

<ul>

 <li>Set the seed to 1 before running the cross-validation with LASSO to choose the best <em>λ</em>. Use 10-fold cross validation. Report the test error obtained, along with the number of non-zero coefficient estimates.</li>

</ul>