# XGBoosting 

- XGBoost stands for eXtreme Gradient Boosting.

- It used for supervised learning tasks that builds an ensemble of decision trees sequentially to make powerful predictions.

- XGBoost works in the same way as Gradient Boosting but with some advancement.

- XGBoost tries to minimize a total objective function.

![XGBoost Objective function](xgboost_objective_function.png)

- Now, suppose you start with a guess

![XGBoost Training](xgboost_training.png)

- Now using Gradients to solve

![XGBoot Training Graidents](xgboost_training_taylor.png)

- Now this is our object and we have to build the tree to minimize this objective loss.

- But solving this directly is hard, so we use a second-order Taylor expansion of the loss.

![Taylor Expansion](taylor_expansion_intution.png)

- We now construct the tree f(t) to minimize the objective function.

### 1/n and 1/2 in loss function

![Loss Calculation](1n_and_12_difference.png)

### Loss function difference

![Loss function difference](loss_fun_difference.png)

### How to constuct the tree in XGBoost 

- Step 1: Compute Gradients and Hessians

![Gradient and Hessian](gradient_and_hessian.png)

- Step 2: Start with One Root Node

![Score/Weight at root node ](score_at_root.png)

- Step 3: Try Splits on All Features

![Split on all features](split_on_all_features.png)

- Step 4: Recursively Split

![Recursive Split](recursive_split.png)

- Step 5: Compute Leaf Weights

![Compute Leaf Weights](leaf_weight_in_xgboost.png)

- Step 6: Update Predictions

![Update Predections](update_predection_in_xgboost.png)