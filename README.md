# Image Processing for Self-Driving Cars in GTA V

An open-source implementation of image processing algorithms used in self-driving cars, demonstrated within the GTA V environment. This project showcases how automated vehicles perceive their surroundings, detect lanes, and identify obstacles.

## Project Overview

The primary goal of this project is to implement and demonstrate key algorithms used in autonomous vehicle navigation:
- **Lane Detection:** Utilizing the Hough Transform algorithm to identify road lanes.
- **Object Detection:** Using the YOLOv3 (You Only Look Once) algorithm to detect surrounding objects such as cars, pedestrians, and traffic lights.
- **Collision Warning:** A heads-up "Warning" system that alerts when the vehicle is too close to other objects.

GTA V is used as a simulation environment due to its high fidelity and realistic driving conditions.

## Features

- Real-time lane detection using Canny Edge Detection and Hough Transform.
- Robust object detection using YOLOv3.
- Integrated warning system for proximity to obstacles.
- Supports both live gameplay (GTA V) and pre-recorded video clips.

## Project Structure

```text
.
├── models/             # YOLOv3 weights, configuration, and class names
├── samples/            # Sample images and video clips for testing
├── src/                # Source code
│   ├── main.py         # Main integrated application
│   ├── lane_detection.py # Independent lane detection module
│   └── object_detection.py # Independent object detection module
└── requirements.txt    # Project dependencies
```

## Getting Started

### Prerequisites

- Python 3.x
- [OpenCV](https://opencv.org/)
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
- [Pillow (PIL)](https://python-pillow.org/)

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. **Download YOLOv3 Model Files:**
   The YOLOv3 weights and configuration files are not included in this repository due to size constraints. Please download them from the official [Darknet website](https://pjreddie.com/darknet/yolo/) and place them in the `models/` directory:
   - `yolov3.weights`
   - `yolov3.cfg`
   
   Ensure `coco.names` is also present in the `models/` folder.

### Running the Application

#### Using GTA V (Live)

1. Launch GTA V and set the resolution to **800x600**.
2. Set graphics settings (Shadows, Reflections, etc.) to **High**.
3. Position the game window in the **top-left corner** of your screen.
4. Run the main script:
   ```bash
   python src/main.py
   ```

#### Using Sample Videos

If you do not have the game installed, you can run the detection on sample video clips:
1. Ensure sample clips are in the `samples/` directory.
2. Run the object detection script:
   ```bash
   python src/object_detection.py
   ```

## Technical Details

### Lane Detection (Hough Transform)
The lane detection module follows these steps:
1. **Grayscale Conversion:** Converts the frame to grayscale.
2. **Gaussian Blur:** Reduces noise and smoothens the image.
3. **Canny Edge Detection:** Identifies edges in the frame.
4. **Region of Interest (ROI):** Isolates the portion of the frame where lanes are expected.
5. **Hough Line Transform:** Detects straight lines within the ROI.
6. **Slope Averaging:** Separates and averages the slopes to find the left and right lane boundaries.

### Object Detection (YOLOv3)
YOLOv3 is a state-of-the-art, real-time object detection system. In this project:
- The frame is resized to 416x416 and normalized.
- It passes through the Darknet-53 network architecture.
- Non-Maximum Suppression (NMS) is applied to filter redundant bounding boxes.
- Objects with a confidence score above 0.5 are displayed with their labels.

## Contributors
- Vrushit Patel
- Dhruv Pathak

## Acknowledgments
- Inspired by various open-source self-driving projects.
- Darknet (YOLOv3) by Joseph Redmon.
