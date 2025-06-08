# Komputasi Numerik Final Project (Team IUP05)
Adelia Tanalina Yumna - 5025241078


### 1. Imports and setup
```c
import numpy as np
import math
```

```c
h = 3
n = 4
xi_values = np.arange(2, 12, h)

for i in range(0, n):
    print("x" + str(i) + ": " + str(xi_values[i]))

# print(x_values)
```


### 2. Exact (“real”) solution
```c
# real y values (using the normal integral method):
def real_f(x):
  return np.round((4*(x**5)/5) - (4*(x**3)), 2)

f_real = real_f(xi_values)

for i in range(0, n):
    print("Real f(" + str(i) + "): " + str(f_real[i]))

# print(y_real)
```

### 3. Derivative values at each x
```c
# f(x, y) values
def y(x):
  return np.round((4*(x**4))-(12*(x**2)), 2)

yi_values = y(xi_values)

for i in range(0, n):
    print("y" + str(i) + ": " + str(yi_values[i]))
```

### 4. Euler’s method approximation
```c
# euler method
euler_y = np.zeros(4)

# initialize y0 to the real value of y0
euler_y[0] = f_real[0]

for i in range(0, n-1):
  euler_y[i+1] = euler_y[i] + (h*yi_values[i])

for i in range(0, n):
  print("euler y" + str(i) + ": " + str(euler_y[i]))
```

### 5. Error calculation
```c
# errors = (abs(euler_y-f_real))/f_real*100

def error(i):
  return abs(((euler_y[i]-f_real[i]))/f_real[i]*100)
# errors = np.where(np.abs(f_real) > 1e-8,
#                   np.abs(euler_y - f_real) / np.abs(f_real) * 100,
#                   0)

errors = [round(error(i), 2) for i in range(n)]
errors[0] = "-"
```
### 6. Final output
```c
print("Initial conditions:")
print("h = 3")
print("n = 4")
print("x0 = 2 to x3=11\n")
print("if f'(x) = 4x^4 - 12x^2, find the values of f(x) using the Euler method")

print("\n")

print("Results:")
print("i  x  Euler y  Exact y  Error")
print("------------------------------------------------------")

for i in range(0, n):
  print(f"{i}  {xi_values[i]}  {euler_y[i]}      {f_real[i]}     {errors[i]}")
```
