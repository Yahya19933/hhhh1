# Arduino-Robot-Arm-Installation-on-ROS
Installing and configuring robot arm package on ROS

## Description

After installing ROS in Ubuntu you need these steps to install arm package

* Ubuntu version: 20.04.4

* ROS version: Noetic


### Create a workspase with Catkin
```
 source /opt/ros/noetic/setup.bash
 mkdir -p ~/catkin_ws/src
 cd ~/catkin_ws/ 
 catkin_make
 source devel/setup.bash
```
Now your ROS workspace is ready to have packages installed in it


### Installing Arduino Robot Arm Package
1. These commands will add the ardunino robot arm package to the src folder
```
 cd ~/catkin_ws/src/
 sudo apt install git
 git clone https://github.com/smart-methods/arduino_robot_arm
```


2. These commands will install all the necessary dependencies
```
 cd ~/catkin_ws
 rosdep install --from-paths src --ignore-src -r -y
 sudo apt-get install ros-noetic-moveit
 sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
 sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
 sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
```

3. This final command will compile all packages in your src folder
```
 catkin_make
```


4.Go to bashrc folder and do the following 
on terminal
```
 sudo nano ~/.bashrc

// at the end of the (bashrc) file add the follwing line:

source /home/*username/catkin_ws/devel/setup.bash

//after that click on ctrl + o then ctrl+ x to back to terminal and type 

source ~/.bashrc
```
make sure to switche *username* with your local username
 


## Configuring Arduino with ROS
1. Install [Arduino IDE](https://www.arduino.cc/en/software) in Ubuntu 
2. After unzipping the folder run the command `$ sudo ./install.sh`
3. Launch the Arduino IDE
4. Install the arduino package and ros library

![Screenshot from 2022-08-31 10-57-25](https://user-images.githubusercontent.com/90250848/187857679-bd98d01f-cfa3-4d3e-ab31-103b8a201767.png)



## Simulation
### Controlling the robot arm by joint_state_publisher
```
roslaunch robot_arm_pkg check_motors.launch
```

![joint_state_publisher](https://user-images.githubusercontent.com/90250848/187865524-914b03c4-3ffd-4130-b6bb-caf1b1647d4f.jpg)

You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```

## Controlling the robot arm by  gazebo
```
roslaunch robot_arm_pkg check_motors_gazebo.launch
```

![Gazebo](https://user-images.githubusercontent.com/90250848/187865554-4ff040f9-6758-44e2-a8cc-81f7b91d5c3a.png)

You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```


## Controlling the robot arm by movelet
```
roslaunch moveit_pkg demo.launch
```

![movelet](https://user-images.githubusercontent.com/90250848/187865613-a46b7508-8f88-4271-9ee1-3dfcbad46cd0.png)

You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```
