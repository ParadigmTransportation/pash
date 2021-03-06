# PASH

> Pod Bash

This is a set of bash scripts that are used for manually controlling the Pod
from an ssh session for **DEBUGGING AND TESTING PURPOSES ONLY**.

# Goals

The primary goal of PASH is to provide a controls environment that allows for
rapid iteration of various static controls strategies to enable fast
characterization of the rest of the pod's subsystems.

# Usage

PASH allows you to quickly develop scripts for controlling the pod.

To get started simply login to the core controller and type. You can do
anything you would otherwise do in Bash, in PASH

```
$ source setup
$ echo $PUSHER_PLATE_PIN # Verify it says 48
48

```

You can look at what commands are available by checking out the [bin](bin/)
folder of this repo.

* `brake <0|1>`: Get the state of the given clamp 0 - front, 1 - rear
* `brake <0|1> <0|1|2>`: Set the state of the clamp 0 - closed, 1 - engaged,
  2 - released
* `emergency`: Set all solenoids to their emergency positions
* `flight`: Runs a basic flight profile controlled by a timer and the pusher plate
* `hpfill <0|1>`: Set the state of the HP FIll Solenoid 0 - closed, 1 - open
* `lat <0|1>`: Get the state of the Lateral Fill Solenoid 0 - front, 1 - rear
* `lat <0|1> <0|1>`: Set the state of the Lateral Fill Solenoid (Closed|Open)
* `lpfill <0|1>`: Get the state of the LP Fill Solenoid
* `lpfill <0|1> <0|1>`: Set the state of the LP Fill Solenoid
* `off`: Turn all solenoids off (including the vent solenoid)
* `on`: Turn all solenoids on
* `poweroff`: Kill the main power board (Kills the BBB too)
* `skate <0|1|2>`:  Get the state of the Front, Mid, or Rear skate set
* `skate <0|1|2> <0|1>`: Set the state of the Front, Mid, or Rear skate set
* `skates <0|1>`: Set all skates to 0 - Off, 1 - On
* `vent <0|1>`: Set all vent solenoid state to **0 - Open, 1 - Closed**
* `wheel <0|1|2> <0|1>`: Set the state of the caliper brakes

Scripts can be easily written to control the pod like so

```
$ nano my_test

>> Enter
#!/bin/bash
skates 1
sleep 1
skates 0
>> Save and Exit

$ chmod +x my_test
# Note: Test your scripts before filling the pod
# Run your test by typing
$ ./my_test
```

# License

BSD 3-Clause License
