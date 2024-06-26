# atlas-gan

Generative Adversarial Networks.

Course written by Kush Aswani.

**Contents**
- [atlas-gan](#atlas-gan)
- [DCGAN](#dcgan)
    - [Imageset import:](#imageset-import)
- [Notes from Resources](#notes-from-resources)
  - [A Friendly Introduction to Generative Adversarial Networks:](#a-friendly-introduction-to-generative-adversarial-networks)
- [Functions](#functions)
- [Classes](#classes)
- [Training](#training)




# DCGAN

Colab Code is being worked on [here](https://colab.research.google.com/drive/1NA0OC1-2ocgxEiNO--E7BGnhutgOILcZ?usp=sharing)


Imports

```
# Imports
from PIL import Image
import os
import keras
import numpy as np
from numpy import random
import cv2
from matplotlib import pyplot as plt
%matplotlib inline

# import MNIST
from keras.datasets import mnist
```

### Imageset import:

`def import_images_as_list(folder_path=None):`

* If you do not provide a folder path, it will default to using the MNIST dataset from Keras.

`mnist` allows us to use `tensorflow.keras.datasets.mnist.load_data()`
* This returns a tuple of 2 tuples: `training` and `testing`
  * the first object in each is a list of images, and the second a list of labels.
* I exclusively used the 60000 test images, so I only cared about the first object in the first tuple: `(image_list, _), (_, _) = mnist.load_data()`
* Utilizing this function to load your imageset without an argument loads the mnist.
* Utilizing with a folder path (any `\` in name strings will need to be replaced with `\\`) as an argument will allow the use of any locally possessed imagesets.
  * the function will load `.png` and `.jpg` files within.
  * loaded images will be converted to `numpy.ndarray`s and put in a list `image_list` formatted the same way mnist delivers its images.


* `return`: the `image_list`
  * this `list` is filled with `numpy.ndarray`s, with each array representing the pixels of the input image.
  * The images within this list are not neccesarily the same size or shape. They are in the exact state they were uploaded in.

# Notes from Resources

## [A Friendly Introduction to Generative Adversarial Networks](https://www.youtube.com/watch?v=8L11aMN5KY8):

Generative Adversarial Networks (GANs) are made of tow parts: Generator, Discriminator.

* `Generator` spams creations, while `Discriminator` says "no, that's not right" until Generator gets one that is perfect.
  * vid describes it as counterfeiter (generator) and cop (discriminator). counterfeiter spams paintings and the cop says "no" until counterfeiter creates a perfect painting. counterfeiter learns from why the cop said "no."
* Discriminator is trained on inputs from real images and Generator images, learning how to discriminate the two.
* Generator is trained on trying to have discriminator classify it's images as "real."


------

https://wandb.ai/site can be used to compare different approaches you've made and see how they do.

* [tutorial](https://docs.wandb.ai/guides/integrations/pytorch)


# Functions

`def preprocess_images(images, new_width=48, new_height=48):`

This is a source-agnostic image preprocesssor. Given any list of imags, it'll return a list of those same images resized to given dimensions, and a record of previous and current dimensions, repsectively.
 * `images`: a `list` of images stored as `numpy.ndarrays`
    * Resizes the images with inter-cubic interpolation
    * Rescales all images to have pixel values in the range [0, 1], rather than [0, 255]
  * `Return`s a tuple of `(pimages, original_sizes, pimage_shapes)`:
    * `pimages`: a `numpy.ndarray` of shape `(ni, input_h, input_w, 3)` containing all preprocessed images
        * `ni`: the number of images that were preprocessed
        * `input_h`: the input height for the Darknet model Note: this can vary by model
        * `input_w`: the input width for the Darknet model Note: this can vary by model
        * `3`: number of color channels
  * `original_sizes` is a numpy.ndarray containing the original sizes, just in case.
  * `pimage_sizes`: tuple containing the uniform preprocessed height and width of the images.
    * essentially a tuple of the inputs, if they were provided. Otherwise `(48,48)`

# Classes

`class Generator():`
    `def __init__(self, input_shape):`

The generator class works very similarly to the example provided by [Luis Serrano](https://www.youtube.com/watch?v=8L11aMN5KY8)'s tutorial, but with the added ability to set an input shape.

This input shape can be the `pimage_sizes` tuple returned by the preproccessor, and will set what shape of image the generator creates.

`class Discriminator():`
    `def __init__(self, input_shape):`

The discriminator is extremely similar to the generator in source, setup, and use.

# Training

```

# Set random seed
np.random.seed(9)

# Hyperparameters
learning_rate = 0.01
epochs = 100

# The GAN
D = Discriminator(pimage_sizes)
G = Generator(pimage_sizes)

```

the above sets up a pair of objects that can be trained.

Then for as many epochs as desired, one can teach the discriminator, generate from the generator, and teach the discriminator:

```
        # Update the discriminator weights from real image
        D.update_from_image(pimage)

        # Pick a random number to generate a fake image
        z = random.rand()

        # Calculate the discriminator error
        errors_discriminator.append(sum(D.error_from_image(pimage) + D.error_from_noise(z)))

        # Calculate the generator error
        # my changes will make g.error return a 2D ndarray
        errors_generator.append(G.error(z, D))

        # Build a fake image
        noise = G.forward(z)

        # Update the discriminator weights from the fake image
        D.update_from_noise(noise)

        # Update the generator weights from the fake image
        G.update(z, D)

```
