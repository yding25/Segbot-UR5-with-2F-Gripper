# Preparation
<img src="https://raw.githubusercontent.com/yding25/pic_share/master/segbot_ur5.png" width="300" />

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
‼️please replace **'/home/yan'** with your own path.

## Install required libraries
```
sudo apt-get install ros-melodic-moveit && sudo apt-get install ros-melodic-ros-control ros-melodic-ros-controllers && sudo apt-get install ros-melodic-industrial-msgs && sudo apt-get install ros-melodic-soem
sudo apt update -qq
```

## Download third-party packages
```
cd catkin_ws/src
sudo apt-get install zip unzip
wget https://www.dropbox.com/s/yy4d88vktq1zk2s/segbot_ur5_third_party_packages.zip?dl=0
unzip segbot_ur5_third_party_packages.zip
sudo rm -rf segbot_ur5_third_party_packages.zip
```

## Download source code
```
wget https://www.dropbox.com/s/ybaxd77qdca3cdv/tamp_perception.zip?dl=0
unzip tamp_perception.zip
sudo rm -rf tamp_perception.zip
cd tamp_perception/src
chmod 777 -R *
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
