# **Finding Lane Lines on the Road** 

In this project I have used Python3, Numpy, Matplotlib, Canny Edge Detection, Hough Transforms, Linear Regression to mark lane lines on a given road image. I have tried the following three different approaches to extrapolate the lines identified through Hough transform to extend them to the full lane lines in the image. 

1. Extrapolating the lines using mean slopes
2. Extrapolating the lines using mean slopes of biggest lines 
3. Extrapolating the lines using Linear Regression 

I have tried all these three approaches on the sample images and test videos. All these three techniques are working fine on the sample images and videos, but the first two techniques are not working well on the optional challenge and the Linear Regression approach is working fine on the optional challenge.

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Goal of this project**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Test the pipeline on the sample images and videos
* Write the Lane marked images and Videos to new directory

A sample original image and lane marked image is shown below

[//]: # (Image References)
[Original Image]: ./folder_for_writeup/whiteCarLaneSwitch.jpg

[Lane Marked Image]: ./folder_for_writeup/whiteCarLaneSwitch_lane_marked_mean_slope_approach.jpg
