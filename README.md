# SGD-Regressor-for-Multivariate-Linear-Regression

## AIM:
To write a program to predict the price of the house and number of occupants in the house with SGD regressor.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start
2. Data preparation
3. Hypothesis Definition
4. Cost Function
5. Parameter Update Rule
6. Iterative Training
7. Model evaluation
8. End
 

## Program:

Program to implement the multivariate linear regression model for predicting the price of the house and number of occupants in the house with SGD regressor.
```
import numpy as np
from sklearn.datasets import fetch_california_housing
from sklearn.linear_model import SGDRegressor
from sklearn.multioutput import MultiOutputRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.preprocessing import StandardScaler

data = fetch_california_housing()
x= data.data[:,:3]

y=np.column_stack((data.target,data.data[:,6]))

x_train, x_test, y_train,y_test = train_test_split(x,y, test_size = 0.2, random_state =42)

scaler_x = StandardScaler()
scaler_y = StandardScaler()
x_train = scaler_x.fit_transform(x_train)
x_test = scaler_x.fit_transform(x_test)
y_train = scaler_y.fit_transform(y_train)
y_test = scaler_y.fit_transform(y_test)
sgd = SGDRegressor(max_iter=1000, tol = 1e-3)
multi_output_sgd= MultiOutputRegressor(sgd)
multi_output_sgd.fit(x_train, y_train)
y_pred =multi_output_sgd.predict(x_test)
y_pred = scaler_y.inverse_transform(y_pred)
y_test = scaler_y.inverse_transform(y_test)
print(y_pred)


mse = mean_squared_error(y_test,y_pred)

print("Mean Squared Error:",mse)

print("\nPredictions:\n",y_pred[:5])
```
Developed by: GURUPARAN G

RegisterNumber:  212224220030


## Output:
![image](https://github.com/user-attachments/assets/7c0250a3-ef71-4647-819d-fc87c4396b41)

![image](https://github.com/user-attachments/assets/c76254a7-3a3c-438b-803b-7991cbecb119)

![image](https://github.com/user-attachments/assets/ae7e32f6-4b18-43f7-8180-ed87ce42beeb)


## Result:
Thus the program to implement the multivariate linear regression model for predicting the price of the house and number of occupants in the house with SGD regressor is written and verified using python programming.
