##Solve ODEs using Runge-Kutta of order 2
```python
from __future__ import division
import numpy as np
import matplotlib.pyplot as plt

plt.ion()
def solveRH2(fSpec,x0,h,tmax):
       f = eval("lambda x,t:" + fSpec)
       t,x = 0.0,x0
       xk = [x0]
       tk = [0.0]
       while t < tmax - h/2 :
        k1 = h*f(x, t)
        k2 = h*f(x + 0.5*k1,t + (0.5)*h)
        x += k2
        t += h
        tk.append(t)
        xk.append(x)
       plt.plot(tk,xk,'r.',markersize=4)
       plt.xlim(0.0,tmax*1.05)
       plt.show()
       print "Number of steps  = ",len(tk)-1
       print "Final value of t = ",tk[-1]
       print "Final value of x = ",xk[-1]
       print"err_rk=", abs(np.e-xk[-1])
       print"relative err_rk=", abs((np.e-xk[-1]/np.e)*0.01)

print "\n Enter ODE to solve by typing solveODE(fSpec,x0,dt,tmax)\n\
 where fSpec is a string giving the function of x and t"
```
```python
def solveRH222(fSpec,x0,h,tmax):
       f = eval("lambda x,t:" + fSpec)
       t,x = 0.0,x0
       xk = [x0]
       tk = [0.0]
       while t < tmax - h/2 :
        k1 = h*f(x, t)
        k2 = h*f(x + 0.5*k1,t + (0.5)*h)
        x += k2
        t += h
        tk.append(t)
        xk.append(x)
        E11=abs(np.exp(1)-xk[-1])
        ER11= abs(E11/xk[-1])
        return ER11
   ```
