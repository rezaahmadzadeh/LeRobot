# Teleoperation

## Teleoperation without Camera

Teleoperation can be done using the following command:

```
lerobot-teleoperate --robot.type=so101_follower --robot.port=/dev/ttyACM1 --robot.id=cool1 --teleop.type=so101_leader --teleop.port=/dev/ttyACM0 --teleop.id=cool1leader
```

detail:
```bash
lerobot-teleoperate \
 --robot.type=so101_follower \
 --robot.port=/dev/ttyACM1 \
 --robot.id=cool1 \
 --teleop.type=so101_leader \
 --teleop.port=/dev/ttyACM0 \
 --teleop.id=cool1leader
```



## Important notes

**Note 1:** ensure both ports are connected with proper permission.

**Note 2:** the leader uses the `teleop` class while the follower uses the `robot` class. 

**Note 3:** when starting the teleoperation, the follower first moves to match the leader's configuration. If the follower's and leader's configurations are very different, the follower moves very quickly. So it would be best to have their configurations as close as possible.


## Teleoperation with Camera

With a camera installed, you can perform the teleoperation using the following command:
```
 lerobot-teleoperate --robot.type=so101_follower --robot.port=/dev/ttyACM1 --robot.id=cool1 --robot.cameras="{handeye: {type: opencv, index_or_path: 4, width: 640, height: 480, fps: 30}}" --teleop.type=so101_leader --teleop.port=/dev/ttyACM0 --teleop.id=cool1leader --display_data=true
```

detail:
```bash
lerobot-teleoperate \
 --robot.type=so101_follower \
 --robot.port=/dev/ttyACM1 \
 --robot.id=cool1 \
 --robot.cameras="{handeye: {type: opencv, index_or_path: 4, width: 640, height: 480, fps: 30}}" \
 --teleop.type=so101_leader \
 --teleop.port=/dev/ttyACM0 \
 --teleop.id=cool1leader \
 --display_data=true
```


**Note 4:** the camera information must be included as a json dict, which allows to include more than one camera.

**Note 5:** When using `--display_data=true` , the `rerun.io` program starts. 
