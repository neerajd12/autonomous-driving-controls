## The Model

The model state vector has 6 components viz. x, y positions, orientation, velocity, cross track error which is the error between the center of the road and the vehicle's position and orientation error which is the difference between car trajectory and expected trajectory.

The actuator vector consist of two values the steering angle "delta" and the throttle/acceleration "a".

Equations used to update the state

* Vt+1 = Vt + a * dt
* PSIt+1 = PSIt + V * delta * dt / Lf
* Xt+1 = Xt + V * cos(PSI) * dt
* Yt+1 = Yt + V * sin(PSI) * dt
* EPSIt+1 = EPSIt + V * delta * dt /Lf
* CTEt+1 = CTEt + V * sin(EPSI) * dt

## Timestep Length and Elapsed Duration (N & dt)

Both N & dt were manually tuned along with the reference velocity which affects these and the final values chosen for Timestep Length (N) is 20 and and Elapsed Duration(dt) is (0.05). These values gave the best results while going fastest.

* Started by keeping dt=0.05 and N=10 with this value the car runs of the track even before the model can do anything. It has to little control inputs to reduce cross track error.
* Next started increasing "N" in steps of 5 until 30 which caused the model to try to predict longer distance on track. The predicted trajectory appeared to going over the next turn and over adjusting, adding the error causing the car to slide and go off the track. So reduced it back to 20.
* Next tested with higher values of dt like 0.075 and 0.1. Increasing dt caused the predictions to be too fast with too little actuations, causing it to add more error to the predicted trajectory since the distance between successive points is too much to reduce the error properly. Causing the car to go off the track.
 
 Apart from "N" and "dt", reference velocity, and cost of use of actuators has quite an impact on the stability. As expected going slowly makes the turns more stable.
 
## Handling a 100 millisecond latency.
To handle the latency I averaged the last 5 actuations. why 5 ? Because I get 5 if I multiple "dt"(which is the time between each actuation) to the latency "100" and it made the car quite stable. 