# WhereAmI
[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)


https://github.com/Mennatallah98/WhereAmI/assets/45118345/c7e48ad5-578f-4467-983c-c31747558c1f

## Overview

This project is the third project in Udacity Robotics Software Engineer nano degree where the world was mapped using pgm_map_creator and the robot navigated the world using navigation stack

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

Describe the quickest way to run this software, for example:

Run the main node with

	roslaunch ros_package_template ros_package_template.launch

## Config files

Config file folder/set 1

* **config_file_1.yaml** Shortly explain the content of this config file

Config file folder/set 2

* **...**

## Launch files

* **launch_file_1.launch:** shortly explain what is launched (e.g standard simulation, simulation with gdb,...)

     Argument set 1

     - **`argument_1`** Short description (e.g. as commented in launch file). Default: `default_value`.

    Argument set 2

    - **`...`**

* **...**

## Nodes

### ros_package_template

Reads temperature measurements and computed the average.


#### Subscribed Topics

* **`/temperature`** ([sensor_msgs/Temperature])

	The temperature measurements from which the average is computed.


#### Published Topics

...


#### Services

* **`get_average`** ([std_srvs/Trigger])

	Returns information about the current average. For example, you can trigger the computation from the console with

		rosservice call /ros_package_template/get_average


#### Parameters

* **`subscriber_topic`** (string, default: "/temperature")

	The name of the input topic.

* **`cache_size`** (int, default: 200, min: 0, max: 1000)

	The size of the cache.


### NODE_B_NAME

...

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





## Bugs & Feature Requests

Please report bugs and request features using the [Issue Tracker](https://github.com/ethz-asl/ros_best_practices/issues).


[ROS]: http://www.ros.org
[rviz]: http://wiki.ros.org/rviz
[Eigen]: http://eigen.tuxfamily.org
[std_srvs/Trigger]: http://docs.ros.org/api/std_srvs/html/srv/Trigger.html
[sensor_msgs/Temperature]: http://docs.ros.org/api/sensor_msgs/html/msg/Temperature.html
