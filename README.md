Aim : To autonomously navigate a UAV on SITL (Simulation) from one Geo-location location to another using velocity control.]


---

### 🎯 1. Project Overview & Objective

https://drive.google.com/file/d/1UQLE_VFid4VfbiwtULZnfQjpxyQ_QdOY/view?usp=drive_link

### 📂 2. Final Submission Files

> https://drive.google.com/drive/folders/1U_QMxKVFdiSoD_aGBrwNgvl3jO-7IR2w?usp=sharing
> 
- PYTHON FILES
    
    **Python Script (`.py`):**   https://drive.google.com/file/d/1FE0w9xtOb1e8eexQ_8R3FROmOtZCjmS-/view?usp=drive_link
    
- SIMULATION LOGS
    
    **Simulation Log (`.log` or `.txt`):** 
    
    https://drive.google.com/file/d/1YjBT_sO3-OfxZmuc2PeOESib_qL0XwTG/view?usp=drive_link
    

### ✍️ 3. Detailed Explanation of Work

### **a. Approach & Logic**

This project was about making a drone fly autonomously in a simulation, without using any controller or joystick. This can be used to test simulations before programming actual drone.

### What will the drone to do:

1. **Take off** to a height of 10 meters
2. **Fly to a specific GPS location**
3. **Land** safely

### Tools used:

- **SITL (Software In The Loop)** – Simulates the drone on our computer
- **ArduPilot** – The autopilot system that runs the drone
- **DroneKit (Python)** – Python library to write drone code
- **MAVProxy** – Shows drone position and status in real-time

### Steps followed:

1. Set up the software (SITL, ArduPilot, MAVProxy, Python)
2. Wrote a Python script using DroneKit
3. Launched the simulated drone using a command
4. Ran script to make the drone:
    - Arm → Take off → Fly → Land

### **b. Key Calculations & Formulas**

### **1. Distance Between Two Locations (GPS)**

To know how far the drone is from the target point, we used a distance formula (called Haversine formula) based on latitude and longitude.

```python
def get_distance(loc1, loc2):
    # Returns distance in meters between two GPS points
```

### **2. Altitude Check Before Hovering**

We checked if the drone reached the correct height (e.g., 10 meters):

```python
if current_altitude >= 9.5:
    print("Reached target altitude")
```

### **c. Code Structure**

### **Import Libraries**

These are tools (like `DroneKit` and `time`) we need in Python.

```python
from dronekit import connect, VehicleMode, LocationGlobalRelative
import time
```

### 2. **Connect to Simulated Drone**

This line connects our Python code to the simulated drone:

```python
vehicle = connect('127.0.0.1:14550', wait_ready=True)
# this is default virtual port
```

### **3. Arm and Take Off**

We define a function that:

- Arms the motors
- Takes off to 10 meters

```python
def arm_and_takeoff(target_altitude):
    # Set mode, arm, and take off
```

### 4. **Navigate to a GPS Point**

This moves the drone to a specific location:

```python
vehicle.simple_goto(LocationGlobalRelative(lat, lon, 10))
```

### 5. **Land**

Once the task is done, we safely land:

```python
vehicle.mode = VehicleMode("LAND")
```

6. **Close Connection**

After landing, we disconnect from the drone:

```python
vehicle.close()
```

**Final Flow (in simple terms):**

Start → Connect to drone → Arm → Take off to 10m
→ Go to GPS point → Wait/Hover → Land → Stop

### **d. Challenges Faced & Solutions**

https://drive.google.com/drive/folders/1kWCZckyGEDxMFP7vd0riWqQ5hk-s5Gil?usp=drive_link

---
### 4. GLIMPSES\

https://drive.google.com/drive/folders/1Ppawf8Rsh0m3wO6bP7ITtObRWjktPYZE?usp=drive_link
