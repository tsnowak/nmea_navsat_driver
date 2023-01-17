# Usage

### Build It
```bash
# install package dependencies, build the package, and source the environment
rosdep install -i --from-path src --rosdistro humble -y
colcon build --packages-select nmea_navsat_driver
. install/setup.bash
```

### Test It
```bash
## In the container in any directory
ros2 launch nmea_navsat_driver jonesy_nmea_tcpclient_driver.launch.py
```

# Status

> [Documentation of debugging issues](https://github.com/ros-drivers/nmea_navsat_driver/issues/160)

> Existing issues:
>- [ ] [NaN values are not handled correctly in ROS2 Humble](https://github.com/ros2/rosidl/issues/705) which causes issues like the following when the stream drops off.
>```
>[nmea_tcpclient_driver-1]   File "/opt/ros/humble/install/lib/python3.8/site-packages/sensor_msgs/msg/_nav_sat_fix.py", line 271, in altitude
>[nmea_tcpclient_driver-1]     assert value >= -1.7976931348623157e+308 and value <= 1.7976931348623157e+308, \
>[nmea_tcpclient_driver-1] AssertionError: The 'altitude' field must be a double in [-1.7976931348623157e+308, 1.7976931348623157e+308]
>[ERROR] [nmea_tcpclient_driver-1]: process has died [pid 345, exit code 1, cmd '/home/searobot/nmea_navsat_driver_ws/install/nmea_navsat_driver/lib/nmea_navsat_driver/nmea_tcpclient_driver --ros-args --params-file /home/searobot/nmea_navsat_driver_ws/install/nmea_navsat_driver/share/nmea_navsat_driver/config/jonesy_nmea_tcpclient_driver.yaml'].
>```