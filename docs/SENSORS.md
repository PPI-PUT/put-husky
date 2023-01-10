## Adding new sensor (serial port device)
### Getting vendor ID 
```bash
udevadm info -a -p $(udevadm info -q path -n /dev/<serial port name>) | grep idVendor | head -1
```
Output:
```
ATTRS{idVendor}=="1546"
```
### Getting product ID
```bash
udevadm info -a -p $(udevadm info -q path -n /dev/<serial port name>) | grep idProduct | head -1
```
Output:
```
ATTRS{idProduct}=="01a9"
```

### Setting udev rules
Create file under `/etc/udev/rules.d` according to udev naming convention.<br>
> Files should be named xx-descriptive-name.rules, the xx should be chosen first according to the following sequence points:
>
> * < 60  most user rules; if you want to prevent an assignment being overriden by default rules, use the := operator. These cannot access persistent information such as that from vol_id; these cannot access persistent information such as that from vol_id
> * < 70  rules that run helpers such as vol_id to populate the udev db
> * < 90  rules that run other programs (often using information in the udev db)
> * \>=90  rules that should run last
    
So for example, create file `sudo nano /etc/udev/rules.d/55-your_sensor_name.rules` with the following content. Choose if it's ACM or USB interface.
```
KERNEL=="tty<ACM/USB>[0-9]*", SUBSYSTEM=="tty", ATTRS{idVendor}=="1546", ATTRS{idProduct}=="01a9", MODE="0666", SYMLINK="tty<your custom name>"
```