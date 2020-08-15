1. sudo docker run -itd --name szz --net=host --mount type=bind,source=/Users/szz/Documents/ros_ws,target=/root/ros_ws ct2034/vnc-ros-kinetic-full bash
2. apt-get update
3. apt-get upgrade
4. apt-get install net-tools wget curl nano inetutils-ping apt-rdepends
5. echo "source /opt/ros/kinetic/setup.bash" >> /root/.bashrc
6. source /root/.bashrc
7. rosdep update
8. mkdir ros_ws
9. cd ros
10. mkdir src
11. cd /root
12. mkdir Libs

## install Hokuyo

1. cd ros_ws/src
2. mkdir hokuyo
3. cd hokuyo
4. git clone https://github.com/ros-drivers/driver_common.git
5. git clone https://github.com/ros-perception/laser_proc.git
6. git clone https://github.com/ros-drivers/urg_c.git
7. git clone https://github.com/ros-drivers/urg_node.git
8.  cd /root/ros_ws
9.  catkin_make
10. cd /root

## install Cartographer

1. sudo apt-get install -y clang g++ git google-mock libboost-all-dev libcairo2-dev libcurl4-openssl-dev libeigen3-dev libgflags-dev libgoogle-glog-dev liblua5.2-dev libsuitesparse-dev ninja-build python-sphinx libpcl-dev ros-kinetic-pcl-conversions ros-kinetic-tf2-eigen
2. cd /root/Libs
3. git clone https://github.com/eigenteam/eigen-git-mirror.git
4. cd eigen-git-mirror
5. git checkout 3.2.7
6. mkdir build
7. cd build
8. cmake ..
9. make install
10. cp -r /usr/local/include/eigen3/Eigen /usr/local/include
11. cd /root/Libs
12. git clone https://github.com/ceres-solver/ceres-solver.git
13. cd ceres-solver
14. git checkout 1.13.0
15. mkdir build
16. cd build
17. cmake .. -G Ninja -DCX11=ON
18. ninja
19. sudo ninja install
20. cd /root/Libs
21. git clone https://github.com/google/protobuf.git
22. cd protobuf
23. mkdir build
24. cd build
25. cmake -G Ninja -DCMAKE_POSITION_INDEPENDENT_CODE=ON -DCMAKE_BUILD_TYPE=Release -Dprotobuf_BUILD_TESTS=OFF ../cmake
26. ninja
27. sudo ninja install
28. cd /root/Libs
29. git clone https://github.com/larics/cartographer_frontier_detection.git
30. cd cartographer_frontier_detection
31. cd cartographer
32. mkdir build
33. cd build
34. cmake .. -G Ninja -DCXX11=ON
35. ninja
36. sudo ninja install
37. cd ../..
38. cp -r cartographer_ros/ /root/ros_ws/src/
39. cd /root/ros_ws/
40. catkin_make
41. cd /root

## install rrt_exploration

1. apt-get install ros-kinetic-gmapping ros-kinetic-navigation python-opencv python-numpy python-scikits-learn ros-kinetic-kobuki ros-kinetic-kobuki-core ros-kinetic-kobuki-gazebo
2. cd /root/ros_ws/src
3. mkdir rrt_exploration
4. cd rrt_exploration
5. git clone https://github.com/hasauino/rrt_exploration_tutorials.git
6. cd /root/ros_ws
7. catkin_make
8. cd /root
9. mkdir .gazebo
10. cd .gazebo
11. mkdir models
12. cd models
13. wget http://file.ncnynl.com/ros/gazebo_models.txt
14. wget -i gazebo_models.txt
15. ls model.tar.g* | xargs -n1 tar xzvf
16. rm model.tar.gz.* 