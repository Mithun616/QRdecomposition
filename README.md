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

Initialize matrices Q and u with the same size as A.

Set the first column of u to the first column of A.

Normalize the first column of u to get the first column of Q.

Loop through each column i from one to n minus one.

Set the ith column of u to the ith column of A.

Loop through each column j from zero to i minus one.

Subtract the projection of A column i on Q column j from u column i.

Normalize u column i to get Q column i.

Initialize a matrix R with zeros, having the same shape as A.

Calculate the upper triangular matrix R using the dot product of A and Q.

## Program:
### Gram-Schmidt Method
```
import numpy as np
def QR_Decomposition(A): 
    n,m=A.shape
    Q=np.empty((n,n))
    u=np.empty((n,n))
    u[:,0]=A[:,0]
    Q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    for i in range(1,n):
        u[:,i]=A[:,i]
        for j in range(i):
            u[:,i]-=(A[:,i]@Q[:,j])*Q[:,j]
            Q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    R=np.zeros((n,m))
    for i in range(n):
        for j in range(i,m):
            R[i,j]=A[:,j]@Q[:,i]
    print(Q)
    print(R)
a=np.array(eval(input()))
QR_Decomposition(a)

```

## Output

![Screenshot 2024-12-04 222500](https://github.com/user-attachments/assets/e8b3c8d0-e4e5-4a7f-b4f2-7886fd9722d1)


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
