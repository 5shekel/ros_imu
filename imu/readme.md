### Create a Custom Image with rosbridge_server Installed
https://github.com/RoboticArts/ros_imu_bno055

Build the image:
```bash
podman build -t imu_ros_kinetic:latest .
```

create a pod:
```bash
podman pod create --name ros_pod -p 11311:11311 -p 9090:9090
```

run the container:
```bash
podman run -it --rm --pod ros_pod custom_ros_melodic:latest /bin/bash
```

