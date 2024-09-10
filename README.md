# Person Detection and Tracking with YOLOv5 and DeepSort

## Overview

This project is designed to detect, track, and assign unique IDs to persons (such as therapists and children) in a video. The goal is to analyze the behavior and interactions between individuals, specifically focusing on therapists and children. The model uses YOLOv5 for object detection and DeepSort for tracking the detected individuals, ensuring each person is assigned a unique ID that remains consistent throughout the video.

## Features

- **Person Detection:** Utilizes YOLOv5 for detecting persons in each frame of the video.
- **Person Tracking:** Uses DeepSort to track detected individuals across frames, ensuring consistent ID assignment.
- **ID Assignment:** Ensures that each person is given a unique ID, which is consistent across frames. The ID is incremented sequentially for each new person detected.
- **Error Handling:** The code includes robust error handling for issues related to detection, tracking, and saving outputs.
- **Output Generation:** Saves a video with bounding boxes and IDs overlaid on detected individuals and stores images of each detected person.

## Installation

To run this project, you need to install the necessary Python packages. You can install the required dependencies using the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

## How It Works
1. **YOLOv5 Detection**
The model uses YOLOv5 to detect persons in each frame of the video. The model is pre-trained and is loaded using torch.hub. Each detected person is assigned a bounding box.

2. **DeepSort Tracking**
DeepSort is employed to track the detected individuals across frames. The tracker assigns a unique ID to each person, ensuring that the ID is consistent throughout the video.

3. **ID Management**
To ensure that each person in the same frame has a unique ID:
The frame_used_ids set is utilized to keep track of the IDs used in each frame.
If a detected person has an ID that has already been used in the same frame, the system skips assigning that ID to another person, ensuring uniqueness.

4. **Image Saving**
For each detected person, an image is saved in a designated folder with their unique ID. This allows for further analysis and validation of the detection and tracking process.

5. **Output Video**
The processed video, with overlaid bounding boxes and IDs, is saved and displayed using IPython's display function within a Kaggle notebook environment.

## Notes for YOLO and Output Paths

- **Ensure the Path for YOLO**: Verify the path where YOLO is loaded. Adjust the path settings as needed based on the environment where the code is running, especially if using Kaggle.

- **Starting IDs**: Ensure that each video starts ID numbering from 1. IDs should be reset for each new video.

- **Kaggle Environment Paths**: Be aware that paths may differ when running on Kaggle. Ensure that paths are correctly set according to the Kaggle environment.

- **Output Path for YOLO**: Review and adjust the output path for YOLO. Ensure the output directory settings are correctly configured and make necessary changes based on the current directory settings.