---
layout: default
title: Query Server and Attack Vector Implementation Detail
parent: FAQ
nav_order: 2
---


# Query Server Implementation Detail

To query the target function without running other components in the system and to simultaneously preserve the blackbox aspect, we isolated the state update code.
When the input is provided in JSON, the result is also sent back to the client JSON after the function is executed.

# Attack Vector Implementation Detail

The objective of the attack vector is to perform man-in-the-middle (MitM) before the execution of the update function.
It exfiltrates the necessary data and inject values into the sensor that are used as input for the update.
It can be achieved by scanning the memory for the input variables for exfiltration and manipulating the memory reponsible for the sensor values.
<!-- To simplify the implementation while preserving the blackbox aspect of the attack, exfiltration and sensor value injection code are -->
To preserve essence of the attack (e.g., the blackbox perspective) and to avoid potential implementation bugs, we reuse the code in the query server implementation for exfiltration.
The exfiltration code is placed before the execution of the update function, resulting in <span style="font-variant:small-caps;">Requiem</span> being **oblivious** of the state update implementation (i.e., the target function). 
Attack server sends an array of values to inject.
The data is exchanged using `mmap` and TCP packets.

## Exfiltration

Exfiltration encodes 2020 variable values of the EKF object as a JSON.
The exact names of the variables are specified in `indexToName.json` in the source code [repository][repo].
By observing which variables changed over a period of mission, the number of variables needed can be narrowed down to only 52 out of 2020.
The 52 variables are


[repo]: https://github.com/projrequiem/requiem

## Communication to the Attack Server

The exfiltration encodes the JSON into a string which is written to using `mmap` on a file descriptor.
TCP packects are used for synchonization, signaling to the attack server that the data have finished writing to the `mmap`.
The attack server recieves the TCP and reads the `mmap`.
The server parses the string into a JSON which is then filtered and serialized into an array of length 52.