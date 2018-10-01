# **CarND-PID-Control**
Self-Driving Car Engineer Nanodegree Program

---

**PID-Control Project**

The goals / steps of this project are the following:
* Implement a PID Controller to control the steering of a car in the simulator
* Tune the controler to drive the car in the circular lane at a reasonable velocity
* Write a report to summarize the process and result


## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/824/view) individually and describe how I addressed each point in my implementation.  

---
### Compilation

#### 1. Code must compile without errors with `cmake` and `make`.

The project includes the following source files in src folder:
* PID.h : Header file for the PID Controller class
* PID.cpp : Source file for the PID Controller class
* json.hpp : Library for handling json
* main.cpp : Main source file containig the main loop

After I updated the source files, I compiled with `cmake` and `make`,  without errors.

### Implementation

#### 1. The PID procedure follows what was taught in the lessons.

My PID Controller follows what was taught in the lessons.

### Reflection

#### 1. Describe the effect each of the P, I, D components had in your implementation.

* __P (Proportion)__ - The P component is for the proportional part of the Controller. It describes how strong the controller reacts on being off the track. It is proportionaly responeded to the current error.
* __I (Integration)__ - The I component is for the integral part of the Controller. It sums up when vehicle is off track for a longer time and produces a stronger reaction in this case.
* __D (Differentiation)__ - The D component is for the differential part of the Controller. This part should slow down the reaction when the change in error is high, so that the vehicle will not overshoot the target too much.

#### 2. Describe how the final hyperparameters were chosen.

I did it by manual tuning. I started with [1.0, 0.0, 0.0].
First I adjusted the proportional part for some tines till the car reacts not too slow and not too fast. The car still roll out the road cources and stack in the field, but that was over several seconds later. I set kp=0.1.
Then, I adjusted the differential part till the car stops overshooting in the center of the lane. After testing for several times， I set kd=2.0.
Finally,  to make approach accumulattion steering bias as the time goes，I added a tiny bit of integral coefficient to improve performance. I set ki=0.0001.
So the final hyperparameters I chose is [0.1, 0.0001, 2.0].

### Simulation

#### 1. The vehicle must successfully drive a lap around the track.

The vehicle drives successfully a lap around the track on my computer.
