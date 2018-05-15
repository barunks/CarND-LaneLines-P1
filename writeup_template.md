# **Finding Lane Lines on the Road** 

## Barun Sharma Writeup 

---

# **Finding Lane Lines on the Road**

### How to run

Please review the installation instructions [here] (https://github.com/udacity/CarND-LaneLines-P1/blob/master/README.md)


---

The goals of this project are the following:

* Make an image processing pipeline that visualize lane lines on the road
* Analyze solution for its further improvement


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "solidWhiteCurve"
[image2]: ./test_images/solidWhiteRight.jpg "solidWhiteRight"
[image3]: ./test_images/solidYellowCurve.jpg "solidYellowCurve"
[image4]: ./test_images/solidYellowCurve2.jpg "solidYellowCurve2"
[image5]: ./test_images/solidYellowLeft.jpg "solidYellowLeft"
[image6]: ./test_images/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"


---

### Reflection

### 1. Pipeline steps for image processing 

This pipeline consisted of 6 steps:

* Transforma original images to grayscale
* Image smoothing using Gaussian filter
* Edge detection using Canny detector and apply yellow lanes to the edges
* Selecting the region of interest's
* Apply hough transformation for line detection
* Combine initial image with transformed images

 NOTE: Modified *draw_line()* function as a starting point to average/extrapolate the line segments to map out the full the 
 extent of the lane.  
    
Think about things like separating line segments by their slope ((y2-y1)/(x2-x1)) to decide which segments are part of the left
line vs. the right line.  One can average the position of each of the lines and extrapolate to the top and bottom of the lane.
This function draws `lines` with `color` and `thickness`. Lines are drawn on the image inplace (mutates the image).


![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]


### 2. Potential shortcomings with the current pipeline


* Image processing could be better solution. Better boundary conditions and exceptional handling can help to deal with break down or jittery curve conditions
* Inconsistent Curve lane can be a challenge to solve for finding lane lines


### 3. Possible improvements and recommendations to improve pipeline

* The curve lanes were not smoothing and a bit jittery, and lines even dropped out of the video completely frequently. This can be solved by creating a container to store the slope and intercept for each line detected by respective N frames. The actual line drawn on the current frame is simply the average slope/intercept of all these lines. Different statistical methods can be applied to calculate a rolling mean of the lines over time

* Better boundary condiotions and continuous changing curvy or jittery lanes can be solved by regression technique. 

