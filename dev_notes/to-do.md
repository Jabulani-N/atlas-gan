# To-do List

- [ ] unchecked content

- [X] checked content

Colab Code is being worked on [here](https://colab.research.google.com/drive/1NA0OC1-2ocgxEiNO--E7BGnhutgOILcZ?usp=sharing)

# SETUP - MNIST GAN

- [x] find where I did the MNIST preprocessing before
* it's in supervised learning > object detection > [5-yolo.](https://github.com/Jabulani-N/atlas-machine_learning/blob/main/supervised_learning/object_detection/5-yolo.py)

- [x] document the variables, input names, and outputs so it can be read easily
- [x] copy that preprocessor code into current project

- [x] have AI write a check for making sure it is preprocessed correctly

  * unneeded, as I copied the function from my previous assignment that got full marks for preprocessing

- [x] find code to import image files as 3-color channels `numpy.ndarray` so I can use the precprocess function and it's output.

  * you may have it in the same previous YOLO project

## mnist importing

- [x] import mnist and define it as `images`
  * `(x_train, y_train), (x_test, y_test) = tensorflow.keras.datasets.mnist.load_data()`
  - [x] I need to find out what data type it is so I can put it through my preprocessing function
    * I've imported it up to `mnist` so we can shorthand it thusly.
    * `mnist.load_data()` returns ((`images`, `labels`),(`testing_data_images`, `testing_data_labels`))
      * `images` = 3D array
        * shape `(num_samples, 28, 28)` - `28x28` pixels.
          * one `28x28` array of pixels per image.
          * grayscale.
            * [x]  comment out the part of preprocessor that respects the 3 color channels and replace it with the one grayscale chanel
              * I looked at it after sleeping, and it's already shape-agnostic
              * I likely don't need to understand what the grayscale channels are doing, because the point is that it will perform the same math logic, but on the one channel
              * this is better, because all images in my own version will be color, so no point in doing hard work.,
      * **we can ignore testing data for this project**.
        * `testing_data` items are used for supervised learning models to be evaluated. they are arranged the same way as the `images` and it's `labels`, but are separate so you can judge a model's labelling accuracy on data it has yet to see.
- [x]  rewrite preprocess method into a strong, independant function.

## MNIST Preprocessing

* The preprocessor is source-agnostic. As long as it gets a list of images, it'll output a list of resized images

* **be sure to remember to haev a dummy variable recieve second index of the output** (tuple), as the Preprocessing function will output a tuple of preprocessed images and a list of oriignal sizes.

- [x]  preprocess the MNIST
    * you may have this imported and preprocessed in a previous project
      * I do but it's in the form of a class's metohd.
    * what am i even preprocessing this into?
      * we're gonna
        * make a standardized shape (i'll do like 4xx pixel squares or something)
        * divide pixel values by 255 so they're fractions between -1 and 1 (I think this ends up being 0 and 1) because models prefer these values over larger integers
        * [x] we'll want it to recive the list of images and output the preprocessed images

# DCGAN

- [x] impliment a baseline DCGAN
   * seems to mean it uses convolutional layers.
   * [this week's autoencoder project](https://github.com/Jabulani-N/atlas-machine_learning/blob/main/unsupervised_learning/autoencoders/2-convolutional.py) used convolutional layers, so we may be able to replicate it's basic structure
   * This just means do the Dricriminator and Generator as the example provided.
- [x] Train that baseline DCGAN on MNIST

## Alter the DCGAN

Let's aim to take no more than 1 hour of trying to get wanb to track our creation.

- [ ] Begin video for each project after that hour

actually, it may be better to do the video first, and then update code later.


* the full dataset one can be presented in a similar video that highlights how the same code handles both operations
  * may highlight that burme can be used to bulk square-ify images if getting non-square images causes a bug (as we didn't get far enough to test that)

- [ ] see if increaseing or decreasing hte number of layers improves things
  - [ ] find out how to get useful performance data.
  - [weights and biases site](https://docs.wandb.ai)?
  - [ ] make account
  - [ ] get a single test to work
  - [ ] message kush if you can't
- [ ] filter sizes
- [ ] strides
