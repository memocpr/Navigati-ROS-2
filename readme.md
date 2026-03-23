
# Section 7: Navigation

## launch the simulated robot
```bash
cd ~/Desktop/Navigati-ROS-2/Section7_Navigation/bumperbot_ws
colcon build --symlink-install
. install/setup.bash
ros2 launch bumperbot_bringup simulated_robot.launch.py world_name:=small_house
```

## launch the navigation stack
```bash
cd ~/Desktop/Navigati-ROS-2/Section7_Navigation/bumperbot_ws
. install/setup.bash
ros2 run nav2_planner planner_server --ros-args --params-file /home/evomrd/Desktop/Navigati-ROS-2/Section7_Navigation/bumperbot_ws/src/bumperbot_navigation/config/planner_server.yaml
```

## set lifecycle state to active
```bash
ros2 lifecycle set /planner_server 1
```