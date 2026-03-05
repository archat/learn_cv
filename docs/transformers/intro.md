# Vision Transformers (ViT)

For many years, the Convolutional Neural Network (CNN) was the undisputed king of computer vision. However, in 2020, researchers at Google introduced the **Vision Transformer (ViT)**, proving that an architecture designed originally for Natural Language Processing (NLP) could beat state-of-the-art CNNs in vision tasks.

## The Transformer Architecture

Transformers (like the architecture behind ChatGPT) rely entirely on a mechanism called **Self-Attention**. 

In NLP, a sentence is broken down into words (tokens). The self-attention mechanism allows the network to look at *all other words* in the sentence to understand the context of the *current word*, regardless of how far apart they are.

CNNs, on the other hand, have a limited "receptive field". A small $3 \times 3$ kernel can only see a tiny patch of the image at a time. To understand the relationship between pixels on opposite sides of an image, the CNN must be very deep.

## How ViT Works

The brilliance of the Vision Transformer lies in its simplicity: it treats an image exactly like a sentence of words.

1.  **Patch Extraction**: The input image (e.g., $224 \times 224$) is divided into a grid of non-overlapping "patches" (usually $16 \times 16$ pixels each).
2.  **Flattening**: Each $16 \times 16 \times 3$ patch is flattened into a single 1D vector. These patches are the "words" (tokens) of our image sentence.
3.  **Linear Projection**: These flattened patches are passed through a simple linear layer to embed them into a higher-dimensional space.
4.  **Positional Encoding**: Since Transformers process all tokens simultaneously (they don't know the order of "words"), we must add a positional embedding to each patch. This tells the network "This patch belongs in the top-left corner, and this one in the bottom-right."
5.  **Transformer Encoder**: The sequence of patches is passed through a standard Transformer Encoder (composed of Multi-Head Self-Attention layers and Multi-Layer Perceptrons).
6.  **Classification Head**: A special `[CLASS]` token is added to the beginning of the sequence. The output state of this specific token at the end of the transformer is used to predict the image class.

## Why are Transformers replacing CNNs?

*   **Global Context**: Thanks to self-attention, the ViT can integrate information from the entire image right from the very first layer, unlike CNNs that build context slowly over many layers.
*   **Scalability**: Transformers scale incredibly well with massive amounts of data and compute.

However, ViTs are notoriously data-hungry. They generally require much more training data than CNNs to achieve competitive performance, as they don't have the built-in assumption of translational invariance (the idea that a cat is a cat no matter where it is in the picture) that CNNs possess.

Next, we look at how Transformers unlock [Advanced Concepts](../advanced/dino.md) like self-supervised and multimodal learning.
