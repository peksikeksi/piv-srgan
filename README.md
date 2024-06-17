# SRGAN for Particle Image Velocimetry (PIV)

## Overview
This project implements a Super-Resolution Generative Adversarial Network (SRGAN) to enhance the resolution of Particle Image Velocimetry (PIV) data. The goal is to upscale images from 64x64 pixels to 256x256 pixels, improving the visualization and analysis of fluid flow data. This project serves as an interesting experiment to explore the capabilities and limitations of using SRGAN for upscaling flow data.

## What is Particle Image Velocimetry (PIV)?
Particle Image Velocimetry (PIV) is an optical measurement technique used in fluid mechanics to visualize and analyze fluid flow. The process involves seeding a fluid with tracer particles that follow the motion of the fluid. By capturing successive images of these particles and analyzing their movement, it is possible to determine the velocity field of the fluid flow. [3]

## What is SRGAN?
Super-Resolution Generative Adversarial Network (SRGAN) is a type of neural network designed to enhance the resolution of images. SRGAN is particularly known for its ability to generate high-resolution images from low-resolution inputs by preserving finer details and textures, making it a powerful tool in image super-resolution tasks.
### How SRGANs work?
SRGAN is composed of two primary components: a generator network and a discriminator network, which are trained in an adversarial manner.
* __Generator Network__: The generator takes a low-resolution image as input and attempts to produce a high-resolution version of the image. It is typically constructed using deep convolutional neural networks (CNNs) and employs various techniques such as residual blocks and upsampling layers to enhance the image quality.
  
* __Discriminator Network__: The discriminator evaluates the authenticity of the generated high-resolution image by distinguishing it from real high-resolution images. It acts as a binary classifier, predicting whether an image is real (from the dataset) or fake (generated).

* __Adversarial Training__: The generator and discriminator are trained simultaneously in a game-like scenario where the generator aims to produce realistic high-resolution images to fool the discriminator, while the discriminator strives to correctly identify real and fake images. This adversarial process helps the generator learn to create more accurate and detailed high-resolution images over time.

### Advantages
SRGANs are capable of producing images with high detail that closely resemble the original high-resolution images. It excels at preserving textures and fine details, which are often lost in traditional upscaling methods. 

### Challenges
Adversarial training can be unstable and requires careful tunning of hyperparameters to achieve optimal results. Training SRGANs is computationally intensive and requires significant processing power. It is also challenging to ensure that the model doesn't overfit on the training data.

## Dataset
The dataset used in this project is sourced from the paper "Dense motion estimation of particle images via a convolutional neural network" published in Experiments in Fluids, 2019. The dataset includes synthetic particle image pairs and their corresponding ground-truth motion fields. [1] For more information on the dataset, go to the original authors page [2].

## Findings
The results, while not as outstanding as initially hoped, offered several valuable insights:
1. Model Stability: The training process revealed that the model was relatively unstable, with the discriminator loss often converging too quickly. This rapid convergence suggests potential issues with the adversarial training balance, which can lead to mode collapse where the generator produces limited variety in the outputs.
  
2. Performance: Despite the instability, the experiment demonstrated that SRGAN could still generate high-resolution flow data images. However, the quality and consistency of these images were not sufficient for practical application, indicating a need for further refinement.
   
3. Training Duration: The model was trained for only 10 epochs. Given the complexity of the task and the size of the dataset, this duration might have been insufficient for the model to fully learn and generalize the features necessary for high-quality upscaling.

## Future Work
To address the challenges observed and build upon the initial findings, several future directions are planned:

1. Hyperparameter Tuning:
   * Experimentation with Learning Rates: Adjusting the learning rates of both the generator and discriminator to ensure neither network converges too quickly.
   * Optimization of Beta Parameters: Exploring different values for beta_1 in the Adam optimizer to stabilize training.
   * Extended Training Period: Increasing the number of training epochs to allow the model more time to learn and stabilize.
2. Scaling Factor:
   * Different Scaling Ratios: Testing different upscaling factors beyond the current 4x to identify the optimal scaling limit for flow data without significant loss of accuracy or detail.
3. Advanced Network Architectures:
   * Exploring New Architectures: Experimenting with advanced architectures, such as GAN variants with more sophisticated loss functions or additional regularization techniques, to enhance model stability and performance.
4. Regularization and Loss Functions:
   * Improved Loss Functions: Incorporating more complex loss functions, such as perceptual loss or feature matching loss, to improve the quality of the generated images.
   * Regularization Techniques: Applying regularization methods like dropout or weight decay to prevent overfitting and enhance generalization.

By pursuing these future directions, the goal is to enhance the stability and performance of the SRGAN model for upscaling PIV data, ultimately achieving higher quality and more reliable results. This ongoing work aims to push the boundaries of what is possible in the field of super-resolution and flow data analysis.



## References and Cool Links
[1] [Dense motion estimation of particle images via a convolutional neural network, Exp Fluids, 2019](https://link.springer.com/article/10.1007/s00348-019-2717-2)

[2] [PIV dataset for neural network training](https://github.com/shengzesnail/PIV_dataset)

[3] [Particle image velocimetry](https://en.wikipedia.org/wiki/Particle_image_velocimetry)

[4] [Image upscaling with SRGAN](https://medium.com/@sridhargkumar11/image-upscaling-with-srgan-17ce0ec8aa62)

[5] [SRGAN Paper Explained](https://medium.com/@ramyahrgowda/srgan-paper-explained-3d2d575d09ff)

[6] [Neuralearn](https://www.youtube.com/@neuralearn)
