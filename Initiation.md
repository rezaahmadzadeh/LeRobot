# Quick Start for LeRobot SO-ARM101

After setting up the robot and getting it connected to power and your computer through USB, follow these steps:

### 1. Get info 
Allows to check if the robot is detected as a device

```
lerobot-info
```

### 2. Find ports
This port finder (finding to which port the robot is connected to) allows you to pint-point which port your robot is using
```
lerobot-find-port
```

after running, it first shows a list of ports, then asks the user to disconnect the USB cable from the computer to detect which port was activated/deactivated. It then returns the specific port and asks the user to reconnect. 

### 3. Permission
In most cases, the user needs to change the permission to avoid getting a permission denied error.

```
sudo chmod 666 [port]
```

example: 
```
sudo chmod 666 /dev/ttyACM0
```

### 4. calibration 
Before using the robot, it is necessary to perform the calibdation process.

```
lerobot-calibrate [robot.type] [robot.port] [robot.id]
```

example:

```
lerobot-calibrate --robot.type=so101_follower --robot.port=/dev/ttyACM0 --robot.id=cool
```

After running the command, first the user is asked to move all the joints to their mid point, and then the user is asked to move all the joints to their minimum and maximum values to be recorded by the robot. 
The resulting observations will be recorded in a table for the specific robot id under the  `.cache/huggingface/lerobot/calibdation/robots/so_follower/[robot.id].json`.

Note that the leader should be calibrated similarly. However, the leader uses the `teleop` class instead of the `robot` class as 
```
lerobot-calibrate [teleop.type] [teleop.port] [teleop.id]
```


example:

```
lerobot-calibrate --teleop.type=so101_leader --teleop.port=/dev/ttyACM1 --teleop.id=cool_leader
```
The calibration file is recorded and stored in the following directory by default `.cache/huggingface/lerobot/calibdation/teleoperators/so_leader/[teleop.id].json`.

### 5. Camera detection
If you have a camera attached, you can find the camera index by running

```lerobot-find-camera```

If this is an OpenCV camera, you can also specify


```lerobot-find-camera opencv```




