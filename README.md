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
