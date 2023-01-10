# put-husky
Custom packages for Clearpath Husky A200 with how-to guide

# Prerequisites

Prepare your robot aaccording to the instructions in the Clearpath tutorial [here](https://clearpathrobotics.com/assets/guides/foxy/husky/index.html). You should have Ubuntu 20.04 and ROS2 Foxy installed before following the tutorial.

# ESA Cognition ROS2 packages

```sh
mkdir -p ~/put_husky_ws/src
cd ~/put_husky_ws/src
git clone https://github.com/PPI-PUT/put-husky.git
cd ..
rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y
colcon build --symlink-install
source install/setup.bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
echo "source ~/put_husky_ws/install/setup.bash" >> ~/.bashrc
ros2 run husky_bringup install
```
