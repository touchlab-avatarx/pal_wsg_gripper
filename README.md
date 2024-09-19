# pal_wsg_gripper

This repository provides configurations, descriptions, and control setups for the WSG Gripper in a ROS1/ROS2 environment. It includes support for hardware interfaces, simulation in Gazebo, URDF descriptions, and fingertip sensors, making it suitable for both real and simulated robotic applications.

## Table of Contents
1. [ROS Control - Hardware Interface](#1-ros-control---hardware-interface)
2. [C++ API](#2-c-api)
3. [Configuration Files](#3-configuration-files)
4. [Launch Files](#4-launch-files)
5. [Example Usage](#5-example-usage)
6. [Dependencies](#6-dependencies)

---

## 1. ROS Control - Hardware Interface

### Effort Command, Position State, Velocity State
The `pal_wsg_gripper` repository integrates with ROS control, providing hardware interfaces that support:
- **Effort Command**: Allows setting the desired force for gripping objects.
- **Position State**: Provides the real-time position of the gripper.
- **Velocity State**: Reports the velocity of gripper movements.

These interfaces are essential for controlling the WSG Gripper in both hardware and simulated environments, allowing precise control over grip and release.

## 2. C++ API

The repository includes a C++ API that interacts with the WSG Gripper's hardware interface, enabling developers to communicate with the gripper for commands and feedback. This API simplifies gripper control and provides abstractions for interacting with the ROS control framework.

## 3. Configuration Files

### Configuration for Gripper and Controllers
- **Gripper Configuration**: The configuration files located in the `pal_wsg_gripper_controller_configuration/config` directory define the control parameters for the WSG Gripper. These include PID settings, sensor configurations, and controller parameters for both fingertip sensors and joint trajectory controllers.
    - `gripper_right_left_fingertip_sensor_controller.yaml`
    - `gripper_right_right_fingertip_sensor_controller.yaml`
    - `joint_trajectory_controllers.yaml`
    - `pids.yaml`

- **Gazebo Configurations**: Files related to simulating the gripper in Gazebo are located in `pal_wsg_gripper_description/gazebo`, including URDF configurations for realistic gripper behavior in the Gazebo simulator.

## 4. Launch Files

### Key Launch Files for the Gripper
This repository contains several launch files for different scenarios such as bringing up the gripper controllers, launching Gazebo simulations, and testing kinematics.

- **Gripper Controllers**:
    - `gripper_controller.launch`: Launches the WSG Gripper controller.
    - `gripper_fingertip_sensor_controller.launch`: Brings up the fingertip sensor controllers.

- **Simulation**:
    - `gripper_gazebo.launch`: Launches the gripper in a Gazebo simulation environment.
    - `gripper_spawn.launch`: Spawns the WSG Gripper in Gazebo.

- **Testing**:
    - `gripper_kinematics_test.launch`: Used for testing the kinematic model of the gripper.

Example usage to bring up the gripper controller:
```bash
roslaunch pal_wsg_gripper_controller_configuration gripper_controller.launch
```

For Gazebo simulation:
```bash
roslaunch pal_wsg_gripper_gazebo gripper_gazebo.launch
```

## 5. Example Usage

### Hardware Gripper Control
To control the real WSG Gripper:
1. Launch the gripper controller:
   ```bash
   roslaunch pal_wsg_gripper_controller_configuration gripper_controller.launch
   ```

2. Send commands using the appropriate ROS topics or services to control grip force and position.

### Simulating the Gripper in Gazebo
1. Launch the Gazebo environment:
   ```bash
   roslaunch pal_wsg_gripper_gazebo gripper_gazebo.launch
   ```

2. Control the gripper using the simulated environment through the provided controllers.

## 6. Dependencies

This repository requires several ROS packages to function correctly. The dependencies are listed in the `package.xml` files of each subfolder. They include:

### Core Dependencies:
- **ROS (Melodic, Noetic, or later)**: The primary ROS distribution for controlling and simulating the WSG Gripper.
- **Gazebo**: For simulating the gripper in a virtual environment.
- **Controller Manager**: To manage the ROS controllers associated with the gripper.
- **Robot State Publisher**: For publishing the state of the URDF-based robot model.

To install all required dependencies, run:
```bash
rosdep install --from-paths src --ignore-src -r -y
```
