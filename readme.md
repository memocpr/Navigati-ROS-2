
# Section 4: Path Planning

## launch localization and mapping
```bash
sudo apt update
sudo apt install -y libserial-dev python3-rosdep
rosdep update
cd ~/Desktop/Navigati-ROS-2/Section4_Path_Planning/bumperbot_ws
rosdep install --from-paths src --ignore-src -r -y
```

```bash
cd ~/Desktop/Navigati-ROS-2/Section4_Path_Planning/bumperbot_ws
colcon build --symlink-install
. install/setup.bash
ros2 launch bumperbot_localization global_localization.launch.py
```
## open rviz
```bash
rviz2
```
add Map:
    set topic to /map
    Durability to TRANSIENT_LOCAL
    Reliability to RELIABLE

## see map info
```bash
ros2 topic info /map --verbose
```




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

## set lifecycle state
configure
```bash
ros2 lifecycle set /planner_server 1
```
activate
```bash
ros2 lifecycle set /planner_server 3
```


## check map info
```bash
ros2 topic info /map --verbose
```
and make sure map settings on rviz:
    Reliability: RELIABLE
    Durability: TRANSIENT_LOCAL


## lifecycle manager
```bash

