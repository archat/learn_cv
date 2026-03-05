# Image Classification

Image Classification is the foundational task in computer vision. The goal is simple: given an image, assign it a single label (class) from a predefined set of categories.

For example, given an image of a handwritten digit, classify it as "$0$", "$1$", ..., or "$9$".

## The Pipeline

A typical image classification pipeline using a CNN looks like this:

1.  **Input Image**: Let's say a $224 \times 224$ RGB image ($224 \times 224 \times 3$).
2.  **Feature Extraction**: The image passes through several Convolutional, ReLU, and Pooling layers. The spatial dimensions shrink, but the number of channels (feature maps) increases as the network learns more complex features.
3.  **Flattening**: The final 3D tensor (e.g., $7 \times 7 \times 512$) is flattened into a 1D vector.
4.  **Classification Head**: The flattened vector passes through one or more Fully Connected layers.
5.  **Output Probabilities (Softmax)**: The final layer has one neuron per class. We apply the **Softmax** function to convert the raw outputs (logits) into a probability distribution.

### Softmax Function

The Softmax function ensures that the outputs for all classes sum up to $1.0$ ($100\%$).

$$ \text{Softmax}(x_i) = \frac{e^{x_i}}{\sum_{j=1}^{C} e^{x_j}} $$

Where $C$ is the total number of classes.

## Famous Categorization Architectures

Over the years, several CNN architectures have defined the state-of-the-art in classification, mostly driven by the ImageNet Large Scale Visual Recognition Challenge (ILSVRC):

*   **LeNet-5 (1998)**: One of the earliest CNNs, designed for handwritten digit recognition (MNIST).
*   **AlexNet (2012)**: Ignited the deep learning boom. It consisted of 5 convolutional layers and 3 fully connected layers, trained on GPUs.
*   **VGGNet (2014)**: Showed that deeper networks (16 or 19 layers) using very small ($3 \times 3$) convolution filters perform better.
*   **ResNet (2015)**: Introduced **Residual Connections** (skip connections), allowing networks to be incredibly deep (e.g., 50, 101, or 152 layers) without suffering from the vanishing gradient problem.

While classification tells us *what* is in an image, it doesn't tell us *where* it is. For that, we need [Object Detection](object_detection.md).
