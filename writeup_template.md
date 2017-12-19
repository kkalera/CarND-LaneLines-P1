# **Finding Lane Lines on the Road**

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline of detecting lane lines, consisted of the following steps:
- converting the image to grayscale
- applying Gaussian blur to the image
- detecting edges using canny edge detection
- creating an array of vertices to cordon of the area in which we want to detect
- getting the pixels from that region
- getting the lines from those pixels, using Hough line detection
- get a fully connected line from the separate lines we just calculated
- finally we added the lines to the image with a red color for non connected lines, and green for our fully connected line.
![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


The first shortcoming is when the size of the image changes. My detection vertices are based on pixel values so a change in image size would result in issues with the detection.

Another shortcoming is presented with the challenge video. I'm filtering out lines that are angled at greater than 1 radian. Also, if the left lane, crosses the center of the image; this also gets filtered out. And vice versa for the right lane. This results in curved lines not being detected.


### 3. Suggest possible improvements to your pipeline

The first improvement I will make is changing my pixel based vertices system to a percentage based system. So the system can scale to any image size.

The second improvement will be on the part where I filter out the lines we do not want. To be able to detect curved lines and more improvements.
