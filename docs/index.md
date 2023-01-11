# PUT HUSKY 

# Setup robot

## Install ROS

Prepare your robot according to the instructions in the Clearpath tutorial [here](https://clearpathrobotics.com/assets/guides/foxy/husky/index.html). You should have Ubuntu 20.04 and ROS2 Foxy installed before following the tutorial.

## Network

### Basic network structure
 
![network](./imgs/network_setup.jpg)

Make sure that the onboard router has access to the internet during the setup.

Depending on your router and onboard PC you may need to follow instructions included in [NETWORK](NETWORK.md) section.

To follow with this instruction you don't have to follow official guidelines for setting network presented in [Clearpath documentation](https://clearpathrobotics.com/assets/guides/foxy/husky/HuskyNetwork.html).

## Sensors

All sensors connected to the robot should be correctly identified at the startup to avoid serial port conflicts. If you want to connect new sensor over USB port, follow the instructions in the [SENSORS](SENSORS.md).

# Setup software

## Husky packages

Packages can be built both on the onboard PC and user PC, however certain operations apply only to onboard PC.

### Build workspace
```sh
mkdir -p ~/put_husky_ws/src
cd ~/put_husky_ws/src
git clone https://github.com/PPI-PUT/put-husky.git
cd ..
rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y
colcon build --symlink-install
source install/setup.bash
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
echo "source ~/put_husky_ws/install/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
### Startup install
Run below script only on robot to enable ROS packages at the robot startup.
```sh
ros2 run husky_bringup install
```
To verify installation you can run
```sh
journalctl -a -b | grep ros
```
to make sure no errors occured during startup. You can compare you out put with ours at [example_output.md](example_output.md). Don't worry if you would not get information about Xsens IMU, which is installed at section [IMU integration](#imu-integration).


## Visualization

## IMU integration

