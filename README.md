# 🚦 Automated Traffic Control System (ATCS)

[![License](https://img.shields.io/badge/License-Custom--Restricted-red)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/downloads/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-orange.svg)](https://github.com/ultralytics/ultralytics)

---

## 📌 About

**ATCS** is an AI-powered, real-time traffic control system that uses computer vision and deep learning to intelligently manage traffic lights. It dynamically prioritizes lanes based on vehicles, pedestrians, and emergency vehicles  ensuring safe, fair, and efficient urban traffic flow.

Automated Traffic Control System using YOLOv8 , Python , Computer Vision, this project implements a real time intelligent traffic control system that uses deep learning and image processing to optimize traffic signal decisions dynamically .

---

## 🧠 Project Description

The Automated Traffic Control System (ATCS) addresses traffic congestion by integrating:

 Key features : 
1.  Object detection : Vehicles , Pedestrians and Emergency Vehicles 
2.  **Priority Calculation Algorithms** factoring in vehicles, pedestrians, emergency response, and starvation handling
3.  Resolves Starvation Problem 
4.  Highest priority given to the emergency vehicles 
5.  Custom Simulation 

 Technologies used : 
1. **YOLOv8 (via Ultralytics) for real time object detection .**
2. OpenCV for image handling .
3. Python for decision making logic and data processing .
4. NumPy for numerical operations . 
6. A custom **Tkinter-based GUI** for simulation and monitoring

 It’s designed to simulate real-world signal control and can be extended for smart city infrastructure.


## 🚀 Features

- 🧠 Real-time object detection with YOLOv8
- 🆘 Emergency vehicle override (absolute priority)
- 🔄 Starvation & red-light penalty-based fairness
- 🧪 Custom simulation using images/videos/datasets
- 🖥️ Tkinter GUI with real-time decision display
- 📁 Optional data export for analysis

---

## 🧰 Technologies Used

| Tool | Purpose |
|------|---------|
| **Python 3.7+** | Programming Language |
| **YOLOv8** | Object Detection |
| **OpenCV** | Image/Video Processing |
| **NumPy** | Array & Logic Calculations |
| **Tkinter** | GUI Interface |
| **Pillow (PIL)** | Image Handling in GUI |
| **PyTorch** | DL backend for YOLOv8 |
| **Matplotlib / Pandas** | Optional reporting & plots |

---

## 🛠️ Installation

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/Automated-Traffic-Control-System.git
cd Automated-Traffic-Control-System
```
### 2. Install Required Packages
Install the following packages using `pip`:
```
pip install opencv-python numpy pillow ultralytics tk
```

#### **Breakdown of Packages:**
| Package | Purpose |
|---------|---------|
| `opencv-python` (cv2) | Computer vision (video/image processing, object detection) |
| `numpy` | Numerical computations (array operations, image handling) |
| `pillow` (PIL) | Image processing for Tkinter GUI |
| `ultralytics` (YOLOv8) | Deep learning-based object detection (vehicles, pedestrians) |
| `tk` (Tkinter) | GUI framework (pre-installed with Python) |


#### Optional Packages (for advanced analysis)
```
pip install matplotlib pandas scipy
```
- **`matplotlib`**: Used for data visualization (if generating graphs).
- **`pandas`**: For structured data analysis (if exporting reports).
- **`scipy`**: Advanced mathematical computations (if needed for simulations).

### 3. GPU Acceleration (if applicable)
For **faster YOLOv8 detection**, install **PyTorch with CUDA** (if you have an NVIDIA GPU):
```
pip install torch torchvision --extra-index-url https://download.pytorch.org/whl/cu117
```
*(Replace `cu117` with your CUDA version if different.)*

### **4. Download YOLOv8 Weights (Automatically Handled)**
The project uses **YOLOv8n (nano model)** for object detection. The weights (`yolov8n.pt`) are automatically downloaded when you first run the code:

```
from ultralytics import YOLO
```
model = YOLO('yolov8n.pt')  # Auto-downloads if not found


### **5. Verify Installation**
Run this Python snippet to check if all dependencies are installed:

```
import cv2
import numpy as np
from PIL import Image
import tkinter as tk
from ultralytics import YOLO
```
print("All dependencies installed successfully!")

### **Troubleshooting**
1. **If OpenCV fails to install**, try:
   
   ```
   pip install opencv-python-headless
   ```
   
3. **If Tkinter is missing** (common on Linux):

   ```
   sudo apt-get install python3-tk
   ```
   - Debian/Ubuntu
   ```
   sudo dnf install python3-tkinter
   ```
   - Fedora
   
5. **If YOLO fails to download weights**, manually download `yolov8n.pt` from [Ultralytics GitHub](https://github.com/ultralytics/ultralytics) and place it in the project directory.

### **Final Notes**
- **OS Compatibility**: Works on **Windows, macOS, and Linux**.
- **Python Version**: Requires **Python 3.7+**.
- **Hardware**: Runs on CPU by default, but GPU (CUDA) is recommended for real-time video processing.


## ✅ Usage Instructions
### Launch the App
```bash
python ATMS02.py
```

## ✅ Supported Inputs

- 🖼️ **Upload Images** (2 to 4 lanes)
- 🎥 **Upload Traffic Video Files**
- 📁 **Use Dataset for Simulation**
- 🔧 **Customize Lane Data Manually**

---

### How it works : 
- Upload Traffic Images from local device (min. 2 or max. 4) required to depict 2-4 lanes of a road.
OR
- Upload Traffic Video. 
- Custom simulate the number of lanes , vehicles , pedestrians and emergency vehicles .
OR 
- Upload a traffic dataset.
- Object Detection using YOLOv8 : Identifies and counts vehicles, pedestrians, and emergency vehicles in each lane.

## 🧮 Priority Logic :  

```mathematica
Priority Score =
  (1.0 × Vehicle Count) +
  (0.5 × Pedestrian Count) +
  (100 × Emergency Vehicles) +
  Starvation Boost +
  Red-Light Penalty
```
   - Starvation factor: Lanes waiting too long receive a boost (0.2 points per second)
   - Red light duration penalty: Additional priority for lanes stuck at red light

---

## 🚦 Traffic Signal Decision Logic
**Also designed powerful fairness mechanisms like `🚫 starvation control` and `🚦 red-light 
priority boosts`, ensuring `no lane is left behind` — even the `less busy lanes eventually get 
their fair chance!`**

- 🚦 **Highest Priority** = Green Signal
- ⏳ **Starved Lanes** gradually gain increased priority over time, To prevent starvation, lanes that don't get green light accumulate additional priority over time.
- 🚑 **Emergency Vehicle** detection results in an **instant override** , Emergency vehicles automatically get highest priority regardless of other factors.

---

## 🖼️ Screenshots

![Demo](https://github.com/user-attachments/assets/bc4dd431-4dd4-4bb5-bfa6-03dfa9033f6d)


### 🧠 Detection Output  

![Traffic Summary](https://github.com/user-attachments/assets/4b718fc8-ea33-4631-ba3e-ecc289a2ff0b)

### 💻 GUI Display  

![Realtime](https://github.com/user-attachments/assets/929c5f53-8f56-4bb3-93be-8f6a3ad049e6)
![Data Analysis](https://github.com/user-attachments/assets/f5749106-c5e6-41bd-9789-a839dc029679)

### 🚨 Emergency Trigger  

![Emergency Trigger](https://github.com/user-attachments/assets/e7791900-e5f1-4d8e-8faa-91cfbbaa45ca)

---

## 🧭 Architecture Diagram

![Diagram](https://github.com/user-attachments/assets/7baaeeba-778a-4c94-aad6-92af2ea23d32)


---

## 📈 Sample Output Table

| 🚥 Lane | 🚗 Vehicles | 🚶 Pedestrians | 🚑 Emergency | 🧮 Status     |
|--------:|------------:|---------------:|-------------:|----------------------:|
| 1       | 8         | 1              | 1            | RED                  |
| 2       | 6           | 3              | 2            | RED                 |
| 3       | 9          | 8              | 4            | Green                  |
| 4       | 6           | 1              | 1            | RED       |

---

## Traffic Simulation

### Custom Traffic Simulation
![Custom Traffic Simulation](https://github.com/user-attachments/assets/1749f5ed-cb08-4dd8-9cf0-fda684e59631)
![Custom Traffic Simulation Overview](https://github.com/user-attachments/assets/47a3b757-df9c-4d43-9eaf-32394fb6aa9f)

### Traffic Management Overview
![Traffic Management Overview](https://github.com/user-attachments/assets/646dbcb9-05d1-428d-92ee-84906185fec8)

### Traffic Data Analysis
![Traffic Data Analysis](https://github.com/user-attachments/assets/37c4cddc-21a3-44df-a9aa-9482deaa8361)

### Decision Explanation
![Decision Explanation](https://github.com/user-attachments/assets/f1137d7f-1606-4dfb-9570-7b9e511f18c7)

### Traffic Management System Report
![Traffic Management System Report](https://github.com/user-attachments/assets/16198172-c6e1-43df-b59a-5518f27dad1d)
![Analysis Report 2](https://github.com/user-attachments/assets/fe0ba65d-af5a-4da0-8942-32d97dad1426)

### Traffic Flow Visualization
![Traffic Flow Visualization](https://github.com/user-attachments/assets/6249768d-d515-4de7-a966-12bca78b239a)

---

## 🔮 Future Enhancements

- 🎤 **Siren Detection** using advanced audio classification  
- 🌧️ **Weather-aware Object Detection** models for rain, fog, and snow  
- 🧠 **Predictive Traffic Flow Models** using time-series forecasting  
- 🌐 **Real-time Live CCTV Stream Integration** with cloud support  
- 🛰️ **Multi-Junction Green Wave Planning** for traffic signal synchronization  
- 🖥️ **Web-Based Dashboard** using React for frontend and Flask for backend  

---

## 📄 License

This project is protected by a **Custom "All Rights Reserved" License**.

> 🚫 Unauthorized use, modification, distribution, or publication is strictly prohibited.  
> 📧 For licensing inquiries, contact: **[samhd8991@gmail.com](mailto:samhd8991@gmail.com)** **[anirbandas2647226@gmail.com](mailto:anirbandas2647226@gmail.com)**


---



