---
title: Test python file
date: 2023/12/23 20:45:48
update: 2023/12/23
categories:
 - [计算机科学, 二进制杂谈, Theme Shoka Documentation]
tags:
 - Hexo
 - 教程
sticky: true
valine:
  placeholder: "1. 提问前请先仔细阅读本文档⚡\n2. 页面显示问题💥，请提供控制台截图📸或者您的测试网址\n3. 其他任何报错💣，请提供详细描述和截图📸，祝食用愉快💪"
---

# Name: Kai Deng

Student number: 123103576

# (a) Classify the fixed point at the origin in dependence on $\nu$ and $\mu$. Indicate the different possibilities in diagram in the ( $\nu,\mu$ )-plane. Hint: You may neglect border-line cases.
$$
\frac{dx}{dt} = 2x(1-\frac{x}{2}) - y(x + \mu)
$$
\begin{equation}
\frac{dy}{dt}= y(\mu - y^2) -x(xy-\mu)
\end{equation}

As the question mentioned the fixed point is (x=0,y=0), so we can construct jacobian matrix as below.

$$x=0 \tag{1}$$
$$y=0 \tag{2}$$

$$
J(\dot{x},\dot{y}) =
\begin{pmatrix}
\frac{\partial \dot{x}}{\partial x} & \frac{\partial \dot{x}}{\partial y} \\
\frac{\partial \dot{y}}{\partial x} & \frac{\partial \dot{y}}{\partial y} \\
\end{pmatrix} =
\begin{pmatrix}
2-2x-y & -x-\nu\\
-2xy  + \nu & \mu-3y^{2}-x^{2} \\
\end{pmatrix}
\tag{3}
$$


Conbine (1),(2),(3), we can get below matrix and in this matrix $\tau = 2 + \mu$, $\Delta=2\mu+\nu^2$.

\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2 & -\nu \\
\nu & \mu \\
\end{pmatrix}
\tag{4}
\end{equation}


As we know both $\nu$ and $\mu$ are positive so $\tau$ and $\Delta$ are positive too, which means the type of fixed point is depends on $\tau^2 - 4\Delta$

\begin{equation}
\tau^2 - 4\Delta = (2+\mu)^2 - 4(2\mu + \nu^2) = 4 + \mu^2 + 4\mu - 8\mu - 4\nu^2 = 4 +\mu^2 - 4\nu^2 =(\mu-2)^2 - 4\nu^2
\end{equation}

let $\tau^2 - 4\Delta = 0$ , we get $\pm(\mu-2)=2\nu$.

1. when $\mu > 2, \mu = 2\nu +2$
2. Since when  $\mu = 2$, we will get $\nu = 0$, but $\nu$ is positive, so $\mu \ne 2 \ and \ \mu >0 $
3. when $\mu < 2, \mu = -2\nu +2$


Finally, Since $\Delta=2+u$ is always positive, we only need consider the condition when $\Delta>0$ and the type of fixed point are below.

1. when $\tau^2 - 4\Delta > 0$ , $\mu>2$ which means $\tau=\nu+2>0$, so it is unstable node.
2. when $\tau^2 - 4\Delta = 0$, except $\mu=2$, they are star nodes and degenerate node.
3. when $\tau^2 - 4\Delta < 0$, $0<\mu<2$ $\mu>2$ which means $\tau=\nu+2>0$, so it is unstable spiral.


# (b) Find all the fixed points.

As the question mentioned $\nu=0$, So the new $\dot{x} \ and  \ \dot{y} \ are \ below$.


\begin{equation}
\frac{dx}{dt} = 2x(1-\frac{x}{2}) - xy
\tag{5}
\end{equation}

\begin{equation}
\frac{dy}{dt}= y(\mu - y^2) -x^2y
\tag{6}
\end{equation}


To find all fixed ponts, we need set the euqation 5 and 6 euqal to 0.

\begin{equation}
\frac{dx}{dt} = 2x(1-\frac{x}{2}) - xy = x(2-x-y)= 0
\tag{7}
\end{equation}

\begin{equation}
\frac{dy}{dt}= y(\mu - y^2) -x^2y = y(\mu-y^2-x^2)= 0
\tag{8}
\end{equation}

### There are 2 condition for equation (7) and (8) = 0.

#### 1. Assuming x = 0  and let equation (8)=0, then we get below.
##### (i) when y = 0 then the fixed point is (0,0).
##### (ii) when $y \ne0$ we get below.
$$u-y^2-x^2=0$$

$$\mu-y^2=0 \$$

$$y = \sqrt{\mu}$$

So when x = 0, $y\ne0$ the fixed point is (0,$\sqrt\mu$).

#### 2. Assuming $x \ne 0$, we get below.

\begin{equation}
2-x-y=0
\tag{9}
\end{equation}

\begin{equation}
y(\mu-y^2-x^2)=0
\tag{10}
\end{equation}

Conbine equation 9 and 10, we can get equation 11.
\begin{equation}
y(\mu-y^2-(2-y)^2)=y(2y^2-4y-\mu+4)=0
\tag{11}
\end{equation}

Let equation (11)=0, we can get below.

##### (i) when y = 0, let euquation (7)=0, x=2  this fixed point is (2,0).
##### (ii) when $y \ne 0$, we need set equation (12) = 0

$$2y^2-4y-\mu+4=0 \tag{12}$$
In this case, we need find the solution of Quadratic Euation.

Firstly we analyze the $\Delta$ to check how many solution we can get when different $\mu$.

$$\Delta = (-4)^2 - 4 * 2 *(\mu+4)=8(\mu-2)$$

###### when $\Delta>0$, $\mu>2$, we get 2 solutions for equation (12).

$$y = \frac{4\pm\sqrt{8(\mu-2)}}{4}=1 \pm \sqrt{\frac{\mu-2}{2}}$$

put y into the euqation (9) we can get x as below.

$$ x = 1\pm \sqrt{\frac{\mu-2}{2}}$$

So when $\mu>2$, we have 2 fixed points $(1 - \sqrt{\frac{\mu-2}{2}},1 + \sqrt{\frac{\mu-2}{2}})$ and $(1 + \sqrt{\frac{\mu-2}{2}},1 - \sqrt{\frac{\mu-2}{2}})$

###### when $\Delta=0$, $\mu=2$, one solution, put $\mu=2$ in to equation (12), we can get below.

$$2y^2-4y+2=0$$

$$(y-1)^2$$

After solve the euqation we can find y=1, put y=1 into euqaion (9), we can get x=1. 

So, when $\mu=2$, we have one fixed point (1,1).


###### when $\Delta<0$, $\mu<2$, no solution, no fixed point.


##### Finally, the total fixed points are below.

(0,0),

$(0,\sqrt\mu)$, 

(2,0), 

$(1 - \sqrt{\frac{\mu-2}{2}},1 + \sqrt{\frac{\mu-2}{2}})$, 

$(1 + \sqrt{\frac{\mu-2}{2}},1 - \sqrt{\frac{\mu-2}{2}})$,

(1,1)


# (c)Determine the character of all the fixed points for $\mu=\frac{17}{8}$.

Since $\mu=\frac{17}{8}>2$, we can firstly skip the fixed points (1,1) when $\mu<=2$.

So in this question, we just only consider 5 fixed points as below.

(0,0),

(2,0),

$(0,\sqrt\mu)=(0,\sqrt{\frac{17}{8}})$, 

$(1 - \sqrt{\frac{\mu-2}{2}},1 + \sqrt{\frac{\mu-2}{2}}) = (\frac{5}{4},\frac{3}{4})$, 

$(1 + \sqrt{\frac{\mu-2}{2}},1 - \sqrt{\frac{\mu-2}{2}})=(\frac{3}{4},\frac{5}{4})$,

Firstly, put $\mu=\frac{17}{8}$ and $\nu=0$ into jacobian matrix (3) then we get new jacobian matrix (13) as below.

\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2-2x-y & -x \\
-2xy & \frac{17}{8}-3y^{2}-x^{2} \\
\end{pmatrix}
\tag{13}
\end{equation}



After that, we need put those fixed point and $\nu=0$ into jacobian matrix (13) one bye one and analyze it.

###### 1. when fixed point is $(0,0)$, we put it in jacobian matrix (13) and get below.

\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2-2x-y & -x \\
-2xy & \frac{17}{8}-3y^{2}-x^{2} \\
\end{pmatrix}=
\begin{pmatrix}
2  & 0 \\
0   & \frac{17}{8}  \\
\end{pmatrix}
\end{equation}

In this case, 

$\tau=2+\frac{17}{8} = \frac{33}{8}>0$

$\Delta = 2 * (-\frac{17}{8})= \frac{17}{4}>0$

Because $\tau^2 - 4\Delta= (\frac{33}{8})^2-4*\frac{17}{4}= \frac{1}{64}>0$ 

So, it is unstable node.

###### 2. when fixed point is $(2,0)$, we put it in jacobian matrix (13) and get below.

\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2-2x-y & -x \\
-2xy & \frac{17}{8}-3y^{2}-x^{2} \\
\end{pmatrix}=
\begin{pmatrix}
-2  & 2 \\
0   & -\frac{15}{8}  \\
\end{pmatrix}
\end{equation}

In this case, 

$\tau=-2 + (-\frac{15}{8}) = -\frac{1}{8}>0$

$\Delta = -2 * (-\frac{17}{8})= \frac{15}{4}>0$

Because $\tau^2 - 4\Delta= (-\frac{1}{8})^2-4*\frac{15}{4}= \frac{1}{64}-15<0$ 

So, it is unstable spiral.

###### 3. when fixed point is $(0,\sqrt\frac{17}{8})$, we put it in jacobian matrix (13) and get below.

\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2-2x-y & -x \\
-2xy & \frac{17}{8}-3y^{2}-x^{2} \\
\end{pmatrix}=
\begin{pmatrix}
2-\sqrt{\frac{17}{8}}  & 0 \\
0 & -\frac{17}{4} \\
\end{pmatrix}
\end{equation}

In this case, 

$\tau=2-\sqrt{\frac{17}{4}}-(-\frac{17}{4}) = \frac{25}{4} - \sqrt{\frac{17}{4}}<0$

$\Delta = (2-\sqrt{\frac{17}{4}}) * (-\frac{17}{4})= \frac{17}{4}*\sqrt{\frac{17}{4}}-{\frac{17}{2}}<0$

Because $\Delta<0$. So, it is saddle node.



###### 4. when fixed point is $(\frac{5}{4},\frac{3}{4})$, , we put it in jacobian matrix (13) and get below.


\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2-2x-y & -x \\
-2xy & \frac{17}{8}-3y^{2}-x^{2} \\
\end{pmatrix}=
\begin{pmatrix}
-\frac{5}{4}  & -\frac{5}{4} \\
-\frac{15}{8}   & -\frac{9}{8}  \\
\end{pmatrix}
\end{equation}

In this case, 

$\tau=-\frac{5}{4}-\frac{9}{8} = -\frac{19}{8}<0$

$\Delta = -\frac{5}{4} * (-\frac{9}{8}) - (-\frac{5}{4})*(-\frac{15}{8})= -\frac{15}{16}<0$


So, it is saddle node.


###### 5. when fixed point is $(\frac{3}{4},\frac{5}{4})$, , we put it in jacobian matrix (13) and get below.


\begin{equation}
J(\dot{x},\dot{y}) =
\begin{pmatrix}
2-2x-y & -x \\
-2xy & \frac{17}{8}-3y^{2}-x^{2} \\
\end{pmatrix}=
\begin{pmatrix}
-\frac{3}{4}  & -\frac{3}{4} \\
-\frac{15}{8}   & -\frac{25}{8}  \\
\end{pmatrix}
\end{equation}

In this case, 

$\tau=-\frac{3}{4}-\frac{25}{8} = -\frac{31}{8}<0$

$\Delta = -\frac{3}{4} * (-\frac{25}{8}) - (-\frac{3}{4})*(-\frac{15}{8})= \frac{15}{16}>0$

Because $\tau^2 - 4\Delta= (-\frac{31}{8})^2-4*\frac{15}{16}= \frac{721}{64}>0$ 

So, it is stable node.

###### Finally

(0,0) is unstable node.

(2,0) is unstable spiral.

$(0,\sqrt\frac{17}{8})$ and $(\frac{5}{4},\frac{3}{4})$ are saddle node.

$(\frac{3}{4},\frac{5}{4})$ is stable node.

# (d) How many fixed points are there when $\mu$ = 1?

From the question (b) we can get all fixed points when different $\mu$ at below.

(0,0),

$(0,\sqrt\mu)$, 

(2,0), 

$(1 - \sqrt{\frac{\mu-2}{2}},1 + \sqrt{\frac{\mu-2}{2}})$, 

$(1 + \sqrt{\frac{\mu-2}{2}},1 - \sqrt{\frac{\mu-2}{2}})$,

(1,1)

But in this case, we only set $\mu=1$, So we should skip the fixed points when $\mu>=2$.
Finally, we got have 3 fixed points as below when $\mu=1$.

(0,0),

$(0,\sqrt\mu)=(0,1)$, 

(2,0), 

## (e) What bifurcation occurs between $\mu$ = 1 and $\mu=\frac{17}{8}$? At what value $\mu_c$ does it occur?

The saddle-node bifurcation occurs between $\mu=1 and \mu=\frac{17}{8}$ and the $\mu_c=2$

Because when $\mu>2$, we get 2 new fixed points,$(1 - \sqrt{\frac{\mu-2}{2}},1 + \sqrt{\frac{\mu-2}{2}})$ and $(1 + \sqrt{\frac{\mu-2}{2}},1 - \sqrt{\frac{\mu-2}{2}})$.

when the $\mu$ close to 2 then we will find these 2 fixed points will close to (1,1) and after $\mu<2$ they dissappear.

So it is a saddle-node bifurcation between $\mu=1 and \mu=\frac{17}{8}$ and the $\mu_c=2$.

