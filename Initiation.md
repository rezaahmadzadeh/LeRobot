# Quick Start for LeRobot SO-ARM101

After setting up the robot and getting it connected to power and your computer through UCB, follow these steps:

1- get info: allows to check if the robot is detected as a device
lerobot-info

2- port finder (finding to which port the robot is connected to)
`lerobot-find-port`

after running, it first shows a list of ports, then asks the user to disconnect the USB cable from the computer to detect which port was activated/deactivated. It then returns the specific port and asks the user to reconnect. 

3- In most cases, the user needs to change the permission to avoid getting a permission denied error.

`sudo chmod 666 [port]`

example: `sudo chmod 666 /dev/ttyACM0`

4- calibration: before using the robot, it is necessary to perform the calibdation process.
`lerobot-calibrate [robot.type] [robot.port] [robot.id]`

example:
`lerobot-calibrate --robot.type=so101_follower --robot.port=/dev/ttyACM0 --robot.id=cool`

After running the command, first the user is asked to move all the joints to their mid point, and then the user is asked to move all the joints to their minimum and maximum values to be recorded by the robot. 
The resulting observations will be recorded in a table for the specific robot id under the  `.cache/huggingface/lerobot/calibdation/robots/so_follower/[robot.id].json`.


