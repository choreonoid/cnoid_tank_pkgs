# cnoid_tank_pkgs
![cnoid_tank](.image/cnoid_tank.png)

This package contains the package for ROS integrated Choreonoid Tank model.

# Dependencies
- [choreonoid:master](https://github.com/choreonoid/choreonoid)
- [choreonoid_ros:dev/ros-control](https://github.com/RyodoTanaka/choreonoid_ros/tree/dev/ros-control)  
  The pull request is on : https://github.com/choreonoid/choreonoid_ros/pull/5
- [rtf_test_plant:master](https://github.com/choreonoid/rtf-test-plant)

# Install
```bash
mkdir <cnoid_ws>/src -p
cd <cnoid_ws>/src
git clone --recursive https://github.com/choreonoid/choreonoid.git
git clone --recursive -b dev/ros-control https://github.com/RyodoTanaka/choreonoid_ros.git
git clone --recursive https://github.com/choreonoid/rtf-test-plant.git
# Above 3 git clone commands will be replaced with vcs commands, after marging the PR for choreonoid_ros
git clone --recursive -b dev/launch-update https://github.com/RyodoTanaka/cnoid_tank_pkgs.git
cd <cnoid_ws>
rosdep update
rosdep install -i -y -r --from-paths src
catkin config --cmake-args -DBUILD_SCENE_EFFECTS_PLUGIN=ON -DBUILD_WRS2018=ON -DBUILD_ROS_TANK=ON -DUSE_PYTHON3=OFF -DUSE_PYBIND11=ON -DBUILD_PYTHON_PLUGIN=ON -DBUILD_PYTHON_SIM_SCRIPT_PLUGIN=ON -DENABLE_PYTHON=ON -DBUILD_COLLISION_HANDLER_SAMPLE=ON -DBUILD_CONTACT_FORCE_EXTRACTION=ON -DBUILD_TRACKED_VEHICLE_SAMPLE=ON -DCMAKE_BUILD_TYPE=Release
catkin build
source devel/setup.bash
```

# Execute
## 1. Launch Choreonoid
```bash
cd <cnoid_ws>
source devel/setup.bash
roslaunch cnoid_tank_bringup choreonoid.launch
```

## 2. Launch Rviz
After pushing the start button on choreonoid GUI, launch following.
```bash
cd <cnoid_ws>
source devel/setup.bash
roslaunch cnoid_tank_bringup display.launch
```
