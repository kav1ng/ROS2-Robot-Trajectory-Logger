##########ROS2 Robot Trajectory Logger ##########

A ROS2-based system that logs robot odometry data and visualizes the trajectory using Python.

---

## Features

* Subscribes to `/odom`
* Logs robot position (x, y) to CSV
* Runs full system using a single launch file
* Visualizes trajectory using Matplotlib

---

## Tech Stack

* ROS2 (Humble)
* Python (rclpy)
* Pandas
* Matplotlib

---

## Project Structure

```
data_ws/
 ├── src/data_logger/
 │    ├── data_logger/
 │    │    └── logger_node.py
 │    ├── launch/
 │    │    └── full_system.launch.py
 │    ├── package.xml
 │    └── setup.py
 ├── plot.py
 ├── trajectory.csv
 ├── requirements.txt

```
---

##  Setup

### 1. Create Workspace

```bash
mkdir -p ~/data_ws/src
cd ~/data_ws
colcon build
source install/setup.bash
```

---

### 2. Install Python Dependencies

```bash
pip3 install "numpy<2" pandas matplotlib
```

---

### 3. Set TurtleBot Model

```bash
export TURTLEBOT3_MODEL=burger
```

---

## Run the System (Single Command)

```bash
ros2 launch data_logger full_system.launch.py
```

This will:

* Launch Gazebo simulation
* Spawn TurtleBot3
* Start odometry logger
* Open teleop in a new terminal (GNOME)

---

## Control the Robot

Use keyboard in the teleop terminal:

```
i → forward  
j → left  
l → right  
k → stop  
```

---

## Generate Plot

After moving the robot:

```bash
cd ~/data_ws
python3 plot.py
```


## Output

* `trajectory.csv` → logged positions
* Plot window → robot trajectory visualization

---

##  Save Plot (Optional)

To save the plot image, add this in `plot.py`:

```python
plt.savefig("trajectory.png")
```

---
Kavin G
