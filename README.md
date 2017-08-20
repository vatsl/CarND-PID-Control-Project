# CarND-Controls-PID

---

In this project I have tried to use my knowledge of Control Systems to implement a PID controller in C++ to maneuver the vehicle around the track!

The simulator will provide you the cross track error (CTE) and the velocity (mph) in order to compute the appropriate steering angle.

## Output

[![Final results with the implementation](http://img.youtube.com/vi/6xpuAsopwsA/0.jpg)](http://www.youtube.com/watch?v=6xpuAsopwsA)

## Parameter Selection
The error values for the P, I and D were chosen as follows:

**p_error** - chosen to be a very large value assuming the car starts far from the intended path

**i_error** - assume that the total sum of errors initially is extremely small as the car is yet to start

**d_error** - assume that the initial difference is small as the car is yet to start

**Initial P (Kp) - 0.150** - This parameter make the car move toward the CTE, by multiplying the CTE by P value.
The true value is never really achieved. It merely oscillates around it. 
I started with a value of 0.2 as given in the quiz. I then tweaked the value by increasing
it a bit and then decreasing it. Finally I stopped in 0.15 as there was not much difference in the driving behavior.

**Initial I (Ki) - 0.001** - This parameter compensates for the systematic bias, like a faulty alignment of the steering
wheel. It will accumulate the values of the errors and over time correct the car. I started with a value of 0.004 as 
given in the quiz. I then increased it to 0.01 and found that the car's oscillations increased. Therefor, I started
decreasing it gradually and found that 0.001 worked just fine.

**Initial D (Kd) - 2.5** - This parameter is for steering the car back to the course. It becomes smaller as the car 
drives towards the CTE. This avoids the over-shooting caused by the P controller alone. I started with a value
of 3.0 as given in the quiz. I increased it to 3.5 and found that the
result was not improving. I therefore experimented with decreasing it a bit and finally settled on 2.5.

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

## Code Style

[Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).
