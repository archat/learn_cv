# Convolutions

Now that we know what filters (kernels) are, how do we actually apply them to an image? The mathematical operation is called **Convolution**.

## The Convolution Operation

A convolution is fundamentally a sliding window operation. We take our small matrix (the filter/kernel) and "slide" it over the large image matrix. At every position, we perform an element-wise multiplication and sum the results.

### Step-by-Step

Let's illustrate with an example. Suppose we have a $$5 \times 5$$ image matrix $$I$$ and a $$3 \times 3$$ kernel $$K$$.

1.  **Place the filter**: Place the $$3 \times 3$$ kernel over the top-left corner of the image (covering a $$3 \times 3$$ grid of pixels).
2.  **Multiply Element-Wise**: Multiply the value of each kernel cell with the value of the image pixel directly beneath it.
3.  **Sum**: Sum up all 9 products to produce a single number.
4.  **Record**: Place this single number in the corresponding position (top-left) of a new "output" matrix.
5.  **Slide and Repeat**: Slide the filter one pixel to the right and repeat steps 2-4. Once you reach the end of the row, slide the filter back to the left but down one pixel, and continue.

### Convolution Hyperparameters

There are several parameters that control the behavior of a convolution operation:

#### 1. Padding

When a filter slides over an image, you'll notice it can't quite center itself on the border pixels without falling off the edge. This means the output matrix will be *smaller* than the input image matrix.

**Padding** solves this by adding extra rows and columns around the edge of the input image, typically filled with zeros ("Zero Padding"). This allows the filter to center on the original border pixels and keeps the output spatial dimensions the same as the input.

#### 2. Stride

The **Stride** is the number of pixels by which the filter shifts or "slides" at each step.

*   A stride of $S=1$ means sliding one pixel at a time (most common).
*   A stride of $S=2$ means skipping a pixel, which results in an output matrix that is roughly half the size of the input. This is a common way to downsample an image.

## Summary

The result of a convolution operation is a new matrix (often called a **feature map** or **activation map**) that highlights the specific features the kernel was designed to detect. For example, if we use an edge-detection kernel, the resulting feature map will show bright pixels where edges exist in the original image.

But what if, instead of manually designing these kernels, we could have a computer *learn* the best kernels for a given task? Enter the [Convolutional Neural Network](../cnn/intro.md).
