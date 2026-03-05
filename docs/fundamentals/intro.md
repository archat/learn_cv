# What is Computer Vision?

Computer Vision (CV) is a field of artificial intelligence (AI) that trains computers and systems to derive meaningful information from digital images, videos, and other visual inputs—and take actions or make recommendations based on that information.

If AI enables computers to think, computer vision enables them to see, observe, and understand.

## How Computers See Images

To a human, an image is a collection of shapes, colors, and objects. To a computer, an image is nothing more than a structured grid of numbers (a matrix or tensor).

### Digital Images as Matrices

*   **Grayscale Images**: A grayscale image is represented as a 2D matrix of pixels. Each pixel has a value typically ranging from 0 (black) to 255 (white).
*   **Color Images (RGB)**: A color image is usually represented in the RGB (Red, Green, Blue) format. It consists of **three** 2D matrices stacked together, forming a 3D tensor of shape $$(Height \times Width \times Channels)$$. The channels correspond to the intensity of red, green, and blue.

### Example:

Consider a tiny $$5 \times 5$$ grayscale image. A computer sees this:

$$
\begin{bmatrix}
20 & 20 & 255 & 20 & 20 \\
20 & 255 & 255 & 255 & 20 \\
255 & 255 & 20 & 255 & 255 \\
255 & 20 & 20 & 20 & 255 \\
255 & 20 & 20 & 20 & 255 \\
\end{bmatrix}
$$

The goal of computer vision algorithms is to parse these massive grids of numbers and extract semantic meaning—like recognizing that the matrix above represents the letter "A" or detecting a pedestrian in a self-driving car's camera feed.

## The Evolution of Computer Vision

1.  **Classical Computer Vision**: Before deep learning, engineers manually designed "filters" or "feature extractors" to detect edges, corners, and shapes. Support Vector Machines (SVMs) and Random Forests were then used for classification.
2.  **Deep Learning (CNNs)**: The field revolutionized when Convolutional Neural Networks (CNNs) showed they could learn these filters automatically from massive amounts of data.
3.  **Modern Era (Transformers & Multimodal)**: Today, Vision Transformers (ViTs) and models like CLIP are pushing boundaries further, integrating text and image understanding.

Next, we will explore the foundations by looking at [Classical Image Processing](../classical/filters.md).
