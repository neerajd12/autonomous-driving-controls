## Effect of PID parameters

#### P - Proportional gain(kp)
This tells us the change in output based on change in error. Which is used to correct the output based on errors as they happen. A larger number will have more effect which means quicker correction may lead to overshooting. This problem is solved by "D" parameter.

#### D - Derivative gain(Kd)
This tells us how much the output should be updated based on the change in direction of error. This helps reducing the overshoots because it allows the loop to anticipate overshoots as they begin to happen and react quickly.

#### I - Integral gain(Ki)
This tells us how much the output should be updated over time due to the error irrespective of it's direction. This helps removing errors due to process values/vehicle problems/process noise. Larger number will have more effect which means high values can infect add more noise instead of removing it.

## Tuning Process

Tuning is mostly done manually and mainly using the resources from
https://robotics.stackexchange.com/questions/167/what-are-good-strategies-for-tuning-pid-loops
https://en.wikipedia.org/wiki/Ziegler–Nichols_method

1. Set all the values to 0 and tested. The car went straight.
2. Increased Kp until the overshooting was reasonably constant.
3. Increased Kd Until the car was able to drive properly.
4. Increased Ki to reduce the process noise. Increasing it too much adds more noise and reduces the performance. so kept it at the highest value that gave reasonable performance.

* Uncomment the init values in code to see the effects of different combinations.