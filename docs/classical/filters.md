# Image Filters

Image filtering is a classic computer vision technique used to enhance, blur, sharpen, or extract edges from images. Filters are essentially mathematical operations applied to an image matrix. 

## The Intuition

Since images are matrices (grids of pixel values), we can alter the image by modifying the pixel values based on the values of the surrounding pixels.

A **filter**, also known as a **kernel**, is a small matrix (like a $$3 \times 3$$ or $$5 \times 5$$ grid) of numbers. We slide this filter over the original image, perform a mathematical operation (usually a dot product), and output a new value for a new "filtered" image.

## Types of Filters

### 1. Smoothing (Blurring) Filters

Smoothing filters are used to reduce noise or "blur" an image. They work by replacing a pixel's value with an average (or weighted average) of its neighbors.

#### Example: Mean Filter (Averaging)

A 3x3 Mean filter kernel looks like this:

$$
K = \frac{1}{9} \begin{bmatrix}
1 & 1 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1
\end{bmatrix}
$$

When applied, this kernel replaces the center pixel with the simple average of all 9 pixels in its neighborhood.

### 2. Sharpening & Edge Detection Filters

Instead of averaging, these filters calculate the **differences** between adjacent pixels to highlight sudden changes in intensity (edges).

#### Example: Sobel Filter (Edge Detection)

The Sobel operator is designed to detect vertical and horizontal edges separately.

**Vertical Edge Filter (Sobel X):**
$$
G_x = \begin{bmatrix}
-1 & 0 & +1 \\
-2 & 0 & +2 \\
-1 & 0 & +1
\end{bmatrix}
$$

**Horizontal Edge Filter (Sobel Y):**
$$
G_y = \begin{bmatrix}
-1 & -2 & -1 \\
 0 &  0 &  0 \\
+1 & +2 & +1
\end{bmatrix}
$$

By finding edges, classical algorithms can start figuring out the shapes of objects—like recognizing a car by the sharp edges that form its rectangular shape and circular wheels.

## How are Filters Applied?

Filters are applied via a mathematical operation called **Convolution**. We will explore exactly how this mathematical operation works in [Convolutions](convolutions.md).
