# Turtlebot 3: SLAM and Navigation
### Written by DK Kang

## OBJECTIVE
The goal is to use the `Turtlebot 3` to autonomously map an environment and then navigate within the map using the `slam_toolbox`

## REQUIREMENTS & SETUP

### REUQIRMENTS

- This project requires `ROS`

- This project requires either a real robot of `Turtlebot 3` or a `gazebo` simulation enviorment and   its info can be found in the following link:
https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/

- If you are using a real robot, refer to to following website: 
https://emanual.robotis.com/docs/en/platform/turtlebot3/setup/


-  we will be using turtlebot 3 packages that ROBOTIS has already developed. Refer to the following website:
https://github.com/ROBOTIS-GIT/turtlebot3



### setup

I will be using `ROS-noetic` version.

1. sudo apt-get update
2. sudo apt-get upgrade
3. install `ROS-noetic` from following website: http://wiki.ros.org/noetic/Installation/Ubuntu
4. install `pythpn3`rosdep
	```
	sudo apt install python3-rosdep
	sudo rosdep init
	rosdep update
	```

5. install some dependencies `sudo apt install python3-vcstool git gitk python3-pip catkin-lint`
6. install `slam-toolbox`by runing `sudo apt install ros-eloquent-slam-toolbox`
7. install `ROS_navigation` by running `sudo apt install ros-noetic-navigation`
6. go to yout home dir `cd ~'
7. Create workspace: `mkdir ws` and `cd _ws`
8. `mkdir src` and `cd src`
9. `git clone https://github.com/ME495-EmbeddedSystems/homework04-rubberdk.git`
10. `cd ..` to cd into your `ws` dir and `catkin_make`
11. edit your `./bashrc ` and add `export TURTLEBOT3_MODEL=burger` in the file. If we are not using burger, change the model name accordingly



## Nodes

This project include one node `auto_nav` used for autonomous mapping & navigation
  
This node generates xy-coordinates that move_base uses for the navigation of the turtlebot. goal coordinate points are generated by a simple algorithm that adds random numbers in between -0.5 and 0.5 to the previous goal coordinates allowing the robot to move slowly and spontaneously.

     
SUBSCRIBER:
     + map_sub (/map) ~ information about the robot's current knowledge of the environment
       type = nav_msgs/OccupancyGrid


## MAPS

The `maps` directory contains two sets of map data.
1) `map.yaml` and `maps.pgm` were mapped by mannual control of the turtlebot
2) `expl.yaml` and `expl.pgm` were mapped autonomously by the turtlebot


## REUSLTS

make sure to source your workspace by `source ~/ws/devel/setup.bash`

Demo gif files are fast-forwarded for your convinence. Refer to the YouTube link for the full video.

### SLAM with mannual control

`roslaunch hw4 start_slam.launch`

This launch file allows you to drive the turtlebot with your keyboard and do mapping in a house in `gazebo` simulation

Keyboard Control:
W - go foward
S - stop
A - turn counter-clockwise
D - turn clockwise
X - reverse

### Navigation with known mapping

`roslaunch hw4 nav_stack.launch`

This launch file allows you to navigate your turtlebot in the house in `gazebo` simulation

You can navigate by moving the robot by setting 2D navigation goals in Rviz


![nav_stack](https://media.giphy.com/media/lpNVGeCa73QhOi9MxV/giphy.gif)


Full Video: https://youtu.be/LqCy_FP7HPU


### SLAM & Navigation 

`roslaunch hw4 slam_stack.launch`

This launch file allows you to do mapping and navigate your turtlebot in the house in `gazebo` simulation.

By moving the robot by setting 2D navigation goals in Rviz, the turtlebot does mapping while navigating.

![slam_stack](https://media.giphy.com/media/KIoptgov1MiLS1YMbx/giphy.gif)

Full Video: https://youtu.be/OFxcJqrekvE


### Autonomous SLAM & Navigation

`roslaunch hw4 auto_nav.launch`

This launch file makes the turtlebot to autonomously navigate and do mapping

![auto_nav](https://media.giphy.com/media/dY2xHECCo95c5DPjfl/giphy.gif)

Full Video: https://youtu.be/ceaA-sR2w_s



