---
title: Real-World Demonstration
layout: home
nav_order: 3
---

# Description

We demonstrate requiem on real drone hardware evaluated on the following missions: Linear and Hold.
The following scenarios are considered:
- Normal - A mission without any attacks
- <span style="font-variant:small-caps;">Requiem</span>: No Correction - an attack that prevents the control from correcting north position value by injecting values to the mocap (i.e., Vicon) north position value while making the north position value seem nominal.
- Naive: Position Boiling Frog - slowly increase the value injected into mocap north position value at the rate of 1m/min (e.g., after 30 seconds of this attack, the magnitude of the injection is 0.5m )

# Specifications

## Hardware 
- CubePilot Orange+
  - ARM Cortex M7 (Dual Core) 400MHz
  - 1MB of RAM
  - PX4 Autopilot v1.15.4
- DJI F450 quadrotor frame
- Four 780kv motor
- Vicon Valkyrie

# Demonstrations

## Linear

After the takeoff, the vehicle moves to (1m, 0m), (1m, 1m) then back to (0m, 0m) from the starting point in east-north coordinate.
A right isosceles traingle with 1m sides is taped on to the floor for visual reference.

### Normal
The drone moves along the triangle as expected.
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/HW_Demo_Linear_Normal.mp4" type="video/mp4">
</video>

### <span style="font-variant:small-caps;">Requiem</span>: No Correction 
The result is reflective of the simulation experiment: <span style="font-variant:small-caps;">Requiem</span> causes the most deviation during the northward movement by causing the control to unable to notice that the vehicle overshot while remaining stealthy.
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/videos/Linear/HW_Demo_Linear_Requiem.mp4" type="video/mp4">
</video>

### Naive: Position Boiling Frog
Similar to the simulation result, PBF did not cause much deviation. 
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
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
<source src="/videos/Hold/HW_Demo_Hold_PBF.mp4" type="video/mp4">
</video>


## Circle

### Normal
<video controls="" width="640" height="360" muted loop="" autoplay="">
<source src="/videos/Circle/HW_Demo_Circle_Normal.webm" type="video/webm">
</video>

Due to space constraints of the flying arena and safety considerations, we only evaluate attacks for linear and hold mission in hardware; circular movements are difficult to execute safely as it is challenging to predict whether the quadrotor will collide with the net.