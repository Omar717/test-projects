# test-projects
import time
import math as mt
#define initial conditions for spring-mass damper system
x0 = 1.0
t0 = 0.0
m = 1.0
c = 1.0
k = 39.4784
p = 0.0
h = 0.1
V0 = 0.0

start=time.time()

#begin loop using basic euler method
while x0>0.01 or x0<-0.01:
     t = t0 + h
     x = x0 + h*V0
     V = V0 + h*(-V0-k*x0)
     t0 = t
     x0 = x
     V0 = V
print(t,x,V)

x0 = 1.0
t0 = 0.0
V0 = 0.0
#Basic euler provides poor accuracy, now we will try symplectic euler
while x0>0.001 or x0<-0.001:
      t1 = t0 + h
      x1 = x0 + h*V0
      V1 = V0 + h*(-V0-k*x1)
      t0 = t1
      x0 = x1
      V0 = V1
print(t1,x1,V1)

end=time.time()

print('time elapsed is: ',end - start)
