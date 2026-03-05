# Image Segmentation

While Object Detection gives us bounding boxes, **Image Segmentation** is the process of partitioning an image into multiple segments (sets of pixels), assigning a label or class to *every single pixel* in the image.

## Types of Segmentation

There are three main types of image segmentation in computer vision:

### 1. Semantic Segmentation

In semantic segmentation, every pixel in the image is classified into one of the predefined categories (e.g., "car", "road", "sky", "tree"). 

However, all objects of the same class are treated as a single entity. For instance, if there are five cars in the image, all pixels belonging to those five cars are labeled "car". The network does *not* differentiate between Car 1, Car 2, or Car 3.

*   **Architecture Example**: **U-Net** (2015). Initially developed for biomedical image segmentation, U-Net features a "U-shaped" architecture with a contracting path (encoder) to capture context and a symmetric expanding path (decoder) that enables precise localization.

### 2. Instance Segmentation

Instance segmentation takes semantic segmentation a step further. Instead of just identifying the class of the pixels, it identifies individual *instances* of that class.

If there are five cars, the network will return a separate segmentation mask for Car 1, Car 2, ... Car 5. 

*   **Architecture Example**: **Mask R-CNN** (2017). This is an extension of Faster R-CNN (an object detector). It adds a third branch to the network that outputs a segmentation mask for each bounding box it detects.

### 3. Panoptic Segmentation

Panoptic segmentation is a combination of semantic and instance segmentation. It aims to assign a unique label to *every* pixel in an image:
*   Things that can be counted (cars, people, animals) get an **instance ID** (Instance Segmentation).
*   Amorphous "stuff" that cannot be easily counted (sky, grass, road) gets a **semantic class label** (Semantic Segmentation).

This provides the most complete and holistic understanding of an image possible.

## Beyond CNNs

For nearly a decade, CNNs and architectures built upon them (like YOLO, ResNet, U-Net, and Mask R-CNN) dominated computer vision. But recently, a new architecture has arrived from the Natural Language Processing (NLP) domain to challenge their supremacy: [Vision Transformers](../transformers/intro.md).
