# Sample Code

## Incremental Joint Movement

The code provided below moves a selected joint incrementally.

**Note 1:** Before running the code make sure your calibration directory and config information are correct.

**Note 2:** disable_torque_on_disconnect allows to either keep the final joint positions (False) or release the joint locks (True)

```python
import time
from copy import deepcopy
from pathlib import Path
from lerobot.robots.so_follower import SO101Follower, SO101FollowerConfig

calibration_dir = Path(
    "~/.cache/huggingface/lerobot/calibration/robots/so_follower/"
).expanduser()
cfg = SO101FollowerConfig(
    id="cool1",
    port="/dev/ttyACM0",
    calibration_dir=calibration_dir,
    disable_torque_on_disconnect=True,  # True to release joints after disconnect, False to keep locks
)
robot = SO101Follower(cfg)

print("Connecting ...")
if not robot.is_connected:
    robot.connect()
    # obs = robot.get_observation()
    # print(obs.keys())
print(f"status: {robot.is_connected}")
# dict_keys(['shoulder_pan.pos', 'shoulder_lift.pos', 'elbow_flex.pos', 'wrist_flex.pos', 'wrist_roll.pos', 'gripper.pos'])

joint1_key = "shoulder_pan.pos"
joint2_key = "shoulder_lift.pos"
joint3_key = "elbow_flex.pos"
joint4_key = "wrist_flex.pos"
joint5_key = "wrist_roll.pos"
joint6_key = "gripper.pos"
joint_key = joint3_key
try:
    for _ in range(10):
        obs = robot.get_observation()
        obs_ = deepcopy(obs)
        obs_[joint_key] += 2.0
        print(f"sensor value: {obs[joint_key]}")
        print(f"desired value: {obs_[joint_key]}")
        robot.send_action(obs_)
        time.sleep(0.5)
finally:
    print("Disconnecting ...")
    try:
        robot.disconnect()
    except Exception as e:
        print(f"disconnect warning: {e}")

```


