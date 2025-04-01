# YOLOv8 Deployment and Inference

This README provides instructions on how to deploy and run YOLOv8 models locally for object detection.

## Prerequisites

* **Python:** Python 3.7 or later is required.
* **pip:** Python package installer.

## Installation

1.  **Install Ultralytics:**

    ```bash
    pip install ultralytics
    ```

## Running Inference

### Using the Command-Line Interface (CLI)

1.  **Place Your Weights:** Ensure your YOLOv8 weights file (`.pt`) is accessible.
2.  **Run Inference:**

    * **For an image:**

        ```bash
        yolo predict model=your_weights.pt source=your_image.jpg
        ```

    * **For a video:**

        ```bash
        yolo predict model=your_weights.pt source=your_video.mp4
        ```

    * Replace `your_weights.pt` with the path to your weights file and `your_image.jpg` or `your_video.mp4` with the path to your input.

    * **For a webcam:**

        ```bash
        yolo predict model=your_weights.pt source=0
        ```

3.  **Output:** The results, including bounding boxes, class labels, and confidence scores, will be displayed and saved. By default the results are saved into a runs/predict/ directory.

### Using Python

1.  **Import the YOLO class:**

    ```python
    from ultralytics import YOLO
    ```

2.  **Load the model:**

    ```python
    model = YOLO('your_weights.pt')  # Load your custom model
    ```

3.  **Perform inference:**

    ```python
    results = model('your_image.jpg')  # Predict on an image
    #or
    results = model('your_video.mp4') # Predict on a video

    #or
    results = model(0) #predict from webcam.
    ```

4.  **Process the results:**

    ```python
    for r in results:
        boxes = r.boxes  # Boxes object for bounding box outputs
        masks = r.masks  # Masks object for segmentation masks outputs
        probs = r.probs  # Class probabilities for classification outputs
        print(boxes) #print the boxes to the console.
        r.show() #show the resulting image/video with bounding boxes.
        r.save('results/')#save the resulting image/video with bounding boxes.

    ```

## Notes

* **Weights:** Make sure you have the correct YOLOv8 weights file (`.pt`).
* **Input:** Provide the correct path to your input image or video.
* **Dependencies:** Ensure all required dependencies are installed.
* **GPU Acceleration:** If you have a compatible NVIDIA GPU, YOLOv8 will automatically use it for faster inference.
* **Output:** The output will include bounding box coordinates, class labels, and confidence scores.
* **Customization:** Refer to the Ultralytics documentation for more advanced options and customization: [Ultralytics YOLOv8 Documentation](https://docs.ultralytics.com/)

## Example directory structure.
