# Gathering Demonstrations

When both the follower, the leader, and the handeye camera is connected, the following command can be used to record multiple demonstrations

```bash
lerobot-record --robot.type=so101_follower --robot.port=/dev/ttyACM1 --robot.id=cool1 --robot.cameras="{handeye: {type: opencv, index_or_path: 4, width: 640, height: 480, fps: 30}}" --teleop.type=so101_leader --teleop.port=/dev/ttyACM0 --teleop.id=cool1leader --dataset.repo_id=test/so101_demo --dataset.single_task="test recording" --dataset.num_episodes=1 --dataset.episode_time_s=20 --dataset.reset_time_s=5 --dataset.push_to_hub=false --display_data=true
```

## Details
The `robot` class includes the follower information while the `teleop` class includes the leader configuration.
Since the handeye camera is connected to the follower, its configuration is included in the `robot` class.
The `dataset` class is used to store the robot and camera information during each episode. The `repo_id` points to the directory in which the data is sotred.
Note that every time you run this command, you either must provide a new directory or remove the current one. 

In the following example, we are interested in recording 1 demonstration for the fixed duration of 20sec and a wait time of 5sec. The `display_data=true` brings up the rerun.io app that shows the robot joints and camera observations.

```bash
lerobot-record \
  --robot.type=so101_follower\
  --robot.port=/dev/ttyACM1 \
  --robot.id=cool1 \
  --robot.cameras="{handeye: {type: opencv, index_or_path: 4, width: 640, height: 480, fps: 30}}" \
  --teleop.type=so101_leader \
  --teleop.port=/dev/ttyACM0 \
  --teleop.id=cool1leader \
  --dataset.repo_id=test/so101_demo \
  --dataset.single_task="test recording" \
  --dataset.num_episodes=1 \
  --dataset.episode_time_s=20 \
  --dataset.reset_time_s=5 \
  --dataset.push_to_hub=false \
  --display_data=true
```
