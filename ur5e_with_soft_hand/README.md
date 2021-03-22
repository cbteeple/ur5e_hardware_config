# UR5e with Soft Hand

This set of ROS packages contains the setup for connecting my standard soft hand (via placeholder geometry) to a UR5e arm.

## Packages
- "_**ur5e_with_soft_hand**_" contains the robot description (meshes, xacro, urdf, etc.)
- "_**ur5e_with_soft_hand_moveit_config**_" conbtains the MoveIt! config for motion planning with the arm.

**The packages were tested only in ROS Melodic.**

## Setup

### Set up your robot config
You can make changes to the placeholder geometry to suit your own needs

1. Build your ROS workspace: `catkin_make`
2. Edit "ur5e_with_soft_hand/urdf/_**measurement_tool.xacro**_" with the correct dimensions, masses, and inertias. This step is based on a great [tutorial from Compas](https://gramaziokohler.github.io/compas_fab/latest/examples/03_backends_ros/07_ros_create_urdf_ur5_with_measurement_tool.html).
3. Generate a URDF from the xacro: `rosrun xacro xacro -o ur5e_with_soft_hand.urdf ur5e_with_soft_hand.xacro`
4. Check that things are connected right: `roslaunch ur5e_with_soft_hand display.launch`

### Set up your MoveIt! config
If you make changes to your robot description, you also need to update the MoveIt! config package.

1. Open the MoveIt! setup assistant: `roslaunch moveit_setup_assistant setup_assistant.launch`
2. Click the button to "edit an existing package", and navigate to "_**ur5e_with_soft_hand_moveit_config**_".
3. Load files
4. Regenerate the self collision matrix
5. Change author data to your name and email.
6. Generate files (_When you do this, the setup assistant might complain about files that have been edited. In this package, I needed to edit some files to make them work with [ur_modern_driver](https://github.com/plusone-robotics/ur_modern_driver)_)

## Usage
Once these packages are updated to your liking, you can use them to do motion planning on the arm like normal.

```bash
roslaunch ur5e_with_soft_hand_moveit_config ur5e_with_soft_hand_moveit_planning_execution.launch limited:=false &
roslaunch ur5e_with_soft_hand_moveit_config moveit_rviz.launch config:=true
```