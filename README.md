# atlas-gan

Generative Adversarial Networks.

Course written by Kush Aswani.

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

`def preprocess_images(self, images):`

 * `images`: a `list` of images stored as `numpy.ndarrays`
    * Resize the images with inter-cubic interpolation
    * Rescale all images to have pixel values in the range [0, 1]
  * `Return`s a tuple of `(pimages, image_shapes)`:
    * `pimages`: a `numpy.ndarray` of shape `(ni, input_h, input_w, 3)` containing all preprocessed images
        * `ni`: the number of images that were preprocessed
        * `input_h`: the input height for the Darknet model Note: this can vary by model
        * `input_w`: the input width for the Darknet model Note: this can vary by model
        * `3`: number of color channels
  * `image_shapes`: a numpy.ndarray of shape (ni, 2) containing the original height and width of the images
    * `2` => `(image_height, image_width)`
