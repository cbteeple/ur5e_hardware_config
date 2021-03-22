# NOT WORKING!!!!!

# UR5e with Robotiq 2Finger Grippers

This set of ROS packages contains the setup for connecting the Robotiq 2F grippers (via thier actual description) to a UR5e arm.

## Packages
- "_**ur5e_with_robotiq2f_85**_" contains the robot description (meshes, xacro, urdf, etc.)
- "_**ur5e_with_robotiq2f_85_moveit_config**_" conbtains the MoveIt! config for motion planning with the arm.
- "_**ur5e_with_robotiq2f_85_joint_limited_moveit_config**_" conbtains the MoveIt! config for motion planning with a joint limited arm arm.

**The packages were tested only in ROS Melodic, and they don't work yet.**

## Usage

```bash
roslaunch ur5e_with_robotiq2f_85_moveit_config ur5e_with_robotiq2f_85_moveit_planning_execution.launch limited:=false &
roslaunch ur5e_with_robotiq2f_85_moveit_config moveit_rviz.launch config:=true
```