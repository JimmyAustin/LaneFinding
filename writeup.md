#**Finding Lane Lines on the Road**

[//]: # (Image References)

[raw_image]: ./examples/raw.png "Grayscale"
[grey_image]: ./examples/grayscale.png "Grayscale"
[blurred_image]: ./examples/blurred.png "Grayscale"
[canny_image]: ./examples/canny.png "Grayscale"
[region_image]: ./examples/region.png "Grayscale"
[final_image]: ./examples/finished.png "Grayscale"

### Reflection

###1. Pipeline

My pipeline consisted of the following steps.

![alt text][raw_image]

First, we took the image and converted it to greyscale.

![alt text][grey_image]

Then we blurred the image using a gaussian blur with a kernal of 5px.

![alt text][blurred_image]

We took the blurred image and ran a canny transformation over it.

![alt text][canny_image]

We then cut out the relevant region from the image.

![alt text][region_image]

We took the hough lines of this region, found the midpoints for each line, separated them into separate left and right arrays by which side of the midpoint of the image they are, then ran a linear regression on each array, and drew the found line on the image.

![alt text][final_image]

### Shortcomings and improvements.

The current pipeline has many faults.

- It relies on a fixed region that doesnt account for turns. It also doesnt scale for images or videos other then the ones of the correct size.
- We use single polynomial linear regression, so we only get a line instead of a curve as we would if we used a different technique.
- No color tuning.
