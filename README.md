# MiniRos: an autonomous UGV robot for educationand research

![MiniROS 3D design](https://github.com/TriKnight/miniros/blob/master/figures/minibot_3.png)

## I. Installation

Step 1. Install Ubuntu 18.04 and  [ROS Melodic!](http://wiki.ros.org/melodic/Installation/Ubuntu)

Step 2. Following [ROS Tutorial](http://wiki.ros.org/ROS/Tutorials) and create **catkin_ws**

Step 3. Git clone Miniros and some repos:

```
cd ~/catkin_ws/src
git clone https://github.com/TriKnight/miniros/
git clone https://github.com/ros-teleop/teleop_twist_keyboard
```

Step 4. Install all ROS dependences

```
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make
```
Step 5. Running Miniros empty world gazebo enviroments 

```
roslaunch miniros_gazebo miniros_world.launch
```
![Minibot in world](https://github.com/TriKnight/miniros/blob/master/figures/Screen%20Shot%202021-05-06%20at%2010.45.39%20PM.png)
Then open the new terminal
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
# Usage keyboard to moving the robot
```
Reading from the keyboard  and Publishing to Twist!
---------------------------
Moving around:
   u    i    o
   j    k    l
   m    ,    .

For Holonomic mode (strafing), hold down the shift key:
---------------------------
   U    I    O
   J    K    L
   M    <    >

t : up (+z)
b : down (-z)

anything else : stop

q/z : increase/decrease max speeds by 10%
w/x : increase/decrease only linear speed by 10%
e/c : increase/decrease only angular speed by 10%

CTRL-C to quit
```
## II. Running SLAM GMapping
[![MiniROS running SLAM](https://j.gifs.com/GRnOr7.gif)](https://www.youtube.com/watch?v=ZCQJhtsWnWg)
### 1. Running Miniros Gazebo Enviroment
```
roslaunch miniros_gazebo miniros_cpr_construction.launch 
```
### 2. Running teleop_keyboard
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py 

```
### 3. Running SLAM Gmapping
```
roslaunch miniros_navigation gmapping.launch 
```
### 4. Open Rviz enviroment

```
roslaunch miniros_description miniros_rviz.launch 

```
### 5. Saving the map
Launch the map_saver node in the map_server package to create map files.
The map file is saved in the directory where the map_saver node is launched at.
```
rosrun map_server map_saver -f ~/map
```

