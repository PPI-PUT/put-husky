# put-husky
Custom packages for Clearpath Husky A200 with how-to guide

# Install ROS2 packages

```sh
mkdir -p ~/put_husky_ws/src
cd ~/put_husky_ws/src
git clone https://github.com/PPI-PUT/put-husky.git
cd ..
rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y
```
