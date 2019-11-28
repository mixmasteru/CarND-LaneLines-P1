# **Finding Lane Lines on the Road** 

[//]: # (Image References)

[image1]: ./examples/gray.jpg "Grayscale"
[image2]: ./examples/gaus.jpg "Gausian Blur"
[image3]: ./examples/canny.jpg "Canny"
[image4]: ./examples/crop.jpg "Crop"
[image5]: ./examples/hough.jpg "Hough"
[image6]: ./examples/final.jpg "Final"

---

## Reflection

### 1. Describe your pipeline

My pipeline consisted of these steps:

- converted to grayscale
- apply gaussian blur
- use Canny algorithm to detect edges
- crop to region of interest (blackout other pixel)
- use Hough transform to detect all lines

To improve the drawing of the lines I do:

- calc the gradient for all lines
- use gradient to divide in left/rigth lines (negative/left, positiv/rigth)
- use polyfit from numpy to get one left/rigth line from left/rigth grouped lines
- use y values from below horizon and image hight to draw left/rigth lines on image

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]

### 2. shortcomings with my pipeline

- this might not work if the horizon is not on the same level like in the example images
- for some frames in the test video no left line is found 
- the current approach does not work with the video 
of optional challenge, so curves are a problem


### 3. Suggest possible improvements to your pipeline

- if no line is found in current frame, use the last found one
- find better algorithm for curves
- find better way to remove false positive lines