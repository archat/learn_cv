# DINO

**DINO** (Self-Distillation with No Labels) is a self-supervised learning method for Vision Transformers developed by Meta AI (formerly Facebook AI).

## What is Self-Supervised Learning?

Historically, training vision models like CNNs required massive datasets with manual, human-provided labels (e.g., ImageNet, where humans labeled 14 million images into 1000 categories).

**Self-Supervised Learning (SSL)** aims to remove the need for human labels. Instead, the model learns by solving "pretext tasks" using only the raw data itself as supervision.

## How DINO Works

DINO stands for **Di**stillation with **No** labels. It uses a student-teacher architecture:

1.  **Two Networks**: We initialize two identical Vision Transformers (a Student network and a Teacher network).
2.  **Different Views**: We take a single image (e.g., a photo of a dog) and create two different views of it (e.g., cropping one to only show the dog's face, and another showing the whole dog).
3.  **Forward Pass**: The Student gets View A, and the Teacher gets View B.
4.  **Distillation**: The Student is trained to predict the output of the Teacher network. In other words, the student learns to say: "Even though I only see the face, I know this is the same object that you see in the global picture."
5.  **Stop-Gradient**: To prevent the networks from collapsing (e.g., both just outputting zero for every image), the Teacher is *not* updated via backpropagation. Instead, its weights are updated as an exponential moving average (EMA) of the Student's weights.

## The Magic of DINO

What makes DINO remarkable is its emergent properties. Even though it is trained without a single human label, a DINO Vision Transformer:

*   **Learns Segmentation**: If you visualize the self-attention maps of a DINO model, it automatically learns to tightly segment objects from their background. It *discovers* the concept of an object boundary purely organically.
*   **Strong Feature Extractor**: DINO features are incredibly powerful. You can take a pre-trained DINO model and use it for downstream tasks like classification or detection, often beating supervised models.

DINO showed that Transformers, when paired with self-supervision, can understand the visual world in a much deeper and more structured way than supervised CNNs. Next, we will look at [CLIP](clip.md), which connects vision with language.
