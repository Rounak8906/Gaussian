# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Read the number of unknowns n and the augmented matrix entries from user input.
2. Reshape the input into an n\times (n+1) augmented matrix A.
3. For each pivot row i, eliminate entries below the pivot by subtracting a factor times the pivot row.
4. Initialize solution vector x with zeros.
5. Perform back substitution: compute each variable from the last row upwards using the formula in the code.
6. Print the solution values of all variables in formatted output.

## Program:
```
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: ROUNAK SINGH
RegisterNumber: 212225240125
'''
import os 
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
import sys
n = int(input())
a = np.zeros((n,n+1))
x = np.zeros(n)
for i in range(n):
    for j in range(n+1):
        a[i][j]= float(input())

for i in range(n):
    if a[i][i] == 0.0:
        sys.exit('Divide by zero detected')
        
    for j in range(i+1,n):
        ratio = a[j][i]/a[i][i]
    
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio * a[i][k]
        
x[n-1] = a[n-1][n]/a[n-1][n-1]

for i in range(n-2,-1,-1):
    x[i] = a[i][n]
    
    for j in range(i+1,n):
        x[i] = x[i]-a[i][j]* x[j]
        
    x[i]= x[i]/a[i][i]
    
    
for i in range(n):
    print('X%d = %0.2f' %(i,x[i]),end = ' ')
```

## Output:
<img width="912" height="445" alt="image" src="https://github.com/user-attachments/assets/ea9e45e8-8f33-491c-9ac0-1150c8594fb5" />



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

