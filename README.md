# BikeSharingAssignment
The bike sharing assignment from upgrad is related to the linear regression.
Essentially, the BoomBikes company wants us to try and predict post pandemic, what drives the business or what factors we need to consider, to predict the future bike rentals.
We have been provided to months, holidays, workingdays, weather situations, humidity, windspeed, temperature and others to make this prediction.

Objective:
* To identify the variables affecting count target variable, e.g. months, holidays, workingdays, weather situations, humidity, etc.

* To create a linear model that quantitatively relates house prices with variables mentioned above.

* To know the accuracy of the model, i.e. how well these variables can predict the count in the test dataset.


The steps we have gine through to make the prediction:
* Step 1: Reading and Understanding the Data
* Step 2: Visualising the Data
* Step 3: Data Preparation: which also involves outliar reduction, the scaling if needed, linear encoding and dummy variable creation.
* Step 4: Splitting the Data into Training and Testing Sets.
* Step 5: Building a linear model: Employ RFE/Backward selection and other ways.
* Step 6: Employing RFE, Updation of the model, addition/deletion of the variables based on p-value and VIF, generate multiple models and compare based on adj. R2.
* Step 7: Residual Analysis of the train data. Check the distribution of the error, it should be normal.
* Step 8: Making Predictions Using the Final Model

The model is selected based on adjusted R^2 and validating the assumptions of linear regression along the way, visualising the predicted vs the test target variable are the end goals.

The adj. R2 of the predicted and the model should be pretty close to each other.
