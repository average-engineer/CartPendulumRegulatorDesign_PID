# CartPendulumRegulatorDesign_PID
Using PID controller (and classical control approach) for regulator design of Cart Pole system.

**CONTROL OBJECTTIVE**: Regulation of the pole angular position *irrespective* of how the cart moves (i.e. the cart horizontal postion is not fedback into the controller).

![Control Architecture](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/ClosedLoopSys.jpg)

*System Input*: System Actuation (Horizontal Force on Cart)
*System Output*: Pole Angular Position

***OPEN LOOP SYSTEM BEHAVIOUR***: When there is no controller actuating the system

![Open Loop Poles](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/OpenLoop_Plant_Poles.png)

As expected, one of the poles is on the Right hand plane, thus the system is unstable.

***CLOSED LOOP SYSTEM BEHAVIOUR (PID Controller)***:

`Transfer Function of Plant: tf_p = -6/(168*s^2 - 706.3)`

`Transfer Function of PID Controller: tf_c = (-500*s^2 - 500*s -10)/s`

`Transfer Function of closed system: tf_cs = feedback(tf_p,tf_c)`

![Reaaranged closed loop system](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/ClosedLoopRe.jpg)

<h2>Some Results with Impulse Force introduced as Distrubance Force</h2>

* `Ki = -10`
![Impulse Response](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/ClosedLoopImpulseRes_Ki%20%3D%20-10.png)
![Poles](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/ClosedLoopPoles_Ki%20%3D%20-10.png)

* `Ki = -100`
![Impulse Response](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/ClosedLoopImpulseRes_Ki%20%3D%20-100.png)
![Poles](https://github.com/average-engineer/CartPendulumRegulatorDesign_PID/blob/main/Images/ClosedLoopPoles_Ki%20%3D%20-100.png)

***As expected, Case 2 (Lower Integral Control) shows a faster response (lower settling times)***

**Realising the advantage of Control Strategies based on Modern Control Theory rather than Classical Control Theory**:

If we also want to control the horizontal position of the cart, we would have to develop a SIMO system whose formulation becomes a little more complex in the Laplace domain (Plant 1: Pole angular position output, Plant 2: Horizontal Cart Position).

But in Modern Control methods, (for eg. Pole Placement), the control law is based on the system states, which include both the cart horizontal position and pole angular position. Thus, the states get included in feedback automatically.
