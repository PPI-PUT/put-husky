# Network settings
## ROS2 topics visibility
Usually during the startup the PC initializes sooner than the onboard router, which can cause to disruption in ROS topics communication.
To avoid situation, when topics are internally visible, but are not propagate through the network, one should delay the PC bootup until the router is up. In order to achieve this, you can change GRUB settings on the PC in the [following way][1].

```bash
sudo nano /etc/default/grub
```
Look for `GRUB_TIMEOUT=n` and change the value of `n` into desired delay in seconds. Once you're done, you need to save the file and run `sudo update-grub` to apply changes. After the robot restart the delay should be visible. In our case it is set 69 seconds. 

[1]:https://askubuntu.com/questions/1315810/add-delay-at-boot

## Unprivileged user
When installing the scripts for bootup initialization, one may loose certain privileges despite being the same user both during install and bootup. Therefore it is wise to add additional udev rule to avoid issues with USB/Serial communication as stated in this [article][2].
>Create a new file named “local.rules” in /etc/udev/rules.d/.<br>
>```
>cd /etc/udev/rules.d/
>sudo touch local.rules
>```
>In this file (edit with admin rights), add a new line:<br> `ACTION=="add", KERNEL=="dialout", MODE="0666"`.<br> This will make the “dialout” group available for all unprivileged users.


[2]:https://roboticsbackend.com/make-ros-launch-start-on-boot-with-robot_upstart/