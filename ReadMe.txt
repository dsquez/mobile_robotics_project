This repository contains the code for the mobile robotics project I worked on with Brenden Richman
during the Fall 2020 semester.

Setup
This works on ros melodic and Ubuntu 18.04

Make sure you have all the right packages
sudo apt-get install ros-melodic-husky-navigation \
ros-melodic-husky-gazebo \
ros-melodic-husky-viz \
ros-melodic-global-planner \
ros-melodic-navfn \
ros-melodic-carrot-planner \
ros-melodic-map-server

create a catkin workspace
mkdir catkin_ws
cd catkin_ws
mkdir src
cd src

Clone the repository
git clone https://github.com/dsquez/mobile_robotics_project.git

Process for collecting and saving maps
in a terminal, run
roslaunch husky_gazebo husky_playpen.launch

in another terminal:
roslaunch husky_viz view_robot.launch

in another terminal
roslaunch husky_navigation gmapping_demo.launch

in the rviz window, use the 2D Nav Goal button to drive the robot around and create a map

when the map is done, open another terminal to save the map
rosrun map_server map_saver -f mymap

Process for testing the maps
in a terminal, run
roslaunch husky_gazebo husky_playpen.launch

in another terminal:
roslaunch husky_viz view_robot.launch

in another terminal
source catkin_ws/devel/setup.bash
roslaunch mobile_robotics_project amcl_project.launch

in another terminal
cd src/mobile_robotics_project/scripts

run each script in turn, waiting for the robot to reach the waypoint
./publish_waypoint1.sh
./publish_waypoint2.sh
./publish_waypoint3.sh
./publish_end.sh

When the robot is done, record its position from the gazebo gui.