# Smart Fridge Project

This project involves the creation of a smart refrigerator system with food detection and face recognition for automatic door opening. The system includes a GUI application, powered by PyQt5, that displays the camera feed, detected foods, and recipe recommendations. The Raspberry Pi setup uses a YOLO model for food detection and a face recognition system for opening the fridge door.

## Components
- **Food Detection**: The Raspberry Pi uses the YOLO model to detect and classify food items inside the fridge.
- **Face Recognition**: A camera is used for face detection, which triggers the door to open automatically when a face is detected.
- **PyQt5 GUI**: Displays the live camera feed, detected food items, and recipe suggestions based on the food in the fridge.

## Features
- **Live Camera Feed**: Displays the real-time video feed from the camera inside the fridge.
- **Food Detection**: Identifies food items in the fridge using YOLO and shows the detected food items with their quantities in a table.
- **Recipe Suggestions**: Based on the detected food items, the system fetches recipe suggestions from the Spoonacular API.
- **Automatic Door Opening**: Uses face recognition to automatically open the fridge door when a face is detected.

## Prerequisites

### Hardware:
- Raspberry Pi (with a camera connected)
- Motor to control door opening and closing

### Software:
- Python 3
- PyQt5
- OpenCV
- Flask
- YOLO (Ultralytics version for object detection)
- mediapipe (for face detection)
- Requests (for API interaction)
- RPi.GPIO (for motor control)

## Setup Instructions

### Install Dependencies:
Install the necessary Python libraries by running the following commands:

```bash
sudo apt-get update
sudo apt-get install python3-pip
pip3 install opencv-python PyQt5 flask requests ultralytics mediapipe RPi.GPIO
```
# Raspberry Pi Setup

- Make sure the Raspberry Pi is set up with the camera module and the necessary motor control hardware for the door.
- Ensure that GPIO pins are correctly wired for motor control (as described in the `door_face_recognition.py`).

## Run the Food Detection Service

The Raspberry Pi will run a Flask web server for food detection and video streaming. Start the Flask app:

```bash
python3 food_detection.py
```
Run the GUI Application:

On your local machine, run the PyQt5 GUI application, which will connect to the Raspberry Pi's food detection service:

```bash
python3 app.py
```
Make sure to replace the IP address in `app.py` with the Raspberry Pi's local IP address.

## Code Overview
- **app.py**: A PyQt5 application that displays the camera feed and allows interaction with the food detection system.
- **door_face_recognition.py**: Manages the door's automatic opening and closing based on face recognition.
- **food_detection.py**: Runs a Flask API on the Raspberry Pi that handles food detection using YOLO and provides recipe suggestions via the Spoonacular API.

## IP Address Configuration
In `app.py`, ensure the `ip` variable is set to your Raspberry Pi's IP address:

```python
# Replace with your Raspberry Pi's IP address
ip = '192.168.x.x'  
```

## Motor Control
The motor control for door opening and closing is set up in door_face_recognition.py using GPIO pins. Ensure you have the motor and sensors wired to the correct pins as described in the script.

## Running the Application
1. Start the Flask server: This will handle the food detection and video streaming.

```bash
python3 food_detection.py
```
2. Run the PyQt5 app: Connects to the Raspberry Pi to display the camera feed and interact with the food detection service.

```bash
python3 app.py
```
## License
This project is licensed under the MIT License - see the LICENSE file for details.
