# UR5e Hardware Setups

This set of ROS packages contains the setup for connecting a UR5e arm to a few grippers/hands.

## Package Sets
- "_**ur5e_with_soft_hand**_": Connect a UR5e to a soft hand (via placeholder geometry)
- "_**ur5e_with_robotiq**_": Connect a UR5e to a Robotiq 2F_85 gripper (via placeholder geometry)
- "_**ur5e_with_robotiq2f**_": (**NOT WORKING YET**) Connect a UR5e to a Robotiq 2F_85 gripper (via the actual joint structure)


**The packages were tested only in ROS Melodic.**

## Usage
**A useful bash script to bring up planning and rviz with any moveit package:**

```bash
#!/bin/bash

roslaunch ${1}_moveit_config ${1}_moveit_planning_execution.launch limited:=false &
sleep 1
roslaunch ${1}_moveit_config moveit_rviz.launch config:=true &
sleep 1

wait $(jobs -p)
```

Svae this as "_bringup-planning.sh_"

For example:
- Just the UR5e: `bash bringup-planning.sh ur5_e`
- UR5e with soft hand: `bash bringup-planning.sh ur5e_with_soft_hand`
- UR5e with Robotiq 2F gripper placeholder `bash bringup-planning.sh ur5e_with_robotiq`
- UR5e with Robotiq 2F gripper `bash bringup-planning.sh ur5e_with_robotiq2f_85`
- Joint limited UR5e with Robotiq 2F gripper `bash bringup-planning.sh ur5e_with_robotiq2f_85_joint_limited`