script

# Imports

* for image display: image, os, pyplot, cv2
* for math: keras, numpy
* dataset: mnist

The basic structure of logic comes from Frinedly Introduction

# Real Images

this function is designed to both import mnist by default, and allow a folder path filled with image files to be converted into ndarrays

Whichever we do is saved to image list


This displays a random image from the list

* it is not yet set to be limited to the range of the image list's length


# Preprocessing

* This gives all images a uniform format, and turns their integer values into float decimals
  * as this is often the format models need.

Default 48x48 is a quickly calculated size good for testing
-  any desired resolution can be set

This displays the same image as the Real Image test, to assure the preproccesing works.

Completing this task and having it function helped me fully understand what a preprocessor is for, and how it works.
* It's all about using uniformly formatted data when training, for fewer potential "break points."


# Generator

recieves the input shape in order to create images of the same resolution as the preprocessed images, for uniformity.
* I have them both recieve the same variable, so they're the same

After reshaping the ndarrays, almost all code is actually preserved from the original project, as numpy's ndarrays are evry flexible with mathematic operations.

I just made sure everything respected the new array shapes, which is why width/height are class attributes

# Discriminator

Similar to Generator, class attribute holds the dimensions.

The same changes made to generator are applied to discriminator, for the most part.
* exception is bias is a constant, rather than array.
  * will be worth investigating, once I can evaluate results properly.

# Training

1. choose hyperparameters
1. create class objects for both discriminator and generator
1. create lists to track resultant error.

Part of the reason for the 48x48 resolution is that significant increases in image size create significant increases in training time.
* similarly, I had to reduce the number of epochs and not use the entire dataset while testing, as the number of operations multiplies all of them, resulting in exponentially increasing train times.

Now this architecture only performs basic forward propagations, and is not properly deep convolutional.

In order to make this Deep Convolution, and not just a GAN

* apply convolutional layering, based on the projects from recent weeks
* That will take a significant review to fully understand how to impliment in that way.
* I will likely need to convert the training to be handled by tensorflow or keras in order for more effective understanding of training results.
* It was simply too late in the project when I realized I had completely missed utilizing these modules.

# Results

Before realizing I was in the wrong dirrection, I had attempted to repurpose the error graphs provided to respect a flattened array of the generator and discriminator's error. The results were not especially useable, and this is part of what made me realize I was doing the wrong thing entirely.

With more time, it should be possible to transpose this logic into keras layers trained using the same interweaving of errors, if keras does not already have systems dedicated to doing this already.

Upon restructuring the project with keras, the entirity of image generation via generator after training will be different from how things started.
