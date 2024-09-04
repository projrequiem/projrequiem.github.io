---
title: Demonstration
layout: home
nav_order: 3
---

# Description

We demonstrate the attack on the three missions: Circle, Linear, and Hold.

# Specifications

## Hardware 

Intel i5 6500 quad core, Ubuntu 22.04, 16GB RAM, AMD Radeon Vega 20 GPU.

## Simulation

PX4 Software-In-The-Loop (SITL) with Gazebo.
The world is set to [`empty.world`][empty_world] where there are no obstacles and weather conditions such as wind or rain, only a flat land.
Vehicle type is set to [`default`][iris]: a quadrotor without any cameras.
To run the SITL simulation with such configuration, run `make px4_sitl gazebo` at the root of the PX4 directory.

[empty_world]: https://github.com/PX4/PX4-SITL_gazebo-classic/blob/main/worlds/empty.world
[iris]: https://docs.px4.io/v1.12/en/simulation/gazebo_vehicles.html#quadrotor

## Setup

A python script handles the launch of the simulator, serves as a ground control station (i.e., issue commands to the vehicle), and the attack server.

1. it executes the simulation as a subprocess (via [`popen`][popen]) and waits for the quadrotor in simulation to be ready (i.e., establish TCP connection with the exfiltrator).
1. Once the quadrotor is ready, the script sends the take-off command.
1. After takeoff, the script sends mission commands 
 - In parallel, the attack starts
1. The data collected throughout the mission is written to the disk
1. The collected data is played back for demonstration.

![setup_diagram](/figures/av_diagram.png)

[popen]: https://docs.python.org/3/library/subprocess.html

# Demonstrations

For each demonstration, we consider the following trajectories
- Planned trajectory: Ideal mission trajectory (black line)
- Normal trajectory: Trajectory of the vehicle when there are no attacks (blue line)
- Attack Trajectory: True trajectory of the vehicle while under attack (red line)
- System POV Trajectory: Trajectory the system believes to have taken while under attack (dashed green line)
- Overt Trajectory: Attack trajectory after anomaly detector alarms (dashed red line)

A black `X` mark indicates that the attack triggered an anomaly detector,

<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/demo.mp4" type="video/mp4">
</video>

## Circle

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Circle/Requiem_Demo_Circle_Normal.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: Direction Bias
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Circle/Requiem_Demo_Circle_DB.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: No Correction
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Circle/Requiem_Demo_Circle_NC.mp4" type="video/mp4">
</video>

### Naive: Position Boiling Frog
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Circle/Requiem_Demo_Circle_PBF.mp4" type="video/mp4">
</video>

## Linear

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/Requiem_Demo_Linear_Normal.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: Direction Bias
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/Requiem_Demo_Linear_DB.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: No Correction 
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/Requiem_Demo_Linear_NC.mp4" type="video/mp4">
</video>

### Naive: Position Boiling Frog
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/Requiem_Demo_Linear_PBF.mp4" type="video/mp4">
</video>

## Hold

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Hold_Normal.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: Direction Bias
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Hold_DB.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: No Correction
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Hold_NC.mp4" type="video/mp4">
</video>

### Naive: Position Boiling Frog
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Hold_PBF.mp4" type="video/mp4">
</video>

## Windy Circle

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Windy_North_Circle_Normal.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: No Correction
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Windy_North_Circle_NC.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: Direction Bias
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/Requiem_Demo_Windy_North_Circle_DB.mp4" type="video/mp4">
</video>