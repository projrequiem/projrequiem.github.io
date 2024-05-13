---
title: Missions
layout: home
nav_order: 2
---

# Missions

The paper presents three types of missions:
- Circle
- Linear
- Hold

Each mission was carried out in the simulation using [`Python-MAVSDK`][mavsdk].
Specifically, the UAV was commanded in `offboard-control` mode that gives the mission planning to the python script.
It controls the UAV "on-the-spot" as opposed to pre-loading the mission to the flight controller before the deployment.start of the 
The script can subscribe to the UAV's state (e.g., position and velocity) to make the mission decisions online.
All three missions occur at `10m` altitude.
The vehicle's mission start after a "warm-up" movement so that the vehicle parameters are tuned to the movement, keeping the nominal residual low.

# Circle

Circle mission use `Vel` command, which only tries to match the forward and angular velocity to `5m/s` and `30deg/s` respectively.
Meaning, it does not guarentee the position the vehicle would have been if it moved with such velocity.
Hence, the planned mission it represents is a circle with `9.59m` radius centered about a meter from the origin.
The mission officially starts after 3 seconds of the motion from the origin (i.e., the warm-up), hence the mission trajectory starts away from the origin.

The planned trajectory is shown as a black circle. A nominal run of the mission (i.e., without any attacks) is shown in blue in the following video:
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/figures/circle/normal.mp4" type="video/mp4">
</video>

# Linear 

Linear mission requires converging to the setpoints.
The setpoint convergence function is located in the [`mission.py`][mission_py].
The vehicle is considered converged if it reaches a distance within `0.3m` and the convergence is checked every second.
Linear mission consists of three convergence points: (10m east, 0m north), (10m east, 10m north) and back to the origin (0m east, 0m north).
Prior to the start of the mission, the vehicle moves to (10m east, 10m north) and back to the origin as a warm-up.

The planned trajectory is shown as a black triangle. A trajectory of the mission without any adversarial influence is shwon in blue.
<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/figures/linear/normal.mp4" type="video/mp4">
</video>

# Hold

In hold mission, convergence setpoint is only set to the origin.
The mission officially starts 3 seconds after converging to the origin.

In this mission, the ideal trajectory would be for the UAV to remain within `0.25m` from the origin.
Therefore, the planned trajectory is represented as a black circle with `0.25m` radius and the normal trajectory shown as a blue line.


<video controls="" width="640" height="360" muted="" loop="" autoplay="">
<source src="/figures/hold/normal.mp4" type="video/mp4">
</video>

[mavsdk]: https://github.com/mavlink/MAVSDK-Python
[mission_py]: https://github.com/projrequiem/requiem
