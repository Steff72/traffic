For the CNN, I started with a copy of the handwriting example of the lecture.
This gave me a really bad accuracy of 5.5%.

I then added a second  which improved the accuracy to about 70%.

Then I looked at the pictures and realized some of the lack contrast.
I found an article by Thomas Tracey who proposed CLAHE to improve traffic sign recognition:
https://medium.com/@thomastracey/recognizing-traffic-signs-with-cnns-23a4ac66f7a7

As in all examples CLAHE was applied to greyscale images, but I didnt want to loose the valuable colorinformation, I transformed the images to LAB color, applied CLAHE to the L channel, then transformed them back to RGB, as detailed in this stackoverflow post:
https://stackoverflow.com/questions/25008458/how-to-apply-clahe-on-rgb-color-images

The result was still not thrilling so I increased the units in the hidden layer to 512 and added some BatchNormalization layers.
This greatly improved the accuracy to 98-99%, but the time to train increased significantly.

By experimenting I found that removing the CLAHE preprocessing and reducing the units in the hidden layer to 256 greatly reduced the time to train without significantly lowering the accurancy. With a training time of around 30 seconds per Epoch and a test accuracy of 98-99% I was happy.
