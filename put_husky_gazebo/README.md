# put_husky_gazebo

## Launch files

Run launch file for gazebo simulation. The default environment is empty world and the simulation is with gui off. 

### GUI ON/OFF
```bash
ros2 launch put_husky_gazebo gazebo.launch.py gui:=<true/false>
```

### GUI ON/OFF
Only few arguments are yet available in the command line to change. If you want to change other argument, you should for now edit `robot_description_content` command as shown below.

```python
# Get URDF via xacro
    robot_description_content = Command(
        [
            PathJoinSubstitution([FindExecutable(name="xacro")]),
            " ",
            PathJoinSubstitution(
                [FindPackageShare("put_husky_description"), "urdf", "put_husky.urdf.xacro"]
            ),
            " ",
            "name:=husky",
            " ",
            "prefix:=''",
            " ",
            "is_sim:=true",
            " ",
            "is_space_mate:=true",
            " ",
            "gazebo_controllers:=",
            config_husky_velocity_controller,
        ]
    )
```

*TO DO*:
- parametrize arguments for the simulation outside the code
- add different gazebo worlds