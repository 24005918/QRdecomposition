# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:

## Gram-Schmidt Method
```
Program to QR decomposition using the Gram-Schmidt method
Developed by: SANTHOSH V
RegisterNumber: 212224230252
'''
import numpy as np

def QR_Decomposition(A):
    n, m = A.shape
    Q = np.empty((n, m))
    u = np.empty((n, m))

    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0] / np.linalg.norm(u[:, 0])

    for i in range(1, m):
        u[:, i] = A[:, i]
        for j in range(i):
            proj = np.dot(A[:, i], Q[:, j]) * Q[:, j]
            u[:, i] -= proj
        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i])

    R = np.zeros((m, m))
    for i in range(m):
        for j in range(i, m):
            R[i, j] = np.dot(Q[:, i], A[:, j])

    print(f"The Q Matrix is \n {Q}")
    print(f"The R Matrix is \n {R}")

a = np.array(eval(input()))
QR_Decomposition(a)







# Output

![{A110FC96-3A78-441C-8AE1-A2DF0DF1F054}](https://github.com/user-attachments/assets/7c297225-c064-44f7-b1fd-45e1f67b3bc6)






## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
