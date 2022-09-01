# hhhh1
Installing and configuring arm package on ROS

## Description
After installing ROS in Ubuntu you need these steps to install arm package
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
 cd catkin_ws/src/
 sudo apt install git
 git clone https://github.com/smart-methods/arduino_robot_arm
```


2. These commands will install all the necessary dependencies
```
 cd catkin_ws
 rosdep install --from-paths src --ignore-src -r -y
 sudo apt-get install ros-noetic-moveit
 sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
 sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
 sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
```

3.Go to bashrc folder and do the following 
on terminal
```
 sudo nano ~/.bashrc

// at the end of the (bashrc) file add the follwing line:

source /home/*username/catkin_pr/devel/setup.bash

//after that click on ctrl + o then ctrl+ x to back to terminal and type 

source ~/.bashrc
```
make sure to change the username as your username

 
4. This final command will compile all packages in your src folder
```
 catkin_make
```

## Configuring Arduino with ROS
1. Install [Arduino IDE](https://www.arduino.cc/en/software) in Ubuntu 
2. After unzipping the folder run the command `$ sudo ./install.sh`
3. Launch the Arduino IDE
4. Install the arduino package and ros library

![Screenshot from 2022-08-31 10-57-25](https://user-images.githubusercontent.com/90250848/187857679-bd98d01f-cfa3-4d3e-ab31-103b8a201767.png)



## Simulation














These commands will add the ardunino robot arm package to the src folder
```
 cd catkin_ws/src/
 sudo apt install git
 git clone https://github.com/smart-methods/arduino_robot_arm
```
