Install Ultralytics:

pip install ultralytics


Run Inference:

yolo predict model=your_weights.pt source=your_image.jpg
#or for video
yolo predict model=your_weights.pt source=your_video.mp4
Python usage:
Python

from ultralytics import YOLO

# Load a model
model = YOLO('your_weights.pt')  # load a custom model

# Predict with the model
results = model('your_image.jpg')  # predict on an image
