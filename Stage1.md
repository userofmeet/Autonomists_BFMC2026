# Bosch Future Mobility Challenge 2025 - Stage 1 Status
**Team Name:** Autonomists
---

## 1. Project Vision
Our goal is to develop a robust 1:10 scale autonomous vehicle capable of navigating a complex smart-city environment. Our approach prioritizes **safety, modularity, and real-time responsiveness**. By leveraging ROS2 and advanced computer vision, we aim to solve urban mobility challenges like intersection management, pedestrian safety, and high-speed lane keeping.

---

## 2. Technical Architecture
We have designed a modular software stack based on the **Sense-Think-Act** paradigm.

### 2.1 Perception (Sense)
The vehicle perceives its environment through a monocular camera and IMU sensor fusion.
* **Lane Detection:** Uses Perspective Transform (Bird’s Eye View) and sliding window search to identify lane curvature.
* **Object Detection:** We utilize a **YOLOv8-tiny** model optimized via TensorRT for real-time detection of:
    * Traffic Signs (Stop, Priority, Parking, One-way).
    * Traffic Lights (State recognition via color masking and CNN classification).
    * Obstacles (Static cars and moving pedestrians).

### 2.2 Decision Making (Think)
The "Brain" of the vehicle consists of two layers:
* **Global Planner:** Processes the graph-based map provided by the Bosch Server to find the shortest path between coordinates.
* **Local Planner (Behavior Layer):** A Finite State Machine (FSM) that handles transitions between states (e.g., `LANE_FOLLOWING` -> `INTERSECTION_APPROACH` -> `WAITING_FOR_LIGHT`).

### 2.3 Control (Act)
* **Lateral Control:** A **PID Controller** or **Pure Pursuit Algorithm** calculates the required steering angle based on the error from the lane center.
* **Longitudinal Control:** Adaptive speed control based on detected signs (e.g., 50km/h limit) and proximity to obstacles.

---

## 3. Connectivity (V2X)
Our system integrates with the Bosch Smart City Server via a dedicated communication node:
* **Localization:** Subscribing to GPS/Initial position data for global path planning.
* **Traffic Lights:** Receiving real-time broadcast states to override local vision if visibility is low.
* **Feedback Loop:** Publishing vehicle telemetry (speed, current position) back to the server for monitoring.

---

## 4. Development Roadmap
| Phase | Focus | Deliverable |
| :--- | :--- | :--- |
| **Phase 1** | Simulation & Environment Setup | Gazebo/Rviz environment with basic lane following. |
| **Phase 2** | Perception Refinement | High-accuracy sign recognition (>95% mAP). |
| **Phase 3** | Integration & Hardware | Porting code to the 1:10 vehicle and tuning PID parameters. |
| **Phase 4** | Optimization | Reducing latency in the V2X communication loop. |

---

## 5. Software Stack
* **Language:** Python 3.10 / C++
* **Framework:** ROS2 Humble
* **Libraries:** OpenCV (Image Processing), PyTorch/TensorRT (Inference), NumPy (Math).
* **Simulation:** Gazebo, Foxglove Studio (Visualization).

---

## 6. Preliminary Control Code (Abstract)
```python
import cv2
import numpy as np

class AutonomousController:
    """
    Core Logic for BFMC Stage 1
    """
    def __init__(self):
        self.steering_angle = 0.0
        self.velocity = 0.0

    def get_steering_error(self, frame):
        # 1. Image Preprocessing (Canny & ROI)
        # 2. Lane Centroid Calculation
        # 3. Return error from image center
        pass

    def control_loop(self, error):
        # PID Logic
        # steering = Kp * error + Ki * integral + Kd * derivative
        pass

    def emergency_stop(self, obstacle_dist):
        if obstacle_dist < 0.2: # 20cm
            self.velocity = 0.0
```
