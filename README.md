## All activities till week 11
### Turlesim installation and rqt
#### Install the turtlesim library
```
asadbek@ubuntu:~$ sudo apt update
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Hit:2 http://packages.ros.org/ros/ubuntu focal InRelease                        
Hit:3 http://us.archive.ubuntu.com/ubuntu focal InRelease                       
Hit:4 http://packages.ros.org/ros2/ubuntu focal InRelease   
-----------------------------------------------------------------------------
asadbek@ubuntu:~$ sudo apt install ros-foxy-turtlesim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ros-foxy-turtlesim is already the newest version (1.2.5-1focal.20220209.151154).
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
#make sure your system is up-to-date
sudo apt update
asadbek@ubuntu:~$ sudo apt install ros-rolling-turtlesim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
....
```
#### Source the ros2 and Check the packages
```
asadbek@ubuntu:~$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
asadbek@ubuntu:~$ ros2 pkg executables turtlesim
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node
```
#### Check the list
```
asadbek@ubuntu:~$ ros2 node list
/teleop_turtle
asadbek@ubuntu:~$ ros2 topic list
/parameter_events
/rosout
/turtle1/cmd_vel
asadbek@ubuntu:~$ ros2 service list
/teleop_turtle/describe_parameters
/teleop_turtle/get_parameter_types
/teleop_turtle/get_parameters
/teleop_turtle/list_parameters
/teleop_turtle/set_parameters
/teleop_turtle/set_parameters_atomically
asadbek@ubuntu:~$ ros2 action list
/turtle1/rotate_absolute
asadbek@ubuntu:~$ 
```
#### Start turtlesim
```
asadbek@ubuntu:~$  ros2 run turtlesim turtlesim_node
[INFO] [1663638092.636082943] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1663638092.645975073] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
```
![image](https://user-images.githubusercontent.com/90145797/197091547-c2e1b19b-d520-495f-a683-1be650c66f52.png)

#### Contol the turtle
```
asadbek@ubuntu:~$  ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```
#### Run turtlesim turtlesim_node
```
asadbek@ubuntu:~$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
asadbek@ubuntu:~$ ros2 run turtlesim turtlesim_node
[INFO] [1663641213.835052574] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1663641213.843843646] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
[INFO] [1663641652.042988255] [turtlesim]: Spawning turtle [turtle2] at x=[1.000000], y=[1.000000], theta=[0.000000]
[WARN] [1663641958.871626326] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.941882, y=11.099703])
[WARN] [1663641958.886837813] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.933865, y=11.119869])
[WARN] [1663641958.903235761] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.925849, y=11.119869])
[WARN] [1663641958.919503554] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.917833, y=11.119869])
[WARN] [1663641958.935489939] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.909817, y=11.119869])
[WARN] [1663641958.950991549] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.901801, y=11.11.......
....skipped.........
```

#### Rqt intallation
```
#  MAKE SURE YOUR SYSTEM IS UP-TO-DATE
asadbek@ubuntu:~$   sudo apt update

# INSTALL THE RQT LIBRARY AND ITS PLUGINS
asadbek@ubuntu:~$  ~$ sudo apt install ~nros-rolling-rqt*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  pybind11-dev ros-rolling-class-loader
  ...
# To run rqt by just typing command "rqt"
asadbek@ubuntu:~$  ~$ rqt

asadbek@ubuntu:~$  ros2 run rqt_console rqt_console
```
![image](https://user-images.githubusercontent.com/90145797/197092085-135033ab-d429-423c-ae7e-4f0893379167.png)

###### rqt console
![image](https://user-images.githubusercontent.com/90145797/197092198-fa3f40bc-bbd7-4466-b83b-dff307880c0e.png)

#### Turtlesim simulation
```
# RUN THE TURTLESIM_NODE IN A NEW TAB
asadbek@ubuntu:~$  ros2 run turtlesim turtlesim_node
[INFO] [1664067181.891114659] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1664067181.940055496] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
# RUN THE TURTLE_TELEOP_KEY TO MOVE THE TURTLE IN A NEW TAB
asadbek@ubuntu:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
#RUN THE rqt in your terminal
asadbek@ubuntu:~$ ~$ rqt
#CHANGE THE /SPAWN SERVICE PARAMETERS TO RUN TURTLE2
#TO RUN THE TURTLE TO RUN THIS COMMAND
asadbek@ubuntu:~$  ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```
![image](https://user-images.githubusercontent.com/90145797/197092424-61bd2e7d-66e3-45f0-a025-aa12156cad11.png)

#### Remapping
```
asadbek@ubuntu:~$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
asadbek@ubuntu:~$ ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```

### Installing Colcon
```
# INSTALLING Colcon
asadbek@ubuntu:~$  sudo apt install python3-colcon-common-extensions
[sudo] password for ulugbekmirzabakhromov: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3-colcon-common-extensions is already the newest version (0.3.0-1).
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

-----------------------------------
 # ROS2 Colcon: Create a workspace
 ----------------------------------
asadbek@ubuntu:~$ echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
asadbek@ubuntu:~$ echo "export _colcon_cd_root=/opt/ros/rolling/" >> ~/.bashrc
asadbek@ubuntu:~$ source /opt/ros/rolling/setup.bash
asadbek@ubuntu:~$  mkdir -p ~/ros2_ws/src
asadbek@ubuntu:~$ cd ~/ros2_ws
asadbek@ubuntu:~$ /ros2_ws$ git clone https://github.com/ros/ros_tutorials.git -b rolling-devel
Cloning into 'ros_tutorials'...
remote: Enumerating objects: 2841, done.
remote: Counting objects: 100% (161/161), done.
remote: Compressing objects: 100% (88/88), done.
remote: Total 2841 (delta 93), reused 131 (delta 71), pack-reused 2680
Receiving objects: 100% (2841/2841), 617.66 KiB | 7.72 MiB/s, done.
Resolving deltas: 100% (1710/1710), done.
# RESOLVE DEPENDENCIES
asadbek@ubuntu:~$ ~/ros2_ws$ rosdep install -i --from-path src --rosdistro rolling -y
All required rosdeps installed successfully

# BUILD THE WORKSPACE WITH Colcon
asadbek@ubuntu:~$ ~/ros2_ws$ colcon build
[1.070s] WARNING:colcon.colcon_core.package_selection:Some selected packages are already built in one or more underlay workspaces:
	'turtlesim' is in: /opt/ros/rolling, /opt/ros/foxy
If a package in a merged underlay workspace is overridden and i
...
This may be promoted to an error in a future release of colcon-override-check.
Starting >>> turtlesim
[Processing: turtlesim]                             
[Processing: turtlesim] 
....
# SOURCE THE OVERLAY
asadbek@ubuntu:~$ source /opt/ros/rolling/setup.bash
asadbek@ubuntu:~$ cd ~/ros2_ws
asadbek@ubuntu:~$ . install/local_setup.bash
# MODIFY THE OVERLAY
asadbek@ubuntu:~/ros2_ws$ cd src
asadbek@ubuntu:~/ros2_ws/src$ ls
asadbek@ubuntu:~/ros2_ws/src$ git clone https://github.com/ros/ros_tutorials
Cloning into 'ros_tutorials'...
remote: Enumerating objects: 2841, done.
remote: Counting objects: 100% (161/161), done.
remote: Compressing objects: 100% (88/88), done.
remote: Total 2841 (delta 93), reused 131 (delta 71), pack-reused 2680
Receiving objects: 100% (2841/2841), 617.66 KiB | 855.00 KiB/s, done.
Resolving deltas: 100% (1710/1710), done.
asadbek@ubuntu:~/ros2_ws/src$ ls
ros_tutorials
asadbek@ubuntu:~/ros2_ws/src$ cd ros_tutorials
asadbek@ubuntu:~/ros2_ws/src/ros_tutorials$ ls
roscpp_tutorials  rospy_tutorials  ros_tutorials  turtlesim
asadbek@ubuntu:~/ros2_ws/src/ros_tutorials$ cd turtlesim/src
asadbek@ubuntu:~/ros2_ws/src/ros_tutorials/turtlesim/src$ ls
turtle.cpp  turtle_frame.cpp  turtlesim  turtlesim.cpp
asadbek@ubuntu:~/ros2_ws/src/ros_tutorials/turtlesim/src$ nano turtle_frame.cpp
```
#### Create a package
```
asadbek@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_python --node-name my_node my_package
going to create a new package
package name: my_package
destination directory: /home/asadbek/ros2_ws/src
package format: 3
version: 0.0.0
...
asadbek@ubuntu:~/ros2_ws/src$ cd ..

# BUILDING PACKAGES
asadbek@ubuntu:~/ros2_ws$ colcon build            
Summary: 3 packages finished [4.08s]
asadbek@ubuntu:~/ros2_ws$ colcon build --packages-select my_package
Starting >>> my_package
Finished <<< my_package [1.14s]          
Summary: 1 package finished [1.37s]

#SOURCE THE SETUP FILE
asadbek@ubuntu:~/ros2_ws$ . install/setup.bash
asadbek@ubuntu:~/ros2_ws$ ros2 run my_package my_node
Hi from my_package.

```
### Writing a publisher and subscriber(Python)

```
#MAKE SURE YOU ARE IN THE src FOLDER AND ENTER THE COMMAND FOR CREATING THE PY_PACKAGE
asadbek@ubuntu:~$ cd ~/ros2_ws
asadbek@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_pubsub
going to create a new package
package name: py_pubsub
destination directory: /home/asadbek/ros2_ws/src
package format: 3
version: 0.0.0
...
asadbek@ubuntu:~/ros2_ws/src$ ls
my_package  my_pkg  py_pubsub  ros_tutorials
asadbek@ubuntu:~/ros2_ws/src$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-09-27 21:42:13--  https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
...
2022-09-27 21:42:14 (11.5 MB/s) - ‘publisher_member_function.py’ saved [1576/1576]

#DOWNLOAD THE publisher_member_function.py TO ros2_ws/src/py_pubsub/py_pubsub DIRECTORY

asadbek@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-09-27 22:19:36--  https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
...
2022-09-27 22:19:37 (31.7 MB/s) - ‘publisher_member_function.py’ saved [1576/1576]

#ALSO DOWNLOAD THE subscriber_member_function.py 
asadbek@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
...
2022-09-27 21:54:36 (18.1 MB/s) - ‘subscriber_member_function.py’ saved [1469/1469]
```


#### buildind and running
```
asadbek@ubuntu:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully
asadbek@ubuntu:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
Finished <<< py_pubsub [2.89s]          

Summary: 1 package finished [4.10s]
asadbek@ubuntu:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully
asadbek@ubuntu:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
Finished <<< py_pubsub [1.41s]          

Summary: 1 package finished [1.66s]

---------------------------------------
# TESTING THE NODES
---------------------------------------
asadbek@ubuntu:~/ros2_ws$ . install/setup.bash
asadbek@ubuntu:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1664342591.577268871] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [1664342592.061454408] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [1664342592.562140724] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [1664342593.062828040] [minimal_publisher]: Publishing: "Hello World: 3"
asadbek@ubuntu:~/ros2_ws$ . install/setup.bash
asadbek@ubuntu:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1664342591.577268871] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [1664342592.061454408] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [1664342592.562140724] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [1664342593.062828040] [minimal_publisher]: Publishing: "Hello World: 3"
```
### Writing a simple service and client(Python)

```

#Firstly, create the package into the ros2_ws/src directory
------------------------------------------------------------
asadbek@ubuntu:~$ cd ros2_ws
asadbek@ubuntu:~/ros2_ws$ cd src
asadbek@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_srvcli --dependencies rclpy example_interfaces
going to create a new package
package name: py_srvcli
....

# Write the service node inside the ros2_ws/src/py_srvcli/py_srvcli directory:

asadbek@ubuntu:~/ros2_ws/src/py_srvcli$ nano service_member_function.py
asadbek@ubuntu:~/ros2_ws/src/py_srvcli$ nano client_member_function.py

# Add an entry points into the setup.py to be able to run the servic&client nodes.

asadbek@ubuntu:~/ros2_ws/src/py_srvcli$ nano setup.py

# BUILD AND RUN
----------------
asadbek@ubuntu:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully
asadbek@ubuntu:~/ros2_ws$ colcon build --packages-select py_srvcli
Starting >>> py_srvcli
Finished <<< py_srvcli [2.13s]          
Summary: 1 package finished [2.48s]

# Open a new terminal, navigate to ros2_ws, and source the setup files

asadbek@ubuntu:~/ros2_ws$ . install/setup.bash
asadbek@ubuntu:~/ros2_ws$ ros2 run py_srvcli service
[INFO] [1664849371.615817085] [minimal_service]: Incoming request
a: 2 b: 3
# Do the same thing for the client node
asadbek@ubuntu:~/ros2_ws$ . install/setup.bash
asadbek@ubuntu:~/ros2_ws$ ros2 run py_srvcli client 2 3
[INFO] [1664849371.665846561] [minimal_client_async]: Result of add_two_ints: for 2 + 3 = 5
```
## Intermediate level
### Creating an action
```
#create a package named action_tutorials_interfaces
asadbek@ubuntu:~$ mkdir -p ros2_ws/src #you can reuse existing workspace with this naming convention
asadbek@ubuntu:~$ cd ros2_ws/src
asadbek@ubuntu:~/ros2_ws/src$ ros2 pkg create action_tutorials_interfaces
ros2: command not found
asadbek@ubuntu:~/ros2_ws/src$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
asadbek@ubuntu:~/ros2_ws/src$ ros2 pkg create action_tutorials_interfaces
going to create a new package
package name: action_tutorials_interfaces
destination directory: /home/asadbek/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['asadbek <khalilovasadbek27@gmail.com>']
licenses: ['TODO: License declaration']
build type: ament_cmake
dependencies: []
creating folder ./action_tutorials_interfaces
creating ./action_tutorials_interfaces/package.xml
creating source and include folder
creating folder ./action_tutorials_interfaces/src
creating folder ./action_tutorials_interfaces/include/action_tutorials_interfaces
creating ./action_tutorials_interfaces/CMakeLists.txt
asadbek@ubuntu:~/ros2_ws/src$ cd action_tutorials_interfaces

#create a file called Fibonacci.action

asadbek@ubuntu:~/ros2_ws/src$ cd action_tutorials_interfaces
asadbek@ubuntu:~/ros2_ws/src/action_tutorials_interfaces$ mkdir action
asadbek@ubuntu:~/ros2_ws/src/action_tutorials_interfaces$ code Fibonacci.action
asadbek@ubuntu:~/ros2_ws/src/action_tutorials_interfaces$ ls
action  CMakeLists.txt  Fibonacci.action  include  package.xml  src
asadbek@ubuntu:~/ros2_ws/src/action_tutorials_interfaces$ code CMakeLists.txt 
asadbek@ubuntu:~/ros2_ws/src/action_tutorials_interfaces$ code package.xml 
asadbek@ubuntu:~/ros2_ws/src/action_tutorials_interfaces$ cd ~/ros2_ws/
asadbek@ubuntu:~/ros2_ws$ colcone build
colcone: command not found

#Build COLCON
asadbek@ubuntu:~/ros2_ws$ colcon build
[1.354s] WARNING:colcon.colcon_core.package_selection:Some selected packages are already built in one or more underlay workspaces:
	'examples_rclcpp_minimal_timer' is in: /opt/ros/foxy
	'examples_rclcpp_minimal_action_server' is in: /opt/ros/foxy
	'examples_rclpy_minimal_subscriber' 
	....
#adding the following lines to our CMakeLists.txt AND to our package.xml
```
![image](https://user-images.githubusercontent.com/90145797/197122177-93175cac-0c57-4992-8215-1dfe18eb5e81.png)
![image](https://user-images.githubusercontent.com/90145797/197122210-33e7cbb4-1f33-43c2-8509-cf3e2e4b172c.png)

#### Final to result to check
```
###We can check that our action built successfully
asadbek@ubuntu:~/ros2_ws$ # Source our workspace
asadbek@ubuntu:~/ros2_ws$ # On Windows: call install/setup.bat
asadbek@ubuntu:~/ros2_ws$ . install/setup.bash
ROS_DISTRO was set to 'foxy' before. Please make sure that the environment does not mix paths from different distributions.
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
asadbek@ubuntu:~/ros2_ws$ # Check that our action definition exists
asadbek@ubuntu:~/ros2_ws$ ros2 interface show action_tutorials_interfaces/action/Fibonacci
int32 order
---
int32[] sequence
---
int32[] partial_sequence
```
### Writing an action server and client(Python)
```
#Writing an action server
-------------------------
asadbek@ubuntu:~$ code fibonacci_action_server.py

#You can get the action_server code from this link:
---------------------------------------------------
```
(https://github.com/Khai2708/turtlesim1_pro/blob/main/fibonacci_action_client(server)/fibonacci_action_server.py)

```
#Run the action server
asadbek@ubuntu:~$ python3 fibonacci_action_server.py 
[INFO] [1664948740.009765307] [fibonacci_action_server]: Executing goal...
[WARN] [1664948740.010891932] [fibonacci_action_server]: Goal state not set, assuming aborted. Goal ID: [ 43 132  59 102 136 104  68 222 136  35 140  96 233 172 179 145]

#In another terminal, use the command line interface to send a goal:
--------------------------------------------------------------------
asadbek@ubuntu:~$ ros2 action send_goal fibonacci action_tutorials_interfaces/action/Fibonacci "{order: 5}"
Waiting for an action server to become available...
Sending goal:
     order: 5

Goal accepted with ID: 15197cd7683f45baa7c2facdddd31a74

Result:
    sequence:
- 0
- 1
- 1
- 2
- 3
- 5

Goal finished with status: SUCCEEDED

# Writing a action_client server
-------------------------
asadbek@ubuntu:~$ nano fibonacci_action_client.py

#You can get the action_client code from this link:
---------------------------------------------------
```
(https://github.com/Khai2708/turtlesim1_pro/blob/main/fibonacci_action_client(server)/fibonacci_action_client.py)

```
#Run the action client
-----------------------
asadbek@ubuntu:~$ python3 fibonacci_action_client.py
[INFO] [1664949683.787442150] [fibonacci_action_client]: Goal accepted :)
[INFO] [1664949683.790887484] [fibonacci_action_client]: Received feedback: array('i', [0, 1, 1])
[INFO] [1664949684.794285170] [fibonacci_action_client]: Received feedback: array('i', [0, 1, 1, 2])
[INFO] [1664949685.796666631] [fibonacci_action_client]: Received feedback: array('i', [0, 1, 1, 2, 3])
[INFO] [1664949686.799187578] [fibonacci_action_client]: Received feedback: array('i', [0, 1, 1, 2, 3, 5])
....

#In another terminal, run the action_server:
--------------------------------------------------------------------
asadbek@ubuntu:~$ python3 fibonacci_action_server.py 
[INFO] [1664949683.788839423] [fibonacci_action_server]: Executing goal...
[INFO] [1664949683.789502547] [fibonacci_action_server]: Feedback: array('i', [0, 1, 1])
[INFO] [1664949684.792395799] [fibonacci_action_server]: Feedback: array('i', [0, 1, 1, 2])
[INFO] [1664949685.794762732] [fibonacci_action_server]: Feedback: array('i', [0, 1, 1, 2, 3])
[INFO] [1664949686.797654565] [fibonacci_action_server]: Feedback: array('i', [0, 1, 1, 2, 3, 5])
....
```
### Composing multiple nodes in a single process
#### DISCOVER AVAILABLE COMPONENTS
```
asadbek@ubuntu:~$ ros2 component types
action_tutorials_cpp
  action_tutorials_cpp::FibonacciActionClient
  action_tutorials_cpp::FibonacciActionServer
depthimage_to_laserscan
  depthimage_to_laserscan::DepthImageToLaserScanROS
composition
  composition::Talker
  composition::Listener
  composition::NodeLikeListener
  composition::Server
  composition::Client
image_tools
  image_tools::Cam2Image
  image_tools::ShowImage
joy ...
```
##### Run-time composition using ROS services with a publisher and subscriber
```
# In the first shell, start the component container:
--------------------------------------------------------
asadbek@ubuntu:~$ ros2 run rclcpp_components component_container

# Open the second shell and verify that the container is running via ros2 command line tools:
---------------------------------------------------------------------------
asadbek@ubuntu:~$ ros2 component list
/ComponentManager
#asadbek@ubuntu:~$ ros2 component load /ComponentManager composition composition::Talker
Loaded component 1 into '/ComponentManager' container node as '/talker'
asadbek@ubuntu:~$

#In the second shell load the talker component 
asadbek@ubuntu:~$ ros2 run rclcpp_components component_container
--------------------------------------------------------------------
#Now the first shell should show a message that the component was loaded as well as repeated message for publishing a message.
asadbek@ubuntu:~$ ros2 run rclcpp_components component_container
[INFO] [1666334596.518827588] [ComponentManager]: Load Library: /opt/ros/foxy/lib/libtalker_component.so
[INFO] [1666334596.527068008] [ComponentManager]: Found class: rclcpp_components::NodeFactoryTemplate<composition::Talker>
[INFO] [1666334596.527209749] [ComponentManager]: Instantiate class: rclcpp_components::NodeFactoryTemplate<composition::Talker>
[INFO] [1666334597.574873610] [talker]: Publishing: 'Hello World: 1'
[INFO] [1666334598.574389449] [talker]: Publishing: 'Hello World: 2'
[INFO] [1666334599.573799202] [talker]: Publishing: 'Hello World: 3'
[INFO] [1666334600.574322492] [talker]: Publishing: 'Hello World: 4'
...

#Run another command in the second shell to load the listener component
---------------------------------------------------------------------
asadbek@ubuntu:~$  ros2 component load /ComponentManager composition composition::Listener
Loaded component 2 into '/ComponentManager' container node as '/listener'

#Now the first shell should show repeated output for each received message.
-----------------------------------------------------------------------------
asadbek@ubuntu:~$ ros2 run rclcpp_components component_container
[INFO] [1666335304.720814020] [ComponentManager]: Load Library: /opt/ros/foxy/lib/libtalker_component.so
[INFO] [1666335304.721622710] [ComponentManager]: Found class: rclcpp_components::NodeFactoryTemplate<composition::Talker>
[INFO] [1666335304.721757286] [ComponentManager]: Instantiate class: rclcpp_components::NodeFactoryTemplate<composition::Talker>
[INFO] [1666335305.733862016] [talker]: Publishing: 'Hello World: 1'
[INFO] [1666335305.734349304] [listener]: I heard: [Hello World: 1]
[INFO] [1666335305.734453155] [listener]: I heard: [Hello World: 1]
[INFO] [1666335306.733860128] [talker]: Publishing: 'Hello World: 2'
[INFO] [1666335306.734136702] [listener]: I heard: [Hello World: 2]
[INFO] [1666335306.734182823] [listener]: I heard: [Hello World: 2]
...
```
### Creating a launch

```
#Create a new directory to store your launch files and write the lancg file
----------------------------------------------------------------------------
asadbek@ubuntu:~$ mkdir launch
asadbek@ubuntu:~$ cd launch/
asadbek@ubuntu:~/launch$ code turtlesim_mimic_launch.py

#Run the launch files above
------------------------------------------------------------------------
asadbek@ubuntu:~/launch$ ros2 launch turtlesim_mimic_launch.py
[INFO] [launch]: All log files can be found below /home/asadbek/.ros/log/2022-10-21-16-04-24-835874-ubuntu-127117
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [turtlesim_node-1]: process started with pid [127119]
[INFO] [turtlesim_node-2]: process started with pid [127121]
[INFO] [mimic-3]: process started with pid [127123]
[turtlesim_node-1] [INFO] [1666335865.829246958] [turtlesim1.sim]: Starting turtlesim with node name /turtlesim1/sim
[turtlesim_node-2] [INFO] [1666335865.830976504] [turtlesim2.sim]: Starting turtlesim with node name /turtlesim1/sim
[turtlesim_node-2] [INFO] [1666335865.862988742] [turtlesim2.sim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
[turtlesim_node-1] [INFO] [1666335865.884127410] [turtlesim1.sim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]

```
![image](https://user-images.githubusercontent.com/90145797/197135469-8eceb9c5-bb89-4b00-b314-9020d022af4b.png)

#### To see the system in action, open a new terminal and run the ros2 topic pub commands below

```
asadbek@ubuntu:~$ ros2 topic pub -r 1 /turtlesim1/turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: -1.8}}"
publisher: beginning loop
publishing #1: geometry_msgs.msg.Twist(linear=geometry_msgs.msg.Vector3(x=2.0, y=0.0, z=0.0), angular=geometry_msgs.msg.Vector3(x=0.0, y=0.0, z=-1.8))

publishing #2: geometry_msgs.msg.Twist(linear=geometry_msgs.msg.Vector3(x=2.0, y=0.0, z=0.0), angular=geometry_msgs.msg.Vector3(x=0.0, y=0.0, z=-1.8))
...
```
![Screenshot from 2022-10-21 16-09-03](https://user-images.githubusercontent.com/90145797/197134874-1f99cce8-c3fb-44b8-be8c-328776301cc0.png)

#### Introspect the system with rqt_graph
```
asadbek@ubuntu:~/launch$ rqt_graph
[INFO] [1665557607.422017603] [rclcpp]: signal_handler(signal_value=2)
```
![image](https://user-images.githubusercontent.com/90145797/197136262-2a61a53a-e13c-410c-84d6-fc3dfb132c78.png)

# Week 9,10,11 Turtlebot3 installation(Foxy version)
#### 1.Setup PC
```
> Install ROS 2 on Remote PC
----------------------------------------------------------------------------
asadbek@ubuntu:~$  wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros2_foxy.sh
--2022-10-26 14:14:20--  https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros2_foxy.sh ...

install_ros2_foxy.s 100%[===================>]   2.28K  --.-KB/s    in 0.004s  

2022-10-26 14:14:20 (549 KB/s) - ‘install_ros2_foxy.sh.1’ saved [2336/2336]

asadbek@ubuntu:~$ sudo chmod 755 ./install_ros2_foxy.sh
[sudo] password for asadbek: 
asadbek@ubuntu:~$ bash ./install_ros2_foxy.sh

[Note] OS version  >>> Ubuntu 20.04 (Focal Fossa)
[Note] Target ROS version >>> ROS 2 Foxy Fitzroy
[Note] Colcon workspace   >>> /home/asadbek/colcon_ws
...

> Install Dependendent ROS 2 Packages
---------------------------------------------------------------------------
> Install Gazebo11
asasadbek@ubuntu:~$ udo apt-get install ros-foxy-gazebo-*
334 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
locales is already the newest version (2.31-0ubuntu9.9).
> Install Cartographer
asasadbek@ubuntu:~$ sudo apt install ros-foxy-cartographer
asasadbek@ubuntu:~$ sudo apt install ros-foxy-cartographer-ros
libgazebo11-dev libgpg-error-dev libgpgme-dev libgraphite2-dev libgtk2.0-dev
  libgts-dev libharfbuzz-dev libharfbuzz-gobject0 libignition-cmake2-dev
  libignition-common3 libignition-common3-av libignition-common3-av-dev
  libignition-common3-core-dev libignition-common3-dev
  libignition-common3-events libignition-common3-events-dev
  libignition-common3-graphics libignition-common3-graphics-dev
  libignition-common3-profiler libignition-common3-profiler-dev
  
> Install Navigation2
asasadbek@ubuntu:~$ sudo apt install ros-foxy-navigation2
asasadbek@ubuntu:~$ sudo apt install ros-foxy-nav2-bringup
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 334 not upgraded.
[Make the colcon workspace and test colcon build]..

> Install TurtleBot3 Packages
------------------------------------------------------
asasadbek@ubuntu:~$ source ~/.bashrc
asadbek@ubuntu:~/turtlebot_install$ sudo apt install ros-foxy-dynamixel-sdk
[sudo] password for asadbek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:...

asadbek@ubuntu:~/turtlebot_install$  sudo apt install ros-foxy-turtlebot3-msgs
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  ros-foxy-dynamixel-sdk
0 upgraded, 1 newly installed, 0 to remove and 334 not upgraded.
Need to get 42.0 kB of archives.
After this operation, 325 kB of ...
asadbek@ubuntu:~/turtlebot_install$  sudo apt install ros-foxy-turtlebot3
[sudo] password for asadbek: 
Reading package lists... Done
Building dependency tree       
Reading state information.
...

> Environment Configuration
-----------------------------------------------------------------------------
asadbek@ubuntu:~/turtlebot_install$ echo 'export ROS_DOMAIN_ID=30 #TURTLEBOT3' >> ~/.bashrc
asadbek@ubuntu:~/turtlebot_install$ source ~/.bashrc
asadbek@ubuntu:~/turtlebot_install$ ..

```
#### 2.SBC setup
```
> Prepare microSD Card and Reader
> Download TurtleBot3 SBC Image
> Unzip the downloaded image file
> Burn the image file
> Raspberry Pi Imager Installation
```
![rpi_imager](https://user-images.githubusercontent.com/90145797/201824177-362652b5-69aa-401f-bf12-bd2c824b07e9.gif)

##### Disks Utility
![disks](https://user-images.githubusercontent.com/90145797/201824350-20ff289e-14a7-4890-8c04-ced33a7199f2.gif)


##### Resize the Partition
![gparted](https://user-images.githubusercontent.com/90145797/201824508-7aeaa336-50bd-42c4-932d-dda27ff8b4ef.gif)

```
> Configure the WiFi Network Setting

asadbek@ubuntu: $ cd /media/$USER/writable/etc/netplan
asadbek@ubuntu: $ sudo nano 50-cloud-init.yaml
```
![image](https://user-images.githubusercontent.com/90145797/201824789-92dd6ae8-4ee9-4f07-a12b-4329cb85cadf.png)

```
> ROS2 Network Configuration 
he default ROS Domain ID for TurtleBot3 is set to 30 in the *.bashrc* file.
... ROS_DOMAIN_ID=12 #TURTLEBOT3

> NEW LDS-02 Configuration
 > Install the LDS-02 driver and update TurtleBot3 package
  
asadbek@ubuntu:  $ sudo apt update
asadbek@ubuntu:  $ sudo apt install libudev-dev
asadbek@ubuntu:  $ cd ~/turtlebot3_ws/src
asadbek@ubuntu:  $ git clone -b ros2-devel https://github.com/ROBOTIS-GIT/ld08_driver.git
asadbek@ubuntu:  $ cd ~/turtlebot3_ws/src/turtlebot3 && git pull
asadbek@ubuntu:  $ rm -r turtlebot3_cartographer turtlebot3_navigation2
asadbek@ubuntu:  $ cd ~/turtlebot3_ws && colcon build --symlink-install


  
 > Export the LDS_MODEL to the bashrc file. Depending on your LDS model, LDS-01 or LDS-02
 
asadbek@ubuntu:   $ echo 'export LDS_MODEL=LDS-02' >> ~/.bashrc
asadbek@ubuntu:  $ source ~/.bashrc
 
-----------------------------------------------------------------
```

#### 3.OpenCR setup
```
> Connect the OpenCR to the Rasbperry Pi using the micro USB cable.
> Install required packages on the Raspberry Pi to upload the OpenCR firmware. 

$ sudo dpkg --add-architecture armhf
$ sudo apt update
$ sudo apt install libc6:armhf

> Depending on the platform, use either burger or waffle for the OPENCR_MODEL name. 
$ export OPENCR_PORT=/dev/ttyACM0
$ export OPENCR_MODEL=burger
$ rm -rf ./opencr_update.tar.bz2

> Download the firmware and loader, then extract the file. 
$ wget https://github.com/ROBOTIS-GIT/OpenCR-Binaries/raw/master/turtlebot3/ROS2/latest/opencr_update.tar.bz2
$ tar -xjf ./opencr_update.tar.bz2

> Upload firmware to the OpenCR.
$ cd ~/opencr_update
$ ./update.sh $OPENCR_PORT $OPENCR_MODEL.opencr
```
##### A successful firmware upload for TurtleBot3 burger
![image](https://user-images.githubusercontent.com/90145797/201826172-685b68b0-7b41-400e-aad0-f5c1c118b0a2.png)

#### 4. Bring up
```
> Bringup TurtleBot3
 > Open a new terminal from PC and connect to Raspberry Pi with its IP address.
$ ssh ubuntu@{IP_ADDRESS_OF_RASPBERRY_PI}

 > Bring up basic packages to start TurtleBot3 applications.
$ export TURTLEBOT3_MODEL=burger
$ ros2 launch turtlebot3_bringup robot.launch.py

 > TurtleBot3 model is burger and the terminal will print below messages.
$ export TURTLEBOT3_MODEL=burger
$ ros2 launch turtlebot3_bringup robot.launch.py
[INFO] [launch]: All log files can be found below /home/ubuntu/.ros/log/2019-08-19-01-24-19-009803-ubuntu-15310
[INFO] [launch]: Default logging verbosity is set to INFO
urdf_file_name : turtlebot3_burger.urdf
[INFO] [robot_state_publisher-1]: process started with pid [15320]
[INFO] [hlds_laser_publisher-2]: process started with pid [15321]
[INFO] [turtlebot3_ros-3]: process started with pid [15322]
[robot_state_publisher-1] Initialize urdf model from file: /home/ubuntu/turtlebot_ws/install/turtlebot3_description/share/turtlebot3_description/urdf/turtlebot3_burger.urdf
[robot_state_publisher-1] Parsing robot urdf xml string.
[robot_state_publisher-1] Link base_link had 5 children
[robot_state_publisher-1] Link caster_back_link had 0 children
[robot_state_publisher-1] Link imu_link had 0 children
[robot_state_publisher-1] Link base_scan had 0 children
[robot_state_publisher-1] Link wheel_left_link had 0 children
[robot_state_publisher-1] Link wheel_right_link had 0 children
[robot_state_publisher-1] got segment base_footprint
[robot_state_publisher-1] got segment base_link
[robot_state_publisher-1] got segment base_scan
[robot_state_publisher-1] got segment caster_back_link
[robot_state_publisher-1] got segment imu_link
[robot_state_publisher-1] got segment wheel_left_link
[robot_state_publisher-1] got segment wheel_right_link
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Init TurtleBot3 Node Main
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Init DynamixelSDKWrapper
[turtlebot3_ros-3] [INFO] [DynamixelSDKWrapper]: Succeeded to open the port(/dev/ttyACM0)!
[turtlebot3_ros-3] [INFO] [DynamixelSDKWrapper]: Succeeded to change the baudrate!
[robot_state_publisher-1] Adding fixed segment from base_footprint to base_link
[robot_state_publisher-1] Adding fixed segment from base_link to caster_back_link
[robot_state_publisher-1] Adding fixed segment from base_link to imu_link
[robot_state_publisher-1] Adding fixed segment from base_link to base_scan
[robot_state_publisher-1] Adding moving segment from base_link to wheel_left_link
[robot_state_publisher-1] Adding moving segment from base_link to wheel_right_link
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Start Calibration of Gyro
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Calibration End
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Add Motors
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Add Wheels
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Add Sensors
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create battery state publisher
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create imu publisher
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create sensor state publisher
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create joint state publisher
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Add Devices
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create motor power server
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create reset server
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Succeeded to create sound server
[turtlebot3_ros-3] [INFO] [turtlebot3_node]: Run!
[turtlebot3_ros-3] [INFO] [diff_drive_controller]: Init Odometry
[turtlebot3_ros-3] [INFO] [diff_drive_controller]: Run!
```
##### Topic list
```
$ ros2 topic list
/battery_state
/cmd_vel
/imu
/joint_states
/magnetic_field
/odom
/parameter_events
/robot_description
/rosout
/scan
/sensor_state
/tf
/tf_static
```
##### Service list
```
$ ros2 service list
/diff_drive_controller/describe_parameters
/diff_drive_controller/get_parameter_types
/diff_drive_controller/get_parameters
/diff_drive_controller/list_parameters
/diff_drive_controller/set_parameters
/diff_drive_controller/set_parameters_atomically
/hlds_laser_publisher/describe_parameters
/hlds_laser_publisher/get_parameter_types
/hlds_laser_publisher/get_parameters
/hlds_laser_publisher/list_parameters
/hlds_laser_publisher/set_parameters
/hlds_laser_publisher/set_parameters_atomically
/launch_ros/describe_parameters
/launch_ros/get_parameter_types
/launch_ros/get_parameters
/launch_ros/list_parameters
/launch_ros/set_parameters
/launch_ros/set_parameters_atomically
/motor_power
/reset
/sound
/turtlebot3_node/describe_parameters
/turtlebot3_node/get_parameter_types
/turtlebot3_node/get_parameters
/turtlebot3_node/list_parameters
/turtlebot3_node/set_parameters
/turtlebot3_node/set_parameters_atomically
```

