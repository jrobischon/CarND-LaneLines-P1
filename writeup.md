# Detecting Lane Lines
## Purpose:
The purpose of this project is to build a pipeline for detecting lane lines in a series of photos and videos. 

## Method:
Lanes are detected using a sequence of steps that are applied in the detect_lanes() functions.  These steps are described below:

1) Convert image to grayscale.
2) Detect edges using Canny edge detection algorithm.
3) Define a region of interest as a polygon with 4 vertices.  Pixels outside of this region are set to 0.
4) Convert edges into line segments using a Hough transform.
5) Split line segments into two groups: one for the left side of the lane and one for the right side
6) Build linear regression models for both the left side and right side of lanes.  Rather than updating the draw_lines() function, 
I created a new function called interpolate_values().
7) Use regression model to extend lane lines to the bottom of each image
8) Superimpose calculated lane lines on each image/video

## Results:
Using the method described above, I was successful in identifying the lane lines on each of the images and videos (excluding the
challenge video).

## Opportunities for Improvement
This methodology falls apart when applying to roads with a large amount of curvature, such as in the challenge video.
Accounting for non-linearities in the regression model may improve performance in these situations.  This could be accomplished
by incorporating polynomial terms, cubic splines, or loess regression.
