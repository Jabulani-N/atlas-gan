# To-do List

- [ ] unchecked content

- [X] checked content

# SETUP - MNIST GAN

- [x] find where I did the MNIST preprocessing before
* it's in supervised learning > object detection > [5-yolo.](https://github.com/Jabulani-N/atlas-machine_learning/blob/main/supervised_learning/object_detection/5-yolo.py)

- [x] document the variables, input names, and outputs so it can be read easily
- [x] copy that preprocessor code into current project

- [x] have AI write a check for making sure it is preprocessed correctly

  * unneeded, as I copied the function from my previous assignment that got full marks for preprocessing

- [x] find code to import image files as 3-color channels `numpy.ndarray` so I can use the precprocess function and it's output.

  * you may have it in the same previous YOLO project

- [x] import mnist
  * `(x_train, y_train), (x_test, y_test) = tensorflow.keras.datasets.mnist.load_data()`
  - [x] I need to find out what data type it is so I can put it through my preprocessing function
    * I've imported it up to `mnist` so we can shorthand it thusly.
    * `mnist.load_data()` returns ((`images`, `labels`),(`testing_data_images`, `testing_data_labels`))
      * `images` = 3D array
        * shape `(num_samples, 28, 28)` - `28x28` pixels.
          * one `28x28` array of pixels per image.
          * grayscale.
            * [ ]  comment out the part of preprocessor that respects the 3 color channels and replace it with the one grayscale chanel
              * I likely don't need to understand what the grayscale channels are doing, because the point is that it will perform the same math logic, but on the one channel
              * this is better, because all images in my own version will be color, so no point in doing hard work.,
      * **we can ignore testing data for this project**.
        * `testing_data` items are used for supervised learning models to be evaluated. they are arranged the same way as the `images` and it's `labels`, but are separate so you can judge a model's labelling accuracy on data it has yet to see.
- [ ]  rewrite preprocess methofd into a strong, independant function.
- [ ]  preprocess the MNIST
    * you may have this imported and preprocessed in a previous project
      * I do but it's in the form of a class's metohd.


# DCGAN

- [ ] impliment a baseline DCGAN
- [ ] Train that baseline DCGAN on MNIST

## Alter the DCGAN
- [ ] see if increaseing or decreasing hte number of layers improves things
- [ ] filter sizes
- [ ] strides
