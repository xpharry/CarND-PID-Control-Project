# Writeup

## Compilation

Environment: macOS v10.13.1, cmake v3.9.4, make v3.81

Your code should compile.

The code compiles without errors or warnings. No modifications were done on the provided setup.

```
mkdir build && cd build
cmake .. && make
```

Then each time when we modify the code, we only do `make` under "build" directory.

## Implementation

The PID procedure follows what was taught in the lessons.

The PID implementation is done on the ./src/PID.cpp. The PID::UpdateError method calculates proportional, integral and derivative errors and the PID::TotalError calculates the total error using the appropriate coefficients.

1) Start the Udacity simulator.

2) Start PID Controller,

```
./pid
```

## Reflection

Describe the effect each of the P, I, D components had in your implementation.

The proportional portion of the controller tries to steer the car toward the center line (against the cross-track error).

The integral portion tries to eliminate a possible bias on the controlled system that could prevent the error to be eliminated.

The differential portion helps to counteract the proportional trend to overshoot the center line by smoothing the approach to it.

Describe how the final hyperparameters were chosen.

The parameters were chosen manually by try and error. First, make sure the car can drive straight with zero as parameters. Then add the proportional and the car start going on following the road but it starts overshooting go out of it. Then add the differential to try to overcome the overshooting. The integral part only moved the car out of the road; so, it stayed as zero. After the car drove the track without going out of it, the parameters increased to minimize the average cross-track error on a single track lap. The final parameters where [P: 1.5, I: 0.0, D: 2.5].

## Simulation

The vehicle must successfully drive a lap around the track.