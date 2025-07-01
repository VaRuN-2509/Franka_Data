# Franka_Data
This repo contains the required data needed for training diffusion policy on the real franka hardware.
Step by Step procedure to collect Data:
**1.Camera access and functioning:-**
    -> we use 3 Brio cameras for this purpose
    -> use cv2_enemurate libraryy to loop through camera_index
    -> refer to the file - human_collect_video

**2.Topic to gather data from**
    -> run the ros2 launch file - franka.bringup to start the hardware
    -> ros2 topic list : /dynamic_joint_states
    /franka_robot_state_broadcaster/current_pose
    /franka_robot_state_broadcaster/desired_end_effector_twist
    /franka_robot_state_broadcaster/desired_joint_states
    /franka_robot_state_broadcaster/external_joint_torques
    /franka_robot_state_broadcaster/external_wrench_in_base_frame
    /franka_robot_state_broadcaster/external_wrench_in_stiffness_frame
    /franka_robot_state_broadcaster/last_desired_pose
    /franka_robot_state_broadcaster/measured_joint_states
    /franka_robot_state_broadcaster/robot_state
    /franka_robot_state_broadcaster/transition_event
    /joint_state_broadcaster/transition_event
    /joint_states
    /parameter_events
    /robot_description
    /rosout
    /tf
    /tf_static

    -> subscribe to : /franka_robot_state_broadcaster/current_pose
                      /franka_robot_state_broadcaster/measured_joint_states
                      /franka_robot_state_broadcaster/desired_end_effector_twist

    -> refer to the file -> human_collect_pose


**3.File structure of collected data**
    -> We collected the data in zarr file format
  
 ├── data
 │   ├── eef_pose (1384, 7) float32
 │   ├── eef_velocity (1384, 6) float32
 │   ├── joint_pose (1384, 7) float32
 │   ├── joint_velocity (1384, 7) float32
 │   └── timestamp (1384,) float64
 └── meta
     └── episode_ends (14,) float32

