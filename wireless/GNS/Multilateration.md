---
tags:
  - gnss
---
# definition
> the end goal of GNSS is to **estimate** the 3 coordinates of the receiver


>With the [[wireless/GNS/pseudorange|pseudoranges]] of three satellite the position can be anywhere on one of the two point where the 3 spheres intersect. Usually one is on the Earth's surface, the other not

![](https://i.sstatic.net/e2g6M.jpg).


# formula for the geometric Range
range = distance between tx e rx
$t_0$ time-stamped into the transmitted signal 
$\tau$ is defined as the **travelling time**
$$R = (T_{RX} - T_{TX}) * C = [(t_0+\tau)-(t_0)]*C=\tau*C$$

> [!Attention] synchronization of clocks is IMPORTANT

# synchronization


> satellites have high grade **atomic clock** that are very **stable** in time.

The ground system, also, plays a role in keeping the satellites' clock synchronized

> [!hint] therefore, **synchronous clocks** are assumed to be in the satellites 
> $\delta t^s = 0$


the **user clock** is impossible to have it aligned, at low cost and complexity 
It has a **bias** $\delta t_u$ with respect to the system time
Measured distance is then called **pseudorange**

$$\rho=c*\tau+c*\delta t_u$$


so we have 4 **unknowns**:
- user coordinates $x_u, y_u, z_u$
- Bias of the user clock $\delta t_u$

# estimation problem 
$$
\begin{cases}
\rho _ 1=\sqrt{(x _ 1-x _ u)^2+(y _ 1-y _ u)^2+(z _ 1-z _ u)^2}+b _ {ut}\\
\rho _ 2=\sqrt{(x _ 2-x _ u)^2+(y _ 2-y _ u)^2+(z _ 2-z _ u)^2}+b _ {ut}\\
\rho _ 3=\sqrt{(x _ 3-x _ u)^2+(y _ 3-y _ u)^2+(z _ 3-z _ u)^2}+b _ {ut}\\
\rho _ 4=\sqrt{(x _ 4-x _ u)^2+(y _ 4-y _ u)^2+(z _ 4-z _ u)^2}+b _ {ut}
\end{cases}
$$
$(x _ j,y _ j,z _ j)$  Satellite position: center of the pseudo-sphere

$\rho _ j$ Pseudorange: radius of the pseudo-sphere

$b _ {ut}=c \cdot \delta t _ u$  Clock bias


$$\rho _ j=\sqrt{(x _ j-x _ u)^2+(y _ j-y _ u)^2+(z _ j-z _ u)^2}+b _ {ut}$$



Can be approximated through the Taylor expansion around a known location:

$$(\hat{x} _ u, \hat{y} _ u, \hat{z} _ u, \hat{b} _ {ut})$$

$$
\hat{\rho _ j}=\sqrt{(x _ j-\hat{x} _ u)^2+(y _ j-\hat{y} _ u)^2+(z _ j-\hat{z} _ u)^2}+b _ {ut}
$$

> [!tip]
>  it is not a restriction to choose $\hat{b} _ {ut}=0$


At a first order approximation

$$\Delta \rho _ j=\hat{\rho _ j}-\rho _ j $$

$$
\Delta \rho _ j=a _ {xj}\Delta x _ u + a _ {yj}\Delta y _ u+ a _ {zj}\Delta z _ u -\Delta b _ {ut}
$$

Having defined

$$
\begin{aligned}
\Delta x _ u = x _ u - \hat{x} _ u \\
\Delta y _ u = y _ u - \hat{y} _ u \\
\Delta z _ u = z _ u - \hat{z} _ u \\
\Delta b _ {ut} = b _ {ut} - \hat{b} _ {ut}
\end{aligned}
$$

The coefficients are: 

$$
a _ {xj} = \frac{x _ j-\hat{x} _ u}{\hat{r} _ j},
a _ {yj} = \frac{y _ j-\hat{y} _ u}{\hat{r} _ j},
a _ {zj} = \frac{z _ j-\hat{z} _ u}{\hat{r} _ j}
$$

and

$$
\hat{r} _ j = \sqrt{(x _ j-\hat{x} _ u)^2 + (y _ j-\hat{y} _ u)^2 + (z _ j-\hat{z} _ u)^2}
$$

is the geometrical distance between the linearization point and the satellite



$$
\begin{cases}
\Delta\rho _ 1=a _ {x1}\Delta x _ u + a _ {y1}\Delta y _ u+ a _ {z1}\Delta z _ u -\Delta b _ {ut}\\
\Delta\rho _ 2=a _ {x2}\Delta x _ u + a _ {y2}\Delta y _ u+ a _ {z2}\Delta z _ u -\Delta b _ {ut}\\
\Delta\rho _ 3=a _ {x3}\Delta x _ u + a _ {y3}\Delta y _ u+ a _ {z3}\Delta z _ u -\Delta b _ {ut}\\
\Delta\rho _ 4=a _ {x4}\Delta x _ u + a _ {y4}\Delta y _ u+ a _ {z4}\Delta z _ u -\Delta b _ {ut}\\
\end{cases}
$$$$
\Delta\rho = 
\begin{bmatrix}
    \Delta\rho _ 1 \\
    \Delta\rho _ 2 \\
    \Delta\rho _ 3 \\
    \Delta\rho _ 4
\end{bmatrix},\quad

H = 
\begin{bmatrix}
	a _ {x1} & a _ {y1} & a _ {z1} & 1 \\
	a _ {x2} & a _ {y2} & a _ {z2} & 1 \\
	a _ {x3} & a _ {y3} & a _ {z3} & 1 \\
	a _ {x4} & a _ {y4} & a _ {z4} & 1 \\
\end{bmatrix}, \quad

\Delta x = 
\begin{bmatrix}
	\Delta x _ u \\
	\Delta y _ u \\
	\Delta z _ u \\
	-\Delta b _ {ut}  
\end{bmatrix}
$$


$$\Delta \rho = H \Delta x$$
In case four satellites are used
$$\Delta x = H^{-1}\Delta \rho$$
If a larger number of satellite is used, 𝐇 is non-square and not invertible


$$H = 
\begin{bmatrix}
	a _ {x1} & a _ {y1} & a _ {z1} & 1 \\
	a _ {x2} & a _ {y2} & a _ {z2} & 1 \\
	. & . &. & . \\
	. & . &. & . \\
	
	a _ {xn} & a _ {yn} & a _ {zn} & 1 \\
\end{bmatrix}
$$
#### The Least Squares Solution
If more than four range measurements are used (more than four satellite in LoS)
It is possible to use a Least Square solution
Provided that $(H^T H)^{-1}$  is [non-singular](https://en.wikipedia.org/wiki/Invertible_matrix), the solution is : 
$$\Delta x = (H^TH)^{-1}H^T \Delta \rho$$
A GNSS receiver solves the equation by recursive methods.
Alternatively, a Kalman filter or other advanced Bayesian estimation methods can be used
# Positioning Errors


The pseudorange **measurement** is **affected by errors** due to system intrinsic uncertainties, propagation in atmosphere, receiver noise and other factors

$$\rho _ j=\sqrt{(x _ j-x _ u)^2+(y _ j-y _ u)^2+(z _ j-z _ u)^2}+b _ {ut} + \epsilon  $$
The error in the pseudorange measurement affects the user position
Intentional and unintentional interference can increase the error contribution

The set of equations to solve is then
$$\Delta \rho + \delta \rho = H(\Delta x + \delta x)$$
Where $\delta x$ is the error in the position and time estimation

The Least Squares solution is applied on measurements errors as well

$$\delta x = [(H^TH)^{-1}H^T]\delta \rho$$
$[(H^TH)^{-1}H^T]$ depends only on the satellite geometry
$\delta \rho$ depends on the error in the pseudorange estimation
