I did manage to run the basic GAN structure in a way that would train without error.

Preprocessor worked perfectly, so images can be prepared to be trained.

## Main topics

model convergence
* I was not able to get observable results from training, but was able to confirm training was happening without crashing, as it was able to perform the trainig without erroring out (it was originally raising errors of misaligned arrays.)

training time
* One *can* preprocess images to over 100 pixels squared, but this massively increases required training time to the point it's useless for testing. I'd underestimated the multiplicative effect. For this reason, I chose `48x48` as default resolution to work with.
* Due to the extraordinary size of the MNIST dataset, I tested this with only the first 200 images when using CPU for testing.

image quality
* Unfortunately