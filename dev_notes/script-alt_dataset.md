script for functionality with different imagesets

# changes when using custom dataset

Because the real image import function is transferable, we can train using any given stored imageset. the chcanges in use are minimal, but I'll explain them here.


# imports

Imports will be identical, at the moment, unless a given dataset's use requires any. My selected dataset does  not appear to necessarily need imports.
* it appears the images are generally stored in files that can be directly downloaded, with an optional script to download any updates made.
  * [forward in history on huggingface page]

# Real Images

we can give it an address to a directory of images (instead of running it without an argument,) and it'll create an image list ready to be preprocessed.

At this point, preprocessing will ensure we can use the exact same execution methods on a custom dataset, requiring no recoding, as the inputs to the model will be formatted identically as MNIST was before.
