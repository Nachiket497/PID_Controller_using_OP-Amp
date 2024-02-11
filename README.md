# PID_Controller_using_OP-Amp

Aim :
-----

Voltage control across system using PID controller designed using OPAMP.

Abstract
--------

****

A PID controller is an instrument used in a wide range of applications
for industrial process control such as to regulate temperature, flow,
pressure, speed, and other process variables. Approximately 95% of the
closed-loop operations of the industrial automation sector use PID
controllers. PID stands for Proportional-Integral-Derivative. These
three controllers are combined in such a way that it produces a control
signal and functions based on a control loop feedback mechanism to
control process variables and are the most accurate and stable
controller.

PID control is a well-established way of driving a system towards a
target position or level. It’s practically ubiquitous as a means of
controlling temperature and finds application in myriad chemical and
scientific processes as well as automation. PID control uses closed-loop
control feedback to keep the actual output from a process as close to
the target or setpoint output as possible.

In this project, we are making optimal and effective use of analog
electronic components mainly OPAMP for designing PID controller. As the
name suggests, the PID controller is having three control parameters,
namely, proportional, integral, and derivative-based on which it
functions, we need to test each of these components separately and then
integrate them. Here, we are assuming that our plant is for controlling
voltage and our controller should be tunable. Therefore, implementing
the components for all these three controllers is done using LM741IC
OPAMP.for this purpose resistors, potentiometer, and capacitors of
suitable values were chosen as shown in the circuit diagram



In many real-world scenarios, we have a voltage-sensitive system and
system tuner. There it is expected that voltage across the system gets
steadily tuned w.r.t our reference voltage. In such cases, the PID
controller plays an important role.

Basicaly, our model takes reference voltage(that is to be set across the
system) as input, computes error, and provides output to the system.
Recursively, it takes feedback from the system to measure error. Note
that in this project, our system is going to be **LED**. Here, we tried
to design a PID Controller using OPAMP as you will see further below.

Software
--------

Multisim.

Block diagram
-------------

****

![block diagram .](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/PID%20Diagram-01.png)

As you can see in the block diagram, the steps of designing will be as
follows.

-   Error counted over measured value and reference will be given as
    input to PID controller.

-   PID controller outputs a voltage value that will be one step closer
    to attain reference voltage.

-   Our system, in this case, is LED. Voltmeter acts as a reading
    component that sends feedback through Buffer back to the PID
    controller.

Circuit diagram
---------------

****

![Circuit diagram of PID controller.](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/Circuit_diagram.jpeg) [fig:circuit diagram of
PID]

![block diagram of CRO.](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/Circuit_diagram_component_wise.jpeg) [fig:ckt PID]

[fig:circuit diagram of PID] shows the circuit that was made in
simulation software Simulink. Along with every component’s name. The
entire circuit was built with opamp only. Opamp with different
configuration performs different function. All together in ckt, they
construct PID controller.

Refer [fig:ckt PID] With the help of this diagram let us look at each
and every component of this circuit...

-   Error calculation

    1.  RED : Error calculation : OPAMP as difference amplifier.

-   PID

    1.  YELLOW : Proportional : OPAMP as inverting amplifier

    2.  PINK : Differentiator : OPAMP as differentiator.

    3.  GREEN : Integrator : OPAMP as integrator.

-   Feedback

    1.  PURPLE : Buffer : OPAMP as a voltage follower.

Now let’s have look at each and individual component in detail. Lets
look at their working.

Traverse through circuit
------------------------

****

Op-amp- operational amplifier is the basic amplifier, which can be used
by adding few components to perform various mathematical operations.

**1) Inverting Op-Amp**

-   The following figure is of inverting Op-Amp. It is called inverting
    amplifier because it inverts the polarity of the voltage applied at
    the input.

-   Here, Vo i.e., is output voltage which is fed back to inverting
    input terminal through Rf where it is feedback resistor.

****

<!-- ![](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/invertingopamp.png)  -->
<p align="center">
  <img width="200" src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/invertingopamp.png">
</p>
****
**2) Differentiator**

-   If the resistor R1 is replaced by a capacitor, an inverting Op-amp
    can be used as a differentiator.

-   As the name suggests , circuit performs the mathematical operation
    of differentiation, that is output waveform is the derivative of the
    input waveform.

-   The equation for the differentiator is as follows.

<!--     $$ V_o = -RC\frac{dv_{in}}{dt} $$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/differentator.png">
</p>


-   The minus sign in the formula indicates 180phase shift in the output
    waveform with respect to input signal.

****

<!-- ![](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/differentiatoropamp.png)  -->
<p align="center">
  <img width="200" src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/differentiatoropamp.png">
</p>
****

**3) Integrator**

-   If the resistor Rf is replaced by a capacitor, an inverting Op-amp
    can be used as integrator circuit.

-   As the name suggests , circuit performs the mathematical operation
    of integration, that is output waveform is the integral of the input
    waveform. The equation for the integrator is as follows.

<!--     $$V_o = -RC\int{dV_{in}} dt$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/integrator.png">
</p>

-   The circuit provides an output voltage which is proportional to the
    time integral of input and where is time constant of the integrator.

****

<!-- ![](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/integratoropamp.png) [fig:pis1] -->
<p align="center">
  <img width="200" src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/integratoropamp.png">
</p>

****

**4) Difference amplifier**

-   A differential amplifier generates an output which is difference
    between the outputs due to both the inputs.

-   The above difference amplifier can be analysed using superposition
    principle i.e. by considering only 1 source in the circuit at a
    time.

****

<!-- ![](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/differenceopamp.png) [fig:pis1] -->
<p align="center">
  <img width="200" src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/differenceopamp.png">
</p>

****

**5) Buffer or Voltage follower**

-   Voltage buffer which is also known as the voltage follower or unity
    gain amplifier, is an amplifier with its gain unity i.e., 1.

-   It is a special case of non-inverting amplifier having maximum
    negative feedback. So, voltage is also minimum.

-   Even though the gain of 1 doesn’t give us any voltage amplification,
    voltage buffer is very useful because it prevents one stage’s input
    impedance from loading prior stage’s output impedance, which causes
    the signal losses.

****

<!-- ![](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/bufferopamp.png){:height="36px" width="36px"} [fig:pis1] -->
<p align="center">
  <img width="200" src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/bufferopamp.png">
</p>
 
****


So, we saw in brief how opamp can be used in different configurations
and how do they function. Now using this idea, we will look at the
circuit made previously to execute the PID controller....

Working
-------

-    **Error Calculation**

    First of all we calculate the error using the Differential
    amplifier, we apply the reference voltage to the Non-inverting
    terminal of the op-amp and the sensor reading to the inverting
    terminal, so we get

<!--     $$Error = Gain * ( Reference -  Sensor Reading )$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/error.png">
</p>

    For the accuracy purpose, we are using the gain of 10 in the
    difference amplifier. hence we get the required error as the input
    to the PID controller

-    **Proportional Controller**

    Now , we have the error. for this part we are using the inverting op
    amp. which take the error and amplify it according to our need .

<!--     $$Proportional Gain = \frac{Rf}{R1}  Error$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/pg.png">
</p>

    In this way, we get the Proportional gain using the inverting
    op-amp, but it should be noticed that it is inverted.

-    **Integral Controller**

    we have the error from the difference amplifier , by using the op
    amp as a integrator with the input as Error, we get the integration
    of the error with respect to the time.

<!--     $$Integral Gain =  RC \int{Error} *dt$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/ig.png">
</p>

    In this way, we get the Integral gain using the inverting op-amp,
    but it should be noticed that it is inverted.

-    **Derivative Controller**

    we have the error from the difference amplifier, by using the op-amp
    as a differentiator with the input as Error, we get the
    differentiation of the error concerning the time.

<!--     $$Differential Gain = \frac{1}{ RC} \frac{d Error} {dt}$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/dg.png">
</p>

    In this way we get the Differential gain using the inverting op amp
    , but it should be notice that it is inverted.

-    **Adding all Gains**

    we have calculated all gains now we going to add all the gains by
    using an op-amp as the inverting summing amplifier, we are using the
    inverting because ore gains are inverted in the last stage.

<!--     $$Overall Gain = - Rf (\frac{P.G}{R1}+\frac{I.G}{R2}+\frac{D.G}{R3})$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/og.png">
</p>

-    **Inputs to the System**

    After getting the overall gain we add it to the input of the system
    so that output changes according to our requirements. In our case,
    we are applying it to the -ve terminal of the dc source so that
    potential at the +ve terminal may decrease or increase

-    **Taking Sensor Reading**

    For this we are using an op-amp as buffer cause buffer has high
    input impedance so no current will flow through it, this will not
    produce any side effects on the system. In this way, we are taking
    the sensor reading using buffer

-    **System**

    For the simulation purpose only we are using LED as the system, we
    can replace our system with the other device which required voltage
    regulation

-   In this way the Circuits works and gives the required voltage across
    the system

Tuning parameters
-----------------

****
**Trial and error PID tuning method**\

The trial-and-error method is relatively easy, once you get a clear
understanding of PID parameters. It steps through the parameters from
proportional to integral to derivative. Usually, you start from an
existing set of parameters from which you perform small tweaks to
improve the response. For new PID loops, you start with a rough and safe
initial guess.

One considers:

-   The P-action is introduced to increase the speed of the response.
    Exaggerated P-action results in oscillation. It refers to parameter
    $K_p$.

-   The I-action is introduced to obtain a desired steady-state
    response. The disadvantage is a higher oscillating response over a
    longer period. It refers to parameter $K_i$.

-   The D-action is introduced for damping purposes. The disadvantage is
    the fact that oscillation on a high frequency is more probable, plus
    the sensitivity to the noise. It refers to parameter $K_d$.

Trial and error method is easy way to obtain a reasonable result. But
It’s time-consuming. It takes a long time to achieve good performance.

***How do we tune these parameters??***
**Answer:**Inverting Summer amplifier


Summer amplifier is another application of OPAMP. It is used to get the
weighted average of inputs.

<!-- $$V_o = -R_f(\frac{V_1}{R_1}+\frac{V_2}{R_2}+\frac{V_3}{R_3})$$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/summer.png">
</p>

Where V1, V2, V3 will be outputs through P, I, D components. So, we can
say,
<!-- $K_p = \frac{-R_f}{R_1}$ -->
<!-- $K_i = \frac{-R_f}{R_2}$ -->
<!-- $K_d = \frac{-R_f}{R_3}$ -->
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/kp.png">
</p>
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/ki.png">
</p>
<p align="center">
  <img src="https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/equations/kd.png">
</p>

Hence by setting Resistance values, we are setting parameters. In this
way we can tune parameters.

The circuit is built. Now let’s try to simulate it and try to achieve
the goal...

Transient analysis
------------------

****
Here we could paste analysed images only but, **A detailed video of this
testing is recording and loaded over [This Link](https://drive.google.com/file/d/1OLOjiyjNxIE9lzGEMWcn49jJz9GvPYvm/view?usp=sharing).**

![variation in Voltage across system with time. Reference voltage set
here was 2V. It can be observed that voltage stablizes
succesfully](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/pis1.png) [fig:pis1]

![variation in Voltage across system with time. Reference voltage set
here was 1V. It can be observed that voltage stablizes
succesfully](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/pis2.png) [fig:pis2]

![variation in Voltage across system with time. Reference voltage set
here was 3V. It can be observed that voltage stablizes
succesfully](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/pis3.png) [fig:pis3]

1.  Refer [fig:pis1] Here you can observe that initially, the voltage
    across LED was 0. This resulted in +ve Error to PID controller and a
    signal was provided that made to increase the output voltage. It
    slowly starts increasing and crosses a reference voltage of 2V. Now
    due to -ve error, voltage drops down. This process goes on and
    oscillates till output voltage reaches the reference voltage of 2V.

    Kp:Ki:Kd = 10:1:10 . Its effect can be observed in the transient
    analysis.

    -   Due to moderate Kp, the voltage reaches to reference voltage
        fast.

    -   Due to Low but moderate Ki, with PID, pushes the graph to
        reference voltage but with some oscillations.

    -   Due to moderate Kd, PID removers extra oscillations and cases
        faster damping that results in achieving reference voltage just
        in 100 ms !!!

2.  Refer [fig:pis2] Here you can observe that initially, the voltage
    across LED was 0. This resulted in +ve Error to PID controller and a
    signal was provided that made to increase the output voltage. It
    slowly starts increasing and crosses a reference voltage of 1V. Now
    due to -ve error, voltage drops down. This process goes on and
    oscillates till output voltage reaches the reference voltage of 2V.

    Kp:Ki:Kd = 100:1:8.3 . Its effect can be observed in the transient
    analysis.

    -   Due to moderate Kp, the voltage reaches to reference voltage
        fast.

    -   Due to Low but Ki, with PID, pushes the graph to reference
        voltage but with lesser oscillations.

    -   Due to moderate Kd, PID removers extra oscillations and cases
        faster damping that results in achieving reference voltage just
        in 100 ms !!!

3.  Refer [fig:pis3] Here you can observe that initially, the voltage
    across LED was 0. This resulted in +ve Error to PID controller and a
    signal was provided that made to increase the output voltage. It
    slowly starts increasing and crosses a reference voltage of 3V. Now
    due to -ve error, voltage drops down. This process goes on and
    oscillates till output voltage reaches the reference voltage of 2V.

    Kp:Ki:Kd = 200:1:16.6 . Its effect can be observed in the transient
    analysis.

    -   Due to moderate Kp, the voltage reaches to reference voltage
        fast.

    -   Due to moderate Ki, with PID, pushes the graph to reference
        voltage but with some oscillations. Since reference voltage was
        high in this case (3V) we had to set Ki high which causes more
        oscillation.

    -   Due to moderate Kd, PID removers extra oscillations and cases
        faster damping that results in achieving reference voltage just
        in 100 ms !!!. Kd also had to be adjusted high

Further modification
--------------------

****

The model built in this project can further be extended to many other
applications such as, **Temperature control**. Since the simulator lacks
the availability of temperature sensors, and also due to time
constraints, we had to restrict this project to voltage control only.
But this could be one of the further modifications possible.

Certain changes those are required-

1.  Replacement of voltmeter with temperature sensor.

2.  System could be replaced with an iron of any device whose
    temperature needs to be maintained,

3.  Reference here too will be set some voltage value only. Cause at the
    end, whatever heat will be produced to raise or lower the
    temperature, will be due to power loss through filament only. It
    will be maintained with reference voltage only.

4.  Reference voltage could be manipulated to find its temperature
    equivalent and that could be displayed over there.

The basic ckt and structure of PID controller will remain the same, i.e.
integrator, differentiator, inverting amplifier using opamp. Just there
will be a change in a system and other PID parameters can be tuned as
per the requirements. Here is an example :

![Temerature control using PID
controller.](https://github.com/Nachiket497/PID_Controller_using_OP-Amp/blob/main/images/Closed-loop-PID-temperature-control-of-water-heating-tank-system.png)
[fig:mod temp]

Conclusion
----------

-   PID controller was studied briefly

-   OPAMP and its linear, as well as non-linear application, were
    studied.

-   PID controller was designed using OPAMP.

-   PID controller was tuned.

-   A remarkable phenomenon observed is that the PID controller achieves
    desired output just within 100ms.

-   It is shown that an Analog device such as OPAMP can be used to
    design a controller.

-   Controller was designed and successfully implemented on Multisim
    software. Earlier we discovered other simulation software too and
    found out multisim to be most useful.

-   Multisim provides a variety of features such as AC, DC analysis,
    transients, and real-time experience. Also, multisim processes data
    faster.

References
----------

1.  <https://www.omega.co.uk/prodinfo/pid-controllers.html> for
    abstract.

2.  <https://www.incatools.com/pid-tuning/pid-tuning-methods/#:~:text=Trial%20and%20error%20PID%20tuning%20method&text=Usually%20you%20start%20from%20an,the%20speed%20of%20the%20response.>
    for pid parameter tuning.

3.  Book by Roy Choudhari for applications of opamp


