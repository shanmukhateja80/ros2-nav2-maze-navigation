# ros2-nav2-maze-navigation


Autonomous maze navigation using ROS2 Navigation2 stack.

https://github.com/shanmukhateja80/ros2-nav2-maze-navigation/blob/main/videos/maze_navigation_demo.webm

---

## System Overview

This project uses the following robotics components:

- **Gazebo** – Robot simulation environment
- **TurtleBot3** – Mobile robot platform
- **SLAM Toolbox** – Mapping and localization
- **ROS2 Navigation2 (Nav2)** – Autonomous navigation stack
- **RViz** – Visualization and goal interface

Navigation pipeline:

```

Gazebo Simulation
↓
SLAM Toolbox (Mapping)
↓
Saved Map
↓
Nav2 Navigation Stack
↓
Global Planner + Local Planner
↓
Robot Navigation to Goal

```

---

## Repository Structure

```

ros2-nav2-maze-navigation
│
├── maps
│   ├── maze_map.pgm
│   └── maze_map.yaml
│
├── worlds
│   └── maze.world
│
├── launch
│   └── turtlebot3_maze.launch.py
│
├── videos
│   └── maze_navigation_demo.webm
│
└── README.md

```

---

## Requirements

Operating System:

```

Ubuntu 22.04

```

ROS Distribution:

```

ROS2 Humble

```

Simulation:

```

Gazebo Classic

````

---

## Install ROS2

Follow the official ROS2 installation guide:

https://docs.ros.org/en/humble/Installation.html

---

## Install TurtleBot3 Packages

Create a workspace:

```bash
mkdir -p ~/turtlebot3_ws/src
cd ~/turtlebot3_ws/src
````

Clone TurtleBot3 repositories:

```bash
git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
```

Install dependencies:

```bash
cd ~/turtlebot3_ws
rosdep install --from-paths src --ignore-src -r -y
```

Build workspace:

```bash
colcon build
```

Source workspace:

```bash
source install/setup.bash
```

Set TurtleBot3 model:

```bash
export TURTLEBOT3_MODEL=burger
```

---

## Install Navigation2 (Nav2)

Install Nav2 packages:

```bash
sudo apt install ros-humble-navigation2
sudo apt install ros-humble-nav2-bringup
```

---

## Launch Gazebo Maze World

Run the TurtleBot3 maze simulation:

```bash
ros2 launch turtlebot3_gazebo turtlebot3_maze.launch.py
```

---

## Run SLAM Mapping

Launch SLAM Toolbox:

```bash
ros2 launch slam_toolbox online_async_launch.py
```

Drive the robot to create a map.

Save the map:

```bash
ros2 run nav2_map_server map_saver_cli -f maze_map
```

---

## Launch Navigation

Run Nav2 with the saved map:

```bash
ros2 launch nav2_bringup navigation_launch.py map:=maze_map.yaml
```

---

## Send Navigation Goal

Open RViz:

```bash
rviz2
```

Use the **2D Goal Pose tool** to send navigation goals.

The robot will autonomously navigate through the maze.

---

## Key Robotics Concepts Demonstrated

* ROS2 Navigation2 stack
* SLAM-based environment mapping
* Autonomous robot navigation
* Global and local path planning
* Robot localization
* Gazebo robotics simulation

---

## Technologies Used

* ROS2 Humble
* Navigation2 (Nav2)
* SLAM Toolbox
* Gazebo Classic
* RViz
* TurtleBot3
* Python

---

## Future Improvements

* Waypoint navigation
* Autonomous exploration
* Dynamic obstacle avoidance
* Integration with real robot hardware

---

## Author

Shanmukha Teja
Robotics Engineering | ROS2 Developer

---
