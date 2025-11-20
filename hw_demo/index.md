---
title: Real-World Demonstration
layout: home
nav_order: 3
---

# Description

We demonstrate requiem on real drone hardware evaluated on the following missions: Linear and Hold.

# Specifications

## Hardware 
- CubePilot Orange+
  - ARM Cortex M7 (Dual Core) 400MHz
  - 1MB of RAM
  - PX4 Autopilot v1.15.4
- DJI F450 quadrotor frame
- Four 780kv motor
- Vicon Valkyrie


<!-- ## Setup -->


<!-- ![setup_diagram](/figures/av_diagram.png)

[popen]: https://docs.python.org/3/library/subprocess.html -->

# Demonstrations
<!-- 
For each demonstration, we consider the following trajectories
- Planned trajectory: Ideal mission trajectory (black line)
- Normal trajectory: Trajectory of the vehicle when there are no attacks (blue line)
- Attack Trajectory: True trajectory of the vehicle while under attack (red line)
- System POV Trajectory: Trajectory the system believes to have taken while under attack (dashed green line)
- Overt Trajectory: Attack trajectory after anomaly detector alarms (dashed red line)

A black `X` mark indicates that the attack triggered an anomaly detector,

<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/demo.mp4" type="video/mp4">
</video> -->


## Linear

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/HW_Demo_Linear_Normal.mp4" type="video/mp4">
</video>
### <span style="font-variant:small-caps;">Requiem</span>: No Correction 
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/HW_Demo_Linear_Requiem.mp4" type="video/mp4">
</video>

### Naive: Position Boiling Frog
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<<<<<<< HEAD
<source src="/videos/Linear/HW_Demo_Linear_PBF.mp4" type="video/mp4">
</video>

## Hold

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/HW_Demo_Hold_Normal.mp4" type="video/mp4">
</video>
### <span style="font-variant:small-caps;">Requiem</span>: No Correction 
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/HW_Demo_Hold_Requiem.mp4" type="video/mp4">
</video>

### Naive: Position Boiling Frog
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<<<<<<< HEAD
<source src="/videos/Hold/HW_Demo_Hold_PBF.mp4" type="video/mp4">
</video>


## Circle

### Normal
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Hold/HW_Demo_Circle_Normal.webm" type="video/webm">
</video>

Due to space constraints of the flying arena and safety considerations, we only evaluate attacks for linear and hold mission in hardware; circular movements are difficult to execute safely as it is challenging to predict whether the quadrotor will collide with the net.