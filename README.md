# **Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project the aim is to detect lane lines in images using Python and OpenCV.


Creating a Great Writeup
---
For this project, a great writeup should provide a detailed response to the "Reflection" section of the [project rubric](https://review.udacity.com/#!/rubrics/322/view). There are three parts to the reflection:

1. Describe the pipeline

2. Identify any shortcomings

3. Suggest possible improvements

We encourage using images in your writeup to demonstrate how your pipeline works.

All that said, please be concise!  We're not looking for you to write a book here: just a brief description.


The Project
---

### Reflection

### 1. The Pipeline

My pipeline consisted of the following steps.
1. Convert to grayscale
2. Perform Gaussian Smoothing
3. Apply Canny Edge Detection to smoothed image
4. Apply a polygon mask to the edge detected image
5. Run a Hough transform on the masked edge detected image
6. Draw the lines on the image

### 2. The `draw_lines()` function

In order to draw a single line on the left and right lanes, I modified the draw_lines().
For each line returned by Hough tranform, the slope and intercept was calculated. The lines were classified as left and right based on their slope values. Some lines are rejected for extreme slope values which don't make sense for lane lines. Having obtained the slope and intercept for left and right lines separately, the mean slope and intercept is calculated for each. A simple function is defined to extrapolate lines given the slope, interecept and image size (this is to determine the top and bottom of the region of interest). These extrapolated lines are drawn on the blank image, which is then superimposed on the original image using `cv2.addweighted()`

<hr>
![sample output][test_images_output/opsolidYellowCurve.jpg]


### 2. Potential shortcomings of current pipeline


One potential shortcoming would be what would happen when ...

Another shortcoming could be ...


### 3. Possible improvements to current pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

