### Create a Custom Image with rosbridge_server Installed

Create a Dockerfile with the following content:

```dockerfile
FROM ros:melodic
RUN apt-get update && apt-get install -y ros-melodic-rosbridge-server
```

Build the custom image:
```bash
podman build -t custom_ros_melodic:latest .
```

Run a new container using the custom image in the same pod:
```bash
podman pod create --name ros_pod -p 11311:11311 -p 9090:9090
```

```bash
podman run -it --rm --pod ros_pod custom_ros_melodic:latest roslaunch rosbridge_server rosbridge_websocket.launch
```
