# Segbot_ur5 Preparation

<img src="https://github.com/yding25/mobile_manipulator/blob/master/images/overview.png" width="40%" height="40%">

## Basics of UR5e
If this is your first time, please check the [Wiki page](https://github.com/bu-air-lab/UR5e_arm/wiki) of this repository to learn how to work with the arm


## Install ROS (melodic) on Ubuntu 18.04
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update
sudo apt install ros-melodic-desktop-full
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
source /opt/ros/melodic/setup.bash
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
sudo apt install python-rosdep
sudo rosdep init
rosdep update
```
Detailed instruction can be found at http://wiki.ros.org/melodic/Installation/Ubuntu

## Create catkin workspace
```
mkdir -p ~/catkin_ws/src
cd catkin_ws
```

## Add local environment path
```
echo "source /home/yan/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

## Install required libraries
```
sudo apt-get install ros-melodic-moveit && sudo apt-get install ros-melodic-ros-control ros-melodic-ros-controllers && sudo apt-get install ros-melodic-industrial-msgs && sudo apt-get install ros-melodic-soem
sudo apt update -qq
```

## Download source code
```
cd catkin_ws/src
sudo apt-get install zip unzip
wget https://www.dropbox.com/s/zwlx2p6wbqj5j2z/src.zip?dl=0
unzip src.zip
sudo rm -rf src.zip
```

## Update dependencies
```
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```
## Compile
``` 
catkin_make (or catkin build)
```
