Move_robot_Project

This project simulates the way a robot works discovers its environment in Gazebo while creating it as a map using SLAM .This is done using Ros in ubuntu 16.04. and with robots from Turtlebot (https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/).

1-Quick Start Guide..

-PC Setup

Install ROS on Remote PC:

$ sudo apt-get update

$ sudo apt-get upgrade

$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh

$ chmod 755 ./install_ros_kinetic.sh

$ bash ./install_ros_kinetic.sh

Install Dependent ROS Packages:

$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy \ ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc \ ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan \ ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python \ ros-kinetic-rosserial-server ros-kinetic-rosserial-client \ ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server \ ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro \ ros-kinetic-compressed-image-transport ros-kinetic-rqt* \ ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers
Install TurtleBot3 Packages

$ sudo apt-get install ros-kinetic-dynamixel-sdk $ sudo apt-get install ros-kinetic-turtlebot3-msgs $ sudo apt-get install ros-kinetic-turtlebot3

Set TurtleBot3 Model Name choose the Trutlebot3 you want to work with:

In case of TurtleBot3 Burger

$ echo "export TURTLEBOT3_MODEL=burger" >> /.bashrc
In case of TurtleBot3 Waffle Pi

$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> /.bashrc

Network Configuration

1 Connect PC to a WiFi device and find the assigned IP address with the command below.

$ ifconfig

2 Open the file and update the ROS IP settings with the command below.

$ nano /.bashrc

3 Source the bashrc with below command.

$ source /.bashrc

2-Simulation

-Gazebo Simulation

Install Simulation Package

$ cd /catkin_ws/src/

$ git clone -b kinetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git

$ cd /catkin_ws && catkin_make

Launch Simulation World

There are 3 simulation environments prepared for TurtleBot3, you can select any one of these environments to launch Gazebo: 1-Empty World

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch

![2021-07-12](https://user-images.githubusercontent.com/86461558/125236244-4ef88080-e2ec-11eb-9405-965028bf86b0.png)

2-TurtleBot3 World

$ export TURTLEBOT3_MODEL=waffle

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

![Screenshot from 2021-07-11 06-34-17](https://user-images.githubusercontent.com/86461558/125236387-8a934a80-e2ec-11eb-84c3-7ea0906fa076.png)

3-TurtleBot3 House

$ export TURTLEBOT3_MODEL=waffle_pi

$ roslaunch turtlebot3_gazebo turtlebot3_house.launch

SLAM Simulation

-Launch Simulation World

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

![Screenshot from 2021-07-11 06-34-17](https://user-images.githubusercontent.com/86461558/125236387-8a934a80-e2ec-11eb-84c3-7ea0906fa076.png)

-Run SLAM Node

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

-Run Teleoperation Node

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

-Save Map

$ rosrun map_server map_saver -f /map
