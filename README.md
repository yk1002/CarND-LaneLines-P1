#**Finding Lane Lines on the Road** 

*Note to mentor:*

*I cloned this repo from the original project repo (https://github.com/udacity/CarND-LaneLines-P1.git)
in order to keep this self-sufficient, and modified P1.ipynb and README.mb (this file) for this project.*

### Goal

The goal of this project is identify right and left lanes in still images (or videos)
and draw them as two straight lines on top of them.

---

###Tasks

I have implemented the "pipeline" as a function *detect_lane_lines* that
produces an image of left and right lane line segments from a given still image.
The function performs the following operations in order.

1. Convert a given still image into a gray-scale image.
2. Apply Gaussian smoothing to the gray-scale image.
3. Produce an image with edges only from the smoothed one.
4. Mask out the region-of-interest from the edge only image.
5. Apply Hough transform to detect lane line segments.
6. Draw the detected lane line segments on a blank image whose dimensions are the same as those of the original image.

In order to draw a single line as the left and right lanes, I implemented a function *draw_lane_lines*
that produces an image with one or two lane lines. 
The function performs the following operations in order.

1. Separate line segments into two groups, left and right, according to their slopes.
2. For each group, fit a regression line.
3. Draw on a blank image those regression lines that span the entire height of the image.
4. Apply the same region-of-interest mask used in *detect_lane_lines*.

###Potential shortcomings with the current pipeline

1. Drawn lane lines are wobbly.
2. Won't work well in curves, up-slopes, and down slops.
3. Won't work if lanes are too weak, covered with something (dirt, snow, water), or even non-existent.
4. Won't work well where lane lines are doubled.

###Possible improvements

1. Apply smoothing over time.
2. Maybe fit the line segments with quadratic regression to account for curvatures.
