# WhereAmI
[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)


https://github.com/Mennatallah98/WhereAmI/assets/45118345/c7e48ad5-578f-4467-983c-c31747558c1f

## Overview

This project is the third project in Udacity Robotics Software Engineer nano degree where the world was mapped using [pgm_map_creator] and the robot navigated the world using [navigation_stack] where [amcl] was used for localization.

**Keywords:** ROS, amcl, navigation_stack, mapping, localization.

**Author: Mennatallah Aly<br />**

The WhereAmI package has been tested under [ROS] Melodic on Ubuntu 18.04. and Gazebo 9.0.0

## Installation

### Installation from Packages

To install all packages from the this repository as Debian packages use

    sudo apt-get update && sudo apt-get upgrade -y
    sudo apt-get install ros-melodic-navigation
    sudo apt-get install ros-melodic-map-server
    sudo apt-get install ros-melodic-move-base
    sudo apt-get install ros-melodic-amcl
    
Or better, use `rosdep`:

	sudo rosdep install --from-paths src

## Building from Source

To build from source, clone the latest version from this repository into your catkin workspace and compile the package using

	cd catkin_ws/src
	sudo apt update
	git clone https://github.com/Mennatallah98/WhereAmI.git
	cd ../
	rosdep install --from-paths . --ignore-src
	catkin_make
	
Source the workspace by adding this line .bashrc

	source ~/catkin_ws/devel/setup.bash

## Usage

In a new terminal

Open the world the world in gazebo and rviz with the rbot included

	roslaunch my_robot world.launch

In another window

Run navigation stack with the modified configuration file

	roslaunch my_robot amcl.launch
	
### To map the world

For [pgm_map_creator] which has been modified to work with Ubuntu18

	sudo apt-get install libignition-math2-dev protobuf-compiler
	cp <YOUR GAZEBO WORLD FILE> src/pgm_map_creator/world/<YOUR GAZEBO WORLD FILE>
	
Inside the world file
	
	<plugin filename="libcollision_map_creator.so" name="collision_map_creator"/>
	
To map the world

	gzserver --verbose src/pgm_map_creator/world/<YOUR GAZEBO WORLD FILE>
	roslaunch pgm_map_creator request_publisher.launch
	
create yaml file simlar to that exsitant in the repistory with measurements based on your world

## Config files

Config file folder/config

* **base_local_planner_params.yaml:** contains the parameters for [base_local_planner] which is  responsible for computing velocity commands to send to the mobile base. 

* **costmap_common_params.yaml:** contains the [common] parameters between the global and local [costmap].

* **global_costmap_params.yaml:** contains the parameters for [global] [costmap].

* **local_costmap_params.yaml:** contains the parameters for [local] [costmap].

## Launch files

* **robot_description.launch:** Runs the robot file and starts the joint publisher robot state publisher.

* **world.launch:** Starts [rviz] customized configuration and gazebo with the customized world , spawns the robot and launches robot_description.

* **amcl.launch:** Runs [amcl], [move_base], and [map_server] and sets the initial position of the robot in the map.

## Packages

* **my_robot:** Contains the URDF of r 4-wheeled under the name of my_robot with the attached sensors in addition to the world with robot embbeded in aldo the modified configuartion files and the world map.

* **[pgm_map_creator]:** Draws a map for the Gazebo world.


## Structure

	└── WhereAmI                                                # Where Am I Project
	    ├── my_robot                                                               
	    │   ├── CMakeLists.txt                                  # compiler instructions
	    │   ├── config                                          # config folder for configuration files 
	    │   │   ├── base_local_planner_params.yaml         
	    │   │   ├── costmap_common_params.yaml
	    │   │   ├── global_costmap_params.yaml
	    │   │   ├── local_costmap_params.yaml
	    │   │   └── __MACOSX
	    │   ├── launch                                         # launch folder for launch files  
	    │   │   ├── amcl.launch
	    │   │   ├── robot_description.launch
	    │   │   └── world.launch
	    │   ├── maps                                           # maps folder for maps
	    │   │   ├── map.pgm
	    │   │   └── map.yaml
	    │   ├── meshes                                         # meshes folder for sensors
	    │   │   └── hokuyo.dae
	    │   ├── package.xml                                    # package info
	    │   ├── rviz                                           # rviz folder for rviz configuration files
	    │   │   └── myworld.rviz
	    │   ├── urdf                                           # urdf folder for xarco files
	    │   │   ├── my_robot.gazebo
	    │   │   └── my_robot.xacro
	    │   └── worlds                                         # world folder for world files
	    │       └── myworld.world
	    └── pgm_map_creator                                    # pgm_map_creator 
		├── CMakeLists.txt                                 # compiler instructions
		├── launch                                         # launch folder for launch files 
		│   └── request_publisher.launch
		├── LICENSE                                        # License for repository
		├── maps                                           # maps folder for generated maps
		├── msgs                                           # msgs folder for communication files
		│   ├── CMakeLists.txt
		│   └── collision_map_request.proto
		├── package.xml                                    # package info
		├── README.md                                      # README for documentation
		├── src                                            # src folder for main function
		│   ├── collision_map_creator.cc               
		│   └── request_publisher.cc
		└── world                                          # world folder for world files
		    ├── myworld.world
		    └── udacity_mtv


[ROS]: http://www.ros.org
[amcl]: http://wiki.ros.org/amcl
[rviz]: http://wiki.ros.org/rviz
[pgm_map_creator]: https://github.com/udacity/pgm_map_creator.git
[navigation_stack]: http://wiki.ros.org/navigation/Tutorials/RobotSetup
[base_local_planner]: http://wiki.ros.org/base_local_planner
[costmap]: http://wiki.ros.org/costmap_2d
[global]: http://wiki.ros.org/navigation/Tutorials/RobotSetup#Global_Configuration:~:text=Global%20Configuration%20(global_costmap)
[local]: http://wiki.ros.org/navigation/Tutorials/RobotSetup#Local_Configuration:~:text=Local%20Configuration%20(local_costmap)
[common]: http://wiki.ros.org/navigation/Tutorials/RobotSetup#Global_Configuration:~:text=Common%20Configuration%20(local_costmap)%20%26%20(global_costmap)
[move_base]: http://wiki.ros.org/move_base
[map_server]: http://wiki.ros.org/map_server
