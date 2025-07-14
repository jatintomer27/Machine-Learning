# SVR

- The key idea is to find a function that maps the input variables x to an output y, in a way that errors are within a certain margin.

- The key difference with traditional regression methods (like linear regression) is that we introduce a margin of tolerance, ε, around the true target values yi and the model should only penalize errors that exceed this margin.

#### The Regression Function (Hypothesis)

![Regression Function](regression_function.png)

#### Epsilon-Insensitive Loss Function

- In standard regression, the loss function might be something like Mean Squared Error (MSE), where every error contributes to the cost.

- In SVR, we introduce a margin (tolerance) ε, which allows for small deviations without penalizing them.

- The idea is that if the predicted value is within the margin ε of the actual value, there is no penalty.

- The epsilon-insensitive loss function for a single data point is:

![Epsilon-Insensitive Loss](epsilon_loss.png)

- Now, we want to minimize the total loss for all the training points.

![Epsilon-Insensitive Total Loss](epsilon_total_loss.png)

#### Regularization (Model Complexity)

- SVR aims to find the simplest function f(x) = w^T(x) + b (a linear function) that fits the data well. 

- This means we want to avoid very large weights w because large weights can lead to overfitting.

- To achieve this, we add a regularization term that penalizes large weights. 

- The regularization term is typically 1/2(||w||)^2, which is a measure of the magnitude of the weights.

- The smaller the magnitude of w, the simpler the model.

- Now we have two components in the objective:

![Components of Objective](components_of_objective.png)

#### Introducing Slack Variables

- One more thing: because we allow some error beyond the margin ε, we need to measure the amount of error for each data point.

- To do this, we introduce slack variables ξi and ξi∗

![Slack Variable](slack_variables.png)

- Now, we can rewrite the loss function for each data point using the slack variables

- If the error exceeds ε, it will be captured by the slack variables ξi and ξi∗
​
- Thus, the loss function becomes

![Loss function with Slack variable](loss_function_with_slack.png)

#### Final Objective Function

- Now combine the regularization term with the total loss function

- The final objective function we aim to minimize is:

![Objective function](objective_function.png)

###### Constraints on Slack Variables

- To make sure the slack variables are properly defined, we add the following constraints to the optimization problem.

![Slack Variable Constrains](slack_variables_constrains.png)

**Q: Why Two Different Forms in the Constraints although the loss is y_true - y_pred ?** 

- The key idea is that constraints are directional, while loss is symmetric.

- We break the absolute error into two separate inequality constraints to handle both overprediction and underprediction separately.

![Forms of Constrains](forms_of_constrains.png)

###### Final Optimization Problem

![Optimization Problem](optimization_problem.png)

#### Form the Lagrangian (KKT Conditions)

- To derive the dual, we build the Lagrangian function using Lagrange multipliers.

![Langrangian Multiplier](Langrangian_multiplier.png)

![KTT Stationarity](ktt_stationarity.png)

#### Dual Formulation

- Expand all sums of Langrangian equation and group similar terms.

![Expanded Langrangian Equation](expanded_langrangian_equation_1.png)

-  Collect All Terms, Let’s rewrite L grouped by variables

![Collect Langrangian Equation](collect_langrangian_equation.png)

- Final Expression for the Dual Lagrangian

![Final Dual Langrangian](dual_langrangian_final_equation.png)

- Substitute Optimal w value in Dual Formulation

![Substitute Optimal w](substitue_optimal_w.png)

- Now we solve the Dual Optimization Problem and find the value of αi and (αi)^*, which are related to the margins and error constraints.

- We find the αi and (αi)^* for every record

- However only some αi ,αi∗ will be non-zero

- Most of the time:

*For points inside the ε-tube, we get αi = αi∗ = 0*

*Only for points lying outside the tube (support vectors), one of the two will be non-zero*

- So in practice, only a subset of training points affect the final model — these are the support vectors


#### Final Prediction

- Once the optimization problem is solved, the final function f(x) (our regression model) is:

![Final Predection](final_predection.png)

![Linear Model Predection](linear_model_predection_formula.png)

![Non Linear Predection](non_linear_predection_formula.png)
​
##### Weight and Bias formula

![Weight and bias formula](w_and_b_formula.png)




