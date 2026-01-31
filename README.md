# camera-only Ackermann vehicle with visual marker (AprilTag) localization

This project aims to build a robot equipped with **only a camera** that performs **localization using visual markers** such as [AprilTag](https://april.eecs.umich.edu/software/apriltag). The robotic stack is ROS2 Jazzy & Gazebo Harmonic and works out of the box in a docker container built with the provided Dockerfile.<br>

**Note:** This work is still in progress.

---
![gazebo-rviz-acker-drive](assets/gazebo-rviz-acker-drive.gif)

---

**Note:** This repository uses the [ros2-jazzy-gazebo-harmonic-ackermann-drive](https://github.com/BBO-repo/ros2-jazzy-gazebo-harmonic-ackermann-drive) repository for the basic Ackermann drive vehicle simulation.

---

To run the Gazebo Rviz demo, log into the docker container built with the `Dockerfile` and run:
```sh
cd /workspace
colcon build --symlink-install
source install/setup.bash
ros2 launch mbpose-bringup mbpose-spawn.launch.py
```
Note: To move the robot, make sure Gazebo is running by pressing the play button in Gazebo opened GUI.<br>

In a terminal inside the container, just run:
```sh
gz topic -t "/cmd_vel" -m gz.msgs.Twist -p "linear: {x: 0.5}, angular: {z: 0.05}"
```

Note: You could also send messages directly from ros2:
```sh
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.5, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.1}}"
```