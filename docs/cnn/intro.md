# Introduction to Convolutional Neural Networks

So far, we've seen how classical computer vision used manually designed filters to extract features like edges from images. This process of designing the right filter for the right task (like "find the bumper of a car") was called **Feature Engineering**, and it was incredibly difficult.

What if we didn't have to guess the numbers in our $3 \times 3$ matrix? Enter **Convolutional Neural Networks (CNNs)**.

## What is a CNN?

A CNN is a type of artificial neural network designed specifically for processing grid-like data, such as images.

Instead of hard-coding the filters, a CNN *learns* the values of these filters during the training process, using a learning algorithm like Backpropagation and Gradient Descent.

The network starts with random filter values. As it sees more images (like 10,000 pictures of cats and dogs), it slowly adjusts these filter values so that they extract the features that are most useful for distinguishing between a cat and a dog.

## Architecture of a CNN

A standard CNN is made up of several distinct layers:

### 1. Convolutional Layers

This is the core building block. A convolutional layer contains a set of learnable filters. When an image passes through this layer, the filters are convolved with the image (as described in the previous section) to produce **feature maps**.

*   **Early layers**: Learn simple, low-level features like edges, corners, and colors.
*   **Deeper layers**: Combine these low-level features to learn higher-level features, like "an eye," "a wheel," or "a texture."

### 2. Activation Layers (ReLU)

After a convolution, we almost always apply a non-linear activation function, most commonly the Rectified Linear Unit, **ReLU**.

$$ ReLU(x) = \max(0, x) $$

This simple function replaces all negative values in the feature map with zero. This introduces non-linearity into the network, allowing it to learn complex patterns instead of just linear transformations.

### 3. Pooling Layers

Pooling layers are used to systematically reduce the spatial dimensions (width and height) of the feature maps. This is also called **downsampling**.

*   **Max Pooling**: The most common type. It slides a window (e.g., $2 \times 2$) over the feature map and simply takes the maximum value in that window. Let's say we have the following $2 \times 2$ patch in a feature map:

$$
\begin{bmatrix}
1 & 5 \\
3 & 2
\end{bmatrix} \xrightarrow{\text{Max Pooling}} \text{takes the max value: } 5
$$

**Why Pool?**
-   **Reduces parameters**: Less computation is required in the following deeper layers.
-   **Translation invariance**: The network becomes slightly less sensitive to the exact position of a feature in the image (e.g., a cat's eye is still an eye even if it shifts by one pixel).

### 4. Fully Connected Layers

After passing through multiple rounds of Convolution $\rightarrow$ ReLU $\rightarrow$ Pooling, the feature maps are finally flattened into a 1D vector. This vector is passed into standard Fully Connected (Dense) layers—the same type found in a traditional Multilayer Perceptron. 

These dense layers take the high-level features extracted by the convolutional base and perform the final logic for [Image Classification](classification.md).
