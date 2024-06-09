# Gun Detection using YOLOv8

This repository contains code and instructions for fine-tuning a YOLOv8 model for gun detection using a dataset of 100,000 images. The training process leverages Roboflow for dataset management and augmentation to ensure model adaptability.

## Installation

To set up the environment for training and evaluation, follow these steps:

1. Clone the repository:

    ```sh
    git clone https://github.com/yourusername/gun-detection-yolov8.git
    cd gun-detection-yolov8
    ```

2. Install the necessary dependencies:

    ```sh
    pip install ultralytics==8.0.20
    pip install roboflow
    ```

3. Verify the installation:

    ```python
    import ultralytics
    ultralytics.checks()
    ```

## Dataset

The dataset used for training and evaluation is managed via Roboflow. Ensure you have an API key from Roboflow and replace the placeholder in the code with your actual key.

1. Download the dataset:

    ```python
    from roboflow import Roboflow
    rf = Roboflow(api_key="YOUR_ROBOFLOW_API_KEY")
    project = rf.workspace("guns-pfypn").project("gun-detection-4xyb0")
    dataset = project.version(3).download("yolov8")
    ```

## Training

To train the YOLOv8 model on the downloaded dataset, use the following command:

```sh
yolo task=detect mode=train model=yolov8s.pt data=path/to/your/data.yaml epochs=5 imgsz=800 plots=True
