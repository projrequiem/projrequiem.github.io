---
title: Attack Types
layout: home
nav_order: 2
---

# Attack Types

We target north position and velocity values of the GPS and we consider two types of attacks: <span style="font-variant:small-caps;">Requiem</span> and Naive.
<span style="font-variant:small-caps;">Requiem</span> is our proposed attack that use surrogate models and GAN training to spoof the sensor values.
Naive attacks are a set of simple spoofing strategies that serves as a baseline in the comparison.

## <span style="font-variant:small-caps;">Requiem</span>

### No Correction (NC)

Sensors do not influence the state estimation, resulting in a dead-reckoning like trajectory.
The spoofer is trained to minimize the residual by spoofing the north position and north velocity values of GPS.

### Direction Bias (DB)

The vehicle moves towards the direction of the *adversary's choosing*.
Spoofer trades off between some residual for more deviation but still remains stealthy.


## Naive

Attack strategies in the naive class of attacks is static (i.e., does not change based on the state of the vehicle).
A constant offset attack injects a constant value into  the sensor value.
Random offset samples a random value to inject into  the target sensor value.
Boiling frog slowly increase the magnitude of the injection over time.
We target either the GPS north position or the north velocity values resulting in a total of 6 types of naive attacks against the GPS:
- Position Constant Offset (PCO)
- Position Random Offset (PRO)
- Position Boiling Frog (PBF)
- Velocity Constant Offset (VCO)
- Velocity Random Offset (VRO)
- Velocity Boiling Frog (VBF)

# Results


| Metric ID (MID) | Description |
|------|-------|
| M1 | Determines if the attack triggered the onboard/default (i.e., chi-squared) alarm|
| M2 | Maximum stealthy deviation under the default alarm in meters |
| M3 | Checks if the *tau* anomaly detector raised an alarm|
| M4 | Maximum stealthy achieved under *tau* anoamly detector|

![results](/figures/results.png)