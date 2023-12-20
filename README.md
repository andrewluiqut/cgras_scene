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
virtual joint, trolley, world, fixed

#### Planning Groups
Add group 1
- Group name: manipulator
- Kinematic Solver: KDLKinematicsPlugin 
- Keep default values in other fields
- Add Joints: from shoulder_pan_joint to ee_control_joint
- Edit manipulator kinematic chain: nothing
- Set Base link: trolley
- Set Tip link: tool0
- Subgroup: enclosure

Add group 2
- Group name: enclosure
- Kinematic Solver: Nil
- Keep default values in other fields
- Add Links: flange to ee_control_link

#### Define Robot Poses
Define stow and home pose

#### Define End Effectors
- ee, enclosure, wrist_3_link, manipulator

#### Define Passive Joints
Skip it

#### Generate Configuration Files
Set the configuration package save path to another package folder (not cgras_scene).
Use cgras_scene_config

## Start Moveit Manipulator

roslaunch cgras_scene_config demo.launch rviz_tutorial:=true

# Compass Setup Robot Model URDF Example

https://gramaziokohler.github.io/compas_fab/0.21.1/examples/03_backends_ros/08_ros_create_moveit_package_from_custom_urdf.html