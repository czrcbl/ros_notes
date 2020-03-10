# ROS Notes

After instalation:

## Pre Setup
Initialize rosdep:
```bash
sudo rosdep init
rosdep update
```

### Environment Setup
```bash
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### Install build dependencies
```bash
sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential
```

## Using

### Workspace Creation
Create a catkin workspace on user home folder:
```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws
catkin_make
# or, for python 3 users
catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```
You have to install `catkin_pkg` with `pip3` in order to use `catkin_make` with `python3`.

```bash
sudo apt install python3-pip
sudo pip3 install catkin_pkg
```

Source the `setup.sh` file:
```bash
source devel/setup.bash
```
Or add the following line to the .bashrc file:
```bash
gedit .bashrc 
source ~/catkin_ws/devel/setup.bash
```
Check if the workspace is properly overlayed:
```bash
echo $ROS_PACKAGE_PATH
```

### Package Creation
Go to the source directory:
```bash
 cd ~/catkin_ws/src
```
Then:
```bash
catkin_create_pkg <package_name> <dependency1> <dependency2> ...
```
Now you need to build the packages in the catkin workspace: 
```bash
cd ~/catkin_ws
catkin_make
```

### Building Packages

```bash
cd ~/catkin_ws
catkin_make
catkin_make install  # (optionally)
```

### rosnode
Supported commands:
```bash
rosnode info    print information about node
rosnode kill    kill a running node
rosnode list    list active nodes
rosnode machine list nodes running on a particular machine or list machines
rosnode ping    test connectivity to node
rosnode cleanup purge registration information of unreachable nodes
```

### rostopic
Supported Commands:
```bash
rostopic bw     display bandwidth used by topic
rostopic delay  display delay for topic which has header
rostopic echo   print messages to screen
rostopic find   find topics by type
rostopic hz     display publishing rate of topic
rostopic info   print information about active topic
rostopic list   print information about active topics
rostopic pub    publish data to topic
rostopic type   print topic type
```

### rosmsg

Show information about a message type.

```bash
rosmsg show <msg_name>
```

### rqt_graph
```bash
rqt_graph
```

### roslaunch

Add a node to a launch file:

```xml
<node name="name" pkg="<package_name>" type="<file_name>" output="screen" />
```

Include another launch file:

```xml
<include file="$(find <package_name>)/launch/<launch_file_name>" /> 
```
