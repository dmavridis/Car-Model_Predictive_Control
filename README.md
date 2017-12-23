# Project 5 report
The following requirements are answered in this document. 

## Compilation
### Your code should compile.
__Code must compile without errors with cmake and make__

Code compliles succesfully

## Implementation
### The Model
__Student describes their model in detail. This includes the state, actuators and update equations.__

State, actuators and update equation are implemeneted into the code. The followed steps can be summarized as:

- Transformation of global coordinates of the path track to coordinates relative to car's x,y and psi values. This approach is facilitating the calculations.
- Polynomial fitting of the transformed track points
- cte and epsi calculations
- MPC solution


### Timestep Length and Elapsed Duration (N & dt)
__Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. 
Additionally the student details the previous values tried__

The chosen N and dt values are 10 and 0.1 respectively. For the choice there are tradeoffs. Large N and small dt are favourable at the expense of increased computanional cost. However, there is no point in increasing N too much as the information in the further future is less important.


### Polynomial Fitting and MPC Preprocessing
__A polynomial is fitted to waypoints.__

A 3rd order polynomial fit is applied. That value for the order is a good compromise between  accuracy for the prediction without getting in too much complexity and possibly overfitting.

The points for the fitting function are the transformed track points relative to the car's currnet position and angle.

### Model Predictive Control with Latency
__The student implements Model Predictive Control that handles a 100 millisecond latency. 
Student provides details on how they deal with latency.__

Latency is taken into account by using the actuator values that are predicted not for the current moment but for a future moment equal to the latency value. That's the reason the solution return the values at one time step in the future.


## Simulation
### The vehicle must successfully drive a lap around the track.

__No tire may leave the drivable portion of the track surface. The car may not pop up onto ledges or roll over any surfaces that would otherwise be considered unsafe (if humans were in the vehicle).__

The car is driving safely around the track. A reference speed of 80mph is applied. 