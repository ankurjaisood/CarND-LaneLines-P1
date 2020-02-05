# **Finding Lane Lines on the Road** 

[//]: # (Image References)

[original]: ./test_images/solidWhiteCurve.jpg "Original"
[grayscale]: ./examples/solidWhiteCurve_grayscale.jpg "Grayscale"
[gaussian]: ./examples/solidWhiteCurve_gaussian.jpg "Gaussian"
[canny]: ./examples/solidWhiteCurve_canny.jpg "Canny"
[roi]: ./examples/solidWhiteCurve_ROI.jpg "ROI"
[hough]: ./examples/solidWhiteCurve_hough.jpg "Hough"
[result_image]: ./test_images_output/solidWhiteCurve.jpg "Result"
[result_video]: ./examples/result.gif "Result"

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
Colour images consist of three channels: red, blue, and green. The first step in the pipeline is to convert the image to grayscale by taking the average of the three channels colour intensity at each pixel.
This allows us to process the image further, reduces the image size, and hence improves pipeline performance.

| ![Original image][original] | ![Grayscale result][grayscale] |

### Gaussian Blur

| ![Grayscale result][grayscale] | ![Gaussian result][gaussian] |

### Edge Detection

| ![Gaussian result][gaussian] | ![Canny image][canny] |

### Region of Interest

| ![Canny image][canny] | ![ROI image][roi] |

### Hough Transform

| ![ROI image][roi] | ![Hough image][hough] |

### Overlay Over Original

| ![Hough image][hough] | ![Result image][result_image] |

### Video Result
![Video showcasing result of pipeline][result_video]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...




## 2. Shortcomings with the current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


## 3. Possible improvements to the pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
