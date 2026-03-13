# Image Processing for Self-Driving in GTA V

This project implements computer vision algorithms to enable basic self-driving capabilities within the GTA V environment. It utilizes real-time image processing to detect lanes and surrounding objects, providing a foundation for automated navigation and obstacle avoidance.

## Project Overview

The core objective is to demonstrate how an automated vehicle perceives its environment. By scanning video frames in real-time, the application identifies driving lanes and classifies objects such as cars, pedestrians, and traffic lights. It also includes a proximity warning system to alert when obstacles are too close.

## Features

- **Real-time Lane Detection:** Uses the Hough Transform algorithm to identify and highlight road lanes.
- **Object Detection:** Implements the YOLOv3 (You Only Look Once) algorithm to detect and classify multiple objects in the frame.
- **Proximity Warning:** Triggers a "Warning !!!" message on-screen when a detected vehicle (car or truck) is dangerously close.
- **GTA V Integration:** Designed to capture and process gameplay from GTA V, providing a realistic simulation environment.

## Architecture & Algorithms

### 1. Lane Detection (Hough Transform)
- **Canny Edge Detection:** Identifies sharp changes in intensity to find potential edges.
- **Gaussian Blur:** Reduces noise and smoothens the image before edge detection.
- **Region of Interest (ROI):** Focuses processing on the area of the frame where lanes are most likely to appear.
- **Hough Line Transform:** Extracts straight lines from the edge-detected image to represent lane boundaries.

### 2. Object Detection (YOLOv3)
- **Deep Learning Model:** Utilizes a pre-trained YOLOv3 network for efficient, real-time object detection.
- **Bounding Boxes:** Draws rectangles around detected objects with classification labels and confidence scores.
- **Non-Maximum Suppression (NMS):** Filters redundant overlapping boxes to ensure each object is detected only once.

## Project Structure

```text
.
├── assets/
│   ├── clips/          # Sample video clips for testing
│   └── coco.names      # COCO dataset class names for YOLO
├── src/
│   ├── lane_detection.py    # Independent lane detection implementation
│   ├── object_detection.py  # Independent object detection implementation
│   └── self_driving.py      # Integrated lane and object detection
├── requirements.txt    # Python dependencies
└── README.md           # Project documentation
```

## Setup & Installation

### Prerequisites

- Python 3.x
- GTA V (optional, for real-time testing)

### Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download YOLOv3 Weights & Config:**
   The YOLOv3 model files are required for object detection. Download them and place them in the `assets/` directory:
   - [yolov3.weights](https://pjreddie.com/media/files/yolov3.weights)
   - [yolov3.cfg](https://github.com/pjreddie/darknet/blob/master/cfg/yolov3.cfg)

## Usage

### Running with Sample Clips
If you don't have the game, you can run the detection on sample clips provided in `assets/clips/`:
```bash
python src/object_detection.py
```

### Running with GTA V
1. Launch GTA V and set the resolution to **800x600**.
2. Position the game window in the **top-left corner** of your screen.
3. Run the integrated self-driving script:
   ```bash
   python src/self_driving.py
   ```

## Authors
- **Dhruv Pathak**
- **Vrushit Patel**

## License
This project is open-source and intended for educational purposes.
