# About task:
The goal of this subtask is to develop your own
model and use it to learn the sine function on the interval $[0, 2π]$. Discretize the interval with a suitable number of points (of your choice) and use the values of the sine function at these discretization points as labels.
Implement a Quantum Machine Learning model which reproduces the values of the sine function.

***Solution:*** A regression model using QML will be designed and implemented.

***Approach:***
- **Data Generation:** First, 100 data points will be generated from the sine function, $y=sin(x),x∈[0,2π]$. From there, 30% of the data will be randomly chosen for testing, and the model will be trained using 70% of the generated data.

- **QML Model:** The data will be encoded using angle embedding.
    - First, a 1 layer of rotation gates will be chosen as the ansatze. The model will be trained using only the training data. The qubit will be measured to get the expectation value as prediction for testing data.
    - 4 layers of rotation gates will be chosen as the ansatze, and the same operation will be performed.

- **Cost function and Optimization:** A cost function will be implemented to estimate the cost of the QML model. A Gradient Descent Optimizer will be used to optimize/minimize the cost.
- **Result & Discussion:** The training and prediction data will be plotted, and the two models will be compared. The mae, mse, and rmse scores between the two models will also be compared.