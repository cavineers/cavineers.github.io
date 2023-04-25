# PID Controllers

The PID (Proportional-Integral-Derivative) controller is a widely used control algorithm in the field of robotics. It is an essential tool for controlling motor speed, position, and many other dynamic systems. 

## Control Terms

A PID Controller is consisted of three terms that control its output.



| Letter | Term | Description |
| --   | --------------|--------------------- |
| **P**    | Proportional |  proportional to the current error between the desired **setpoint** and the measured **process variable**. |
| **I**    | Integral | accumulates the error over time and provides a long-term correction to the **control signal**.|
| **D**    | Derivative | proportional to the rate of change of the error signal. It provides a damping effect to the **control signal** |

!!! abstract "Definitions"

    - **Setpoint**: The desired value of the **process variable**.
    - **Process Variable**: The value of the variable being controlled.
    - **Control Signal**: The output of the PID controller.


## Nomenclature

The following nomenclature will be used to describe the PID controller's equations in this section.

| Notation | Definition |
| --   | --------------|
| **e(t)**    | Error |
| **u(t)**    | Control signal |
| **r(t)**    | Setpoint |
| **y(t)**    | Process variable|

| Variable | Definition |
| --   | --------------|
| **K~p~**    | Proportional gain |
| **K~i~**    | Integral gain |
| **K~d~**    | Derivative gain |

## Proportional Term

The Proportional term is responsible for adjusting the control output proportionally to the current error. This means that the larger the error, the larger the corrective action applied to the system. 

???+ note inline end "**K~p~** Proportional Gain"

    The Proportional gain, represented by the variable K determines the strength of this correction. A higher value of Kp results in a stronger correction for a given error.

The control signal of the proportional term is calculated as follows:
### u(t) = K~p~e(t)


The proportional gain is multiplied by the error to produce the control signal.

A simple P controller can be modelled as follows:

![Simple P Controller Block Diagram](../../assets\pid-p.png){ align=center }


## Integral Term

The Integral term is responsible for adjusting the control output based on the accumulated error over time. This means that the longer the error persists, the larger the corrective action applied to the system.

???+ note inline end "**K~i~** Integral Gain"

    The Integral gain, represented by the variable Ki determines the strength of this correction. A higher value of Ki results in a stronger correction for a given error.

The control signal of the integral term is calculated as follows:

### u(t) = K~i~ ∫e(t)dt

The integral gain is multiplied by the integral of the error to produce the control signal.


