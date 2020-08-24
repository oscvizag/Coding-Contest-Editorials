## Question
![Question](https://github.com/kiransaiabhishek/Coding-Contest-Editorials/blob/master/cOdeSpeC/Circle%20around%20my%20head/Circle%20around%20my%20head.png)

As our friend  Hipparchus said triangle n theta is the key to everything!Just kidding but u need to know the concept of trigonometry to solve this problem.
Consider one of the outer circle and an inner circle join lines as shown in the pic

## Diagram
![Diagram](https://github.com/kiransaiabhishek/Coding-Contest-Editorials/blob/master/cOdeSpeC/Circle%20around%20my%20head/ans.png)

where R is outer circle radius and r is inner circle radius

 θ =sin 
−1(R/R+r) - eq 1
N=2pi/2 θ 

 θ  = pi/ n- eq 2

substitute equation 1 in equation 2

then u get 
N=π/sin 
−1(R/R+r)

Assume that k=R/r,

N=π/sin^-1(k/k+1)

k/k+1=sin(pi/N)

k[1-sin(π/N)]=sin(π/N)

k=sin(π/N)/[1-sin(π/N)]

R/r=sin(π/N)/[1-sin(π/N)]

R=r*(sin(π/N)/[1-sin(π/N)])

# Solution
```
import math
a=list(map(int,input().split()))
n=a[0]
r=a[1]
ans=r*(math.sin(3.141592653589793/n)/(1-math.sin(3.141592653589793/n)))
print('%.4f'%ans)
