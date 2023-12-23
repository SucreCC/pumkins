## Kai Deng 123103576


## (a) Show that the model can be rewritten as 


\begin{equation}
C\frac{dT}{dt}=
Q\left(\frac{1}{2}+\frac{1}{5}\tanh(\frac{T-265}{10})\right) - \left(A + BT \right)
\tag{1}
\end{equation}


To rewritten, we need set 

\begin{equation}
x=\frac{T-265}{10}
\tag{2}
\end{equation}

Then we got

\begin{equation}
\frac{dT}{dt}=10\frac{dx}{dt}
\tag{3}
\end{equation}

After combine (1) , (2) and (3)

\begin{equation}
10C\frac{dx}{dt}=
Q\left(\frac{1}{2}+\frac{1}{5}\tanh(x)-\left(A+B\left(10x+256\right)\right)\right)
\end{equation}

\begin{equation}
\frac{50C}{Q}\frac{dx}{dt}=
\tanh(x) - 5\left(A-\frac{1}{2}+B\left(10x+256\right) \right)
\end{equation}

\begin{equation}
\frac{dx}{\frac{Qdt}{50C}}=
\tanh(x) - 5\left(A-\frac{1}{2}+256B\right) - 50Bx
\end{equation}

Set
\begin{equation}
d\tau =\frac{Qdt}{50C} 
\end{equation}

\begin{equation}
a = 5\left(A-\frac{1}{2}+256B\right)
\end{equation}

\begin{equation}
b=50B
\end{equation}

Finally, we got

\begin{equation}
\frac{dx}{d\tau} =
\tanh(x)-a-bx
\end{equation}


## (b) Assuming b < 1 is constant, discuss the dynamics of model (2) qualitatively for different parameters of $\alpha$ using phase portraits. What bifuracation(s) take place?


### 1. when 0<b<1, Saddle-Node Bifurcation take place

\begin{equation}
\frac{dx}{d\tau} =
\tanh(x)-a-bx=0
\end{equation}

\begin{equation}
\tanh(x)-a-bx=0
\end{equation}

\begin{equation}
\tanh(x)= bx+a
\end{equation}

set $y_1$ = tanh(x) and $y_2$ = bx + a then the intersection point of $y_1$ and $y_2$ is fixed point
draw them in Desmos, the red line is "tanhx" and the blue line is "bx+a"



![image-3.png](../../../../../Downloads/Assignment6005/image-3.png) 
         
<!-- \begin{equation}
\frac{dx}{d\tau} =
(1-b)x - \frac{x^3}{3} + \frac{2x^5}{15}  -a
\end{equation} -->

move a from negative infinite to positive infinite
1. First we have one stable fixed point on the right half-axis of x, and it moves to the right bifurcation point
2. Second when $y_1$ and $y_2$ tangent in the third quadrant at this time we got a half-stable fixed point
3. With the continuous move we got 3 fixed point, the right one and left one are stable points and move toward negative infinite, the middle one is an unstable point and the middle one is an unstable point it move toward the right fixed point.
4. Then the middle fixed point and the right fixed point collide at the right bifurcation and disappear.
5. Finally left fixed point continuously moves toward the negative infinite.

![image-11.png](../../../../../Downloads/Assignment6005/image-11.png)
<!-- ![image-8.png](attachment:image-8.png) -->

![image-3.png](../../../../../Downloads/Assignment6005/image-3.png) 
<!-- ![image-4.png](attachment:image-4.png) -->
![image-5.png](../../../../../Downloads/Assignment6005/image-5.png)
<!-- ![image-6.png](attachment:image-6.png) -->
![image-7.png](../../../../../Downloads/Assignment6005/image-7.png)

### 2. When b =0 or b < 0, no bifurcation
just zero or one fixed potion, so when b = 0 or b < 0 no bifurcation
![image-9.png](../../../../../Downloads/Assignment6005/image-9.png)
![image-10.png](../../../../../Downloads/Assignment6005/image-10.png)


## (c) Determine the bifurcation points a<sub>c</sub> as a function of b.
\begin{equation}
 y_1 = tanh(x)
\end{equation}

\begin{equation}
 y_2 = bx + a
\end{equation}

As the below picture shows, the bifurcation points is that the point when $y_1$ and $y_2$ are tangent.

\begin{equation}
 y_1 = y_2 
\end{equation}

\begin{equation}
 \frac{dy_1}{dx} = \frac{dy_2}{dx}
\end{equation}

Then we got
\begin{equation}
  tanh(x) = bx + a
  \tag{4}
\end{equation}

\begin{equation}
  \frac{d(tanh(x))}{dx}=\frac{d(bx+a)}{dx}
\end{equation}

Because
\begin{equation}
\frac{d(tanh(x))}{dx} = sech^2(x)
\end{equation}

Then 
\begin{equation}
b=sech^2(x)
\tag{5}
\end{equation}

Also because only when 0< b <1 we can have bifurcation point, so replace x by b



\begin{equation}
x = \frac{1}{sech(b)}
\tag{6}
\end{equation}


Square both sides of the equation 4

\begin{equation}
  tanh^2(x) = (bx + a)^2
  \tag{7}
\end{equation}

\begin{equation}
  tanh^2(x) + sech^2 = 1
  \tag{8}
\end{equation}

\begin{equation}
0 < b < 1
\tag{9}
\end{equation}

Combine 5, 6, 7, 8, 9 we got

\begin{equation}
1 - sech^2(x) = (\frac{b}{sech(b)}+a)^2
\end{equation}

Because 0 < b < 1 then 1 - b > 0 

\begin{equation}
1 - b = (\frac{b}{sech(b)}+a)^2
\end{equation}

\begin{equation}
\pm\sqrt{1-b}=\frac{b}{sech(b)}+a
\end{equation}

Finally we got 2 bifurcation point $a_c$ when 0< b < 1
\begin{equation}
a_c = \pm\sqrt{1-b}- \frac{b}{sech(b)}
\end{equation}


![image.png](../../../../../Downloads/Assignment6005/image.png)




# (d) Sketch the bifurcation diagram.

Conbine the equation 5, 7, 8, we got below

\begin{equation}
a = tanh(x) - x*sech^2(x)
\end{equation}

Using python to get every a for x near the bifurcation point, and draw a rough graph of a and x


```python
import math
import numpy as np
import matplotlib.pyplot as plt

def get_result(x):
    return math.tanh(x) - x * (1- math.tanh(x) * math.tanh(x))

x_values = np.linspace(-5,5,20)
a_values = list()

for x in x_values:
    a_values.append(get_result(x))
plt.plot(a_values,x_values)
plt.xlabel("a")
plt.ylabel("x")
plt.show()
```


    
![png](../../../../../Downloads/Assignment6005/output_5_0.png)
    


As the rough graph shows, the finally bifurcation diagram show like below
![image.png](../../../../../Downloads/Assignment6005/image.png)
