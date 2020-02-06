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

### Converting Frame to Grayscale
Colour images consist of three channels: red, blue, and green. The first step in the pipeline is to convert the image to grayscale by taking the average of the three channels colour intensity at each pixel.
This allows us to process the image further, reduces the image size, and hence improves pipeline performance.

| ![Original image][original] | ![Grayscale result][grayscale] |
|:---:|:---:|

### Performing Gaussian Blur
A Gaussian blur operation involves convoluding a filter with the orignal image. In this case the filter is an n by n window of 1s around the pixel in question.
This essentially takes a local average in a n by n neightbourhood of every pixel smoothing out any sudden changes in gradient. 

| ![Grayscale result][grayscale] | ![Gaussian result][gaussian] |
|:---:|:---:|

### Canny Edge Detection
Next the edges in the image are found using Canny edge detection. The Canny edge detector takes the first derivatives of the image in the X and Y directions and then calculates the gradient and direction for each pixel using the two resultant images.
Finally a scan of the original image is done removing any pixels which do not make up an edge.

| ![Gaussian result][gaussian] | ![Canny image][canny] |
|:---:|:---:|

### Creating a Region of Interest
Next a region of interest is created in the area where lanes are expected to be found. This reduces the cost of calculating the Hough transform over an unnecessarily large image. 

| ![Canny image][canny] | ![ROI image][roi] |
|:---:|:---:|

### Finding Lines using Hough Transform
Lines are found using the Hough transform. The Hough transform detects lines by looking for them in the edge detected image not in the x/y space but in the parameter space (for lines slope and y-intercept).
Ones lines are found they are grouped into either being part of the left or the right lane using their calculated slope and intercept.
The final lane positions are calculated by averaging out the slopes and intercepts in the left lane and right lane groups. 

| ![ROI image][roi] | ![Hough image][hough] |
|:---:|:---:|

### Overlay Over Original
Finally the lane markings are overlaid over the original image.

| ![Hough image][hough] | ![Result image][result_image] |
|:---:|:---:|

### Video Result
![Video showcasing result of pipeline][result_video]

## 2. Shortcomings with the current pipeline
One major shortcoming of this pipeline is it assumes all lane markings are straight lines. This results in it struggling significantly in corners as seen in the challenge video.
Another is that this is quite a costly pipeline to compute as many operations need to be done to prepare the image for the Hough transform.
Finally, this pipeline is sensitive to its configuration. There is a lot of manual parameter tuning to get this pipeline to work robustly which results in it not being easily transferrable to other environment such as low-light conditions or differing camera placement.

## 3. Possible improvements to the pipeline
To address the first shortcoming we could consider changing this pipeline to look for higher order polynomials (splines) instead of just simply lines. This would result in higher cost to run the algorithm but would significantly improve the performance of the pipeline.
To address the complexity of this pipeline we could consider re-writing this pipeline in a more efficient language such as C++ while also utilizing parallel GPU computing using CUDA.
To address the sensitivity of this pipeline we would need to create a seperate algorithm to tune our pipleline based on the environment. For example we could use light sensors to measure ambient light conditions and we could iteratively fine tune our ROI so not to easily miss lane markings.
