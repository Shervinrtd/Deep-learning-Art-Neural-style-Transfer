# Deep Learning & Art: Neural Style Transfer

This repository contains an implementation of **Neural Style Transfer**, an algorithm created by Gatys et al. (2015). This project demonstrates how to generate novel artistic images by combining the "content" of one image with the "style" of another (e.g., a photograph painted in the style of Van Gogh).

##  Overview

Neural Style Transfer (NST) is an optimization technique used to blend three images:
1. **Content Image:** The image we want to preserve (e.g., a photo of a building).
2. **Style Image:** The reference image for the texture and brushstrokes (e.g., an artwork).
3. **Generated Image:** The final output initialized as noise or the content image and optimized to match the content of the first and the style of the second.

This implementation is based on the "Deep Learning & Art: Neural Style Transfer" assignment from the Deep Learning Specialization (Convolutional Neural Networks) by DeepLearning.AI.

##  Key Features

- **VGG-19 Architecture:** Uses a pre-trained VGG-19 network (trained on ImageNet) to extract feature maps.
- **Cost Functions:**
  - **Content Cost:** Preserves the structural content of the original image using activation maps from deeper layers.
  - **Style Cost:** Captures artistic style using Gram matrices of activation maps across multiple layers.
- **Optimization:** Uses gradient descent to update pixel values of the generated image directly, rather than updating network weights.
## Methodology
The algorithm works by calculating a total cost function $J(G)$ which is a weighted sum of the content and style costs:
$$J(G) = \alpha J_{content}(C,G) + \beta J_{style}(S,G)$$
- Transfer Learning (VGG-19)
We use the VGG-19 network, pre-trained on the ImageNet database. By accessing the intermediate layers of this deep network, we can extract high-level features (content) and low-level textures (style).
- Content Cost:
The content cost is calculated by comparing the activation maps of a hidden layer for the content image $C$ and the generated image $G$. It encourages the generated image to maintain the structural integrity of the original photo. Shallow layers tend to detect lower-level features like edges, while deep layers detect higher-level features like complex textures and objects.
- Style Cost:
The style representation is computed using the Gram Matrix of the activations from multiple layers. The style cost is defined as the distance between the Gram matrices of the style image $S$ and the generated image $G$ across various layers.
- Optimization:
Unlike standard deep learning training where we update network weights, here we freeze the network and update the pixel values of the generated image. We use the Adam Optimizer and TensorFlow's GradientTape to minimize the total cost.

##  Prerequisites
To run this notebook, you will need the following Python libraries:
- TensorFlow (2.x)
- NumPy
- SciPy
- Pillow (PIL)
- Matplotlib

##  References & Acknowledgements
- Original Paper: Leon A. Gatys, Alexander S. Ecker, Matthias Bethge, (2015). A Neural Algorithm of Artistic Style

- Network Architecture: Karen Simonyan and Andrew Zisserman (2015). Very deep convolutional networks for large-scale image recognition

- Course: Deep Learning Specialization by DeepLearning.AI on Coursera. This project is based on an assignment from the Convolutional Neural Networks course.

## License
This project is open source and available under the MIT License.
