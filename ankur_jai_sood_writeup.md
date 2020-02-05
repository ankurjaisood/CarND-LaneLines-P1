# **Finding Lane Lines on the Road** 

[//]: # (Image References)

[grayscale]: ./examples/grayscale.jpg "Grayscale"
[result_video]: ./test_videos_output/solidYellowLeft.mp4 "Result"

## 1. The pipeline

For this project the goal was to create a pipeline that detects the lane markings on the road from a video feed.
My pipeline did this through the following steps:
- Convert the video frame to grayscale
- Perform a Gaussian blur on result
- Perform Canny edge detection on the result
- Mask the result to create a region of interest in which to detect lines
- Perform a hough transform to find the lines within the region of interest
- Draw the lines and overlay them over the original image

### Convert to Grayscale

![Grayscale result][grayscale]

### Gaussian Blur

### Edge Detection

### Region of Interest

### Hough Transform 

### Overlay Over Original

### Video Result
![Video showcasing result of pipeline][result_video]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...




## 2. Shortcomings with the current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


## 3. Possible improvements to the pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
