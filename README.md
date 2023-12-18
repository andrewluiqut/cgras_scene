# Scene Model Specification

### Prepare URDF file for the Scene Model
 
Build URDF file from XACRO files and validate the URDF file by visualize 
```
rosrun xacro xacro --inorder -o all.urdf all.xacro

check_urdf all.urdf  
```

### Display Scene in RViz

```
cd ~/cgras_moveit_ws
cakin_make

source devel/setup.bash
roslaunch cgras_scene display.launch 
```

## Create Moveit Package

```
roslaunch moveit_setup_assistant setup_assistant.launch

```
#### Self-Collision
Press Generate Collision Matrix button

#### Virtual-joints
Skip it

#### Planning Groups
Add group 1
- Group name: manipulator
- Kinematic Solver: KDLKinematicsPlugin 
- Keep default values in other fields
- Add Kin. Chain button and Expand All
- Set Base link: trolley (or base_link?)
- Set Tip link: tool0

Add group 2
- Group name: camera_enclosure
- Kinematic Solver: Nil
- Keep default values in other fields
- Add Links button
- Select the link defined in gripper.xacro (enclosure and ee_control_link)

#### Define Robot Poses
Define home pose

#### Define End Effectors
- End-effector name: camera_enclosure, group name: camera_enclosure, parent link: tool 0

#### Define Passive Joints
Skip it

#### Generate Configuration Files
Set the configuration package save path to another package folder (not cgras_scene).
Use cgras_scene_config

## Start Moveit Manipulator

roslaunch cgras_scene_config demo.launch rviz_tutorial:=true

# Compass Setup Robot Model URDF Example

https://gramaziokohler.github.io/compas_fab/0.21.1/examples/03_backends_ros/08_ros_create_moveit_package_from_custom_urdf.html