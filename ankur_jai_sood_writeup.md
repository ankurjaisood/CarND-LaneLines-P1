# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. The pipeline

For this project the goal was to create a pipeline that detects the lane markings on the road from a video feed.
My pipeline did this through the following steps:
- Convert the video frame to grayscale
- Perform a Gaussian blur on result
- Perform Canny edge detection on the result
- Mask the result to create a region of interest in which to detect lines
- Perform a hough transform to find the lines within the region of interest
- Draw the lines and overlay them over the original image


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Shortcomings with the current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Possible improvements to the pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
