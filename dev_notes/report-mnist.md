# Takeaways and Observations - MNIST

I did manage to run the basic GAN structure in a way that would train without error.

Preprocessor worked perfectly, so images can be prepared to be trained.

## Main topics

model convergence
* I was not able to get observable results from training, but was able to confirm training was happening without crashing, as it was able to perform the trainig without erroring out (it was originally raising errors of misaligned arrays.)

training time
* One *can* preprocess images to over 100 pixels squared, but this massively increases required training time to the point it's useless for testing. I'd underestimated the multiplicative effect. For this reason, I chose `48x48` as default resolution to work with.
* Due to the extraordinary size of the MNIST dataset, I tested this with only the first 200 images when using CPU for testing.

image quality
* Unfortunately, I was not yet able to have the generator produce a final image to view, but adding the code to do so should be very doable.


other relevant factors
* Improvements I'd like to make are as follows:
  1. add code to preview the final generator output.
      * this way, I will be able to ensure training results are actually imrpoving
  1.    convert the structure to [tensorflow](https://www.tensorflow.org/tutorials/generative/dcgan)
        * this is a much larger task, but will be necessary for the following:
        * Because I feel I fully understand the logic of steps taken, and they are each broken into pieces, I believe it is a very achievable revamp, given time.
  2. have complete training on custom imageset.
      * in particular, I want this to be set up to work even on very high quality images, which Tensorflow should enable via GPU usage.
      * the current project is using CPU only, so it ends up inefficient for the task.