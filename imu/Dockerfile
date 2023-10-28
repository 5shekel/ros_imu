FROM ros:kinetic
RUN apt-get update && \
    apt-get install -y \  
    ros-kinetic-rviz-imu-plugin \
    python-catkin-tools \
    python-pip

# Clone the ROS package
RUN mkdir -p /catkin_ws/src && \
    cd /catkin_ws/src && \
    git clone https://github.com/RoboticArts/ros_imu_bno055.git

# Build the ROS package
RUN /bin/bash -c "source /opt/ros/kinetic/setup.bash && \
                  cd /catkin_ws && \
                  catkin_make --only-pkg-with-deps ros_imu_bno055"

# RUN echo 'source /catkin_ws/devel/setup.bash' >> /ros_entrypoint.sh
RUN echo 'echo "Arguments received: $@"' >> /ros_entrypoint.sh

RUN pip install pyserial

# Set the entrypoint
ENTRYPOINT ["/ros_entrypoint.sh", "/bin/bash"]
# CMD [ "/bin/bash" ]


#entry point for catkin
# ENTRYPOINT ["/bin/bash", "-c", "source /root/catkin_ws/devel/setup.bash && roslaunch imu_ros imu.launch"]
# WORKDIR ~/catkin_ws