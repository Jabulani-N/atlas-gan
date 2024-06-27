# Takeaways and Observations - custom dataset

Though the code does seem to work on a custom imageset, I ran into a small problem:
<details open>
<summary>The problem, illustrated</summary>
<br>

![screenshot of full res is too large](./images/raw%20images%20cost%20too%20much%20at%20full%20res.PNG)

</details>



Some images were so large they nearly crashed my computer. This is minimal problem. If worst comes to worst, I can use https://www.birme.net to preprocess the images for me, so none use excessive memory for allocation.

## Main topics

model convergence
* I was originally of the assumption that any patterns in convergeance would miror the results of MNIST data, but after talking with others who successfully tested, the convergeance will actually be heavily influenced by getting discriminator hyperparameeters only just strong enough to "barely" tell that the fake is a fake. When the discriminator is too effective, it is unable to provide useful feedback to the generator.
  * I wonder if having two discriminators, a weak and strong, would be ideal. The generator could initially be trained on the weak discriminator, so that it learns to generate noise with more form. Then, the strong discriminator, usually too effective to afford the generator any useful training, may actualy begin experiencing uncertainty, allowing the generaator to learn better than with a weak discriminator alone. Potentially, there could be even more increments.

training time
* due to the significantly higher sizes of images used in this dataset, and how quickly the time to train ramped up in the mnist set with larger preprocessed image sizes, it will be important to eeffectively compress all images within the layers during any training steps, and restore them afterwards. I understand this is somethng done via kerenels in tensorflow for this very reason.
* as the workload exceeds any allocations permitted, I am not able to check how the speed compares to the previous dataaset at this time.

image quality
* after getting an mnist image from the generator, the next step would be to use birme to create similarly small images for the sake of quickly testing, even though it wouldn't be a production-level of code performance overall.
* This would allow evaluation of the current methods.
* low quality but a discernable image may mean more epochs are appropriate, while a lack of any coherence at all may mean the discrimiator is too precise to be useful.
  * the quality of the mnist would serve as a good controll, as it is of limited colors and has relatively uniform framing.

other relevant factors
* 