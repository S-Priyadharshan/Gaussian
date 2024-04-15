# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm:

### STEP 1:
Convert the matrix into upper triangular form using Gaussian elimination.

### STEP 2:
Back substitute to find the solution.

### STEP 3:
Iterate over each row to make the elements below the diagonal zero.

### STEP 4:
Return the solution vector.

## Program:
```
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: Priyadharshan S
RegisterNumber: 212223240127
'''
import numpy as np
n=int(input())
matrix=np.zeros((n,n+1))#A matrix of zeroes
x=np.zeros(n)

"""
getting inputs
"""
for i in range(n):
    for j in range(n+1):
        matrix[i][j]=int(input())

"""
Applying Row echelon conditions 
"""
for i in range(n):#Initial loop | runs thrice (0,1,2)
    for j in range(i+1,n):#Loop that runs 1 ahead column wise | runs twice (1,2)
        ratio=matrix[j][i]/matrix[i][i] #runs diagonally across the major diagonal elements
        for k in range(n+1):#Loop that runs parallel across the rows | runs four times (0,1,2,3)
            matrix[j][k]=matrix[j][k]-ratio*matrix[i][k]
            
"""
Substitution of values eg: 4z=6
"""
x[n-1]=matrix[n-1][n]/matrix[n-1][n-1]

"""
Equation evaluation but occurs in reverse
"""
for i in range(n-2,-1,-1):
    x[i]=matrix[i][n]
    for j in range(i+1,n):
        x[i]=x[i]-matrix[i][j]*x[j]
    x[i]=x[i]/matrix[i][i]
    
    
for i in range(n):
    print("X%d = %0.2f"%(i,x[i]),end=" ")
        
```

## Output:

![image](https://github.com/S-Priyadharshan/Gaussian/assets/145854138/35bbe348-c6c3-4aa1-b98c-1fa2520d8306)


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

