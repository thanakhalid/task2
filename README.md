# task2
-installing arduino robot arm steps and pictures-

*in order to do install the robot arm need also to install dependencies,git package provided and then compile the packages,
1- we start by changing dirctory to catkin_es/ws , the command:
$cd catkin_ws/src

2- we need to make sure to install git to be able to have installed packages from the git,the command: 
$sudo apt-get install git-all

3-now we install the package provided by smart method github git repository, the command:
$git clone https://github.com/smart-methods/arduino_robot_arm

4-as said before, we need dependencies,i use melodic version which is different from kinetic version, here is the commands which is written in catkin_ws dirctory so make sure to go back there:
$rosdep install --from-paths src --ignore-src -r -y
$ sudo apt-get install ros-melodic-moveit
$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
5-compile the packages,the command:
$catkin_make



*now we need Ardunio IDE in the ubuntu to do the work:
1-Download the Arduino Software (IDE) 

2-Extract the package:

3-Run the Install Scriptnote, make sure you are in the right dirctory which is the folder extracted and then You should find a new icon on your desktop, you can do it by right click then run in termianl or the command:
$sudo sh install.sh

now here's a screenshoot of the software:

![2](https://github.com/thanathea/task2/blob/main/Screenshot%202022-07-20%20072931.png)






*next is install rosserial to connect our computer with ardunio, with two commands:

$ sudo apt-get install ros-melodic-rosserial-arduino
$ sudo apt-get install ros-melodic-rosserial



*install ros_lib inside arudnio,the commands:

$ cd ~/Arduino/libraries
//Note: you have to delete libraries/ros_lib, if present, in order to regenerate as its existence causes an error. "rosrun rosserial_arduino make_libraries.py" creates the ros_lib directory.
$ rm -rf ros_lib
$  rosrun rosserial_arduino make_libraries.py .




*HERE i need the arm robot itself to connect it and do the rest of steps which is not available to me 
but we should do the follwing command for the USB connection:
$cd sketchbook/arduino 
%ls /dev
find the ttyUSB0 or ttyACM0 in the list, to make sure to change the port permission before uploading the Arduino code 
$ sudo chmod 777 /dev/ttyUSB0
after that i checked the code to make sure the IDE is working,here is a picture 
![2](https://github.com/thanathea/task2/blob/main/Screenshot%202022-07-23%20203015.png)

LASTLY, the rest of steps we need the arm (hardware) so we can control it useing different methods so here's codes copied from github:
Controlling the robot arm by joint_state_publisher
$ roslaunch robot_arm_pkg check_motors.launch

You can also connect with hardware by running:

$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200

(Note: You may need to use ttyACM)

Simulation
Run the following instructions to use gazebo

$ roslaunch robot_arm_pkg check_motors.launch
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
$ rosrun robot_arm_pkg joint_states_to_gazebo.py
(You may need to change the permission)

$ sudo chmod +x ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts/joint_states_to_gazebo.py

Controlling the robot arm by Moveit and kinematics
$ roslaunch moveit_pkg demo.launch

You can also connect with hardware by running:

$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200

(Note: You may need to use ttyACM)

Simulation
Run the following instruction to use gazebo

$ roslaunch moveit_pkg demo_gazebo.launch


thana khalid


