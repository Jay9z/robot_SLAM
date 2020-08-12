Robot SLAM


## Introduction

a robot with RGBD camera and lidar, which can generate map during robot movement.

## Pre-requisites
1. ROS-kinectic

## Install
step 1. install a package of robot and world configuration

    mkdir -p <workspace_name>/src
    cd <workspace_name>/src
    catkin_init_workspace
    git clone https://github.com/Jay9z/robot_SLAM.git code
    mv code/* ./
    cd ..
    catkin_make


step 2. install RTAB package

    git clone -b devel https://github.com/introlab/rtabmap_ros.git src/rtabmap_ros
    mv src/mapping.launch src/rtabmap_ros/launch/
    catkin_make

step 3. install a package of robot teleop 

    git clone https://github.com/ros-teleop/teleop_twist_keyboard.git src/teleop_twist_keyboard
    mv src/mapping.launch src/teleop_twist_keyboard/
    catkin_make


## How to use it
Open a terminal

    cd <workspace_name>
    source devel/setup.bash
    roslaunch my_robot world.launch

Open the second terminal

    cd <workspace_name>
    source devel/setup.bash
    roslaunch rtabmap_ros mapping.launch

Open the third terminal

    cd <workspace_name>
    source devel/setup.bash
    rosrun teleop_twist_keyboard teleop_twist_keyboard.py


## Test it

1. Use keyboard to manipulate robot around simulation enviornment
2. Evaluate map with rtabmap-databaseViewer 