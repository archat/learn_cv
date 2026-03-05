# Object Detection

While Image Classification answers the question "What is in this image?", Object Detection answers both **"What is it?"** and **"Where is it?"**.

The goal of object detection is to draw a **Bounding Box** around all objects of interest in an image and assign a class label to each bounding box.

## Anatomy of a Detection

For a single detected object, the model must output:
1.  **Class ID**: E.g., label 2 (represents 'car').
2.  **Confidence Score**: E.g., $0.95$ ($95\%$ sure it's a car).
3.  **Bounding Box Coordinates**: Usually four numbers $(x_{\text{min}}, y_{\text{min}}, x_{\text{max}}, y_{\text{max}})$ or $(x_{\text{center}}, y_{\text{center}}, \text{width}, \text{height})$.

Since there can be any number of objects in an image (0, 1, or 100), this makes the output of the CNN variable, which is a harder problem than simple classification.

## Evolution of Object Detection

Detection algorithms are generally split into two categories:

### Two-Stage Detectors (e.g., R-CNN, Faster R-CNN)

These models separate the process into two clear stages:
1.  **Region Proposals**: The network scans the image and proposes thousands of regions (boxes) where an object *might* be located. This is separated from classification.
2.  **Classification**: Each proposed region is cropped and passed through a CNN to classify what is inside the box and refine its coordinates.

**Pros**: Highly accurate.
**Cons**: Slow. They are often not suitable for real-time applications like self-driving cars.

### One-Stage Detectors (e.g., YOLO, SSD)

"You Only Look Once" (YOLO) and Single Shot MultiBox Detector (SSD) revolutionized the field. Instead of having a separate region proposal stage, these networks treat detection as a single regression problem.

1.  The image is divided into a grid (e.g., $13 \times 13$).
2.  Each grid cell predicts a fixed number of bounding boxes (with confidence scores) and class probabilities *simultaneously* in one single forward pass of the network.

**Pros**: Exceptionally fast, enabling real-time detection (e.g., 60+ FPS on a GPU).
**Cons**: Historically slightly less accurate than two-stage detectors on very small objects, though the gap has narrowed significantly with newer versions (YOLOv8, YOLOv10).

## Beyond Bounding Boxes

Bounding boxes are great, but they are coarse. If you draw a box around a person, a lot of the background is still inside the box. 

What if we want to know *exactly* which pixels belong to the object? For that, we turn to [Image Segmentation](segmentation.md).
