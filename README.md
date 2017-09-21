# **Finding Lane Lines on the Road** 

In this project I have used Python3, Numpy, Matplotlib, Canny Edge Detection, Hough Transforms, Linear Regression to mark lane lines on a given road image. I have tried the following three different approaches to extrapolate the lines identified through Hough transform to extend them to the full lane lines in the image. 

1. Extrapolating the lines using mean slopes
2. Extrapolating the lines using mean slopes of biggest lines 
3. Extrapolating the lines using Linear Regression 

I have tried all these three approaches on the sample images and test videos. All these three techniques are working fine on the sample images and videos, but the first two techniques are not working well on the optional challenge and the Linear Regression approach is working fine on the optional challenge.

---

## **Goal of this project**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Test the pipeline on the sample images and videos
* Write the Lane marked images and Videos to new directory

A sample original image and lane marked image is shown below

![Original Image](folder_for_writeup/whiteCarLaneSwitch.jpg)

![Lane Marked Image](folder_for_writeup/whiteCarLaneSwitch_lane_marked_polynomial_fit.jpg)

---

## **Reflection**

### **How the Pipeline is built**

I have built this pipeline in the following 7 steps

1. Filtering the image to identify white and yellow colours as the lane lines on original image is marked in these two colours
2. Converting the image to gray scale
3. Applying gaussian smoothing with a kernel size of 3 to smoothen this image
4. Detecting the edges using canny edge detection with a low and high gradient threshold of 50 and 150
5. Selecting a region of interest which is in a polygon shape with wide bottom side and narrow top side to darken any pixels outside this polygon.
6. Applying Hough transform on this image to get an array of all identified lines
7. Extrapolate these lines using Linear Regression to draw one continuou lane line each for the left and right lanes

Here are my observations about the three approaches that I used to draw the lines

### **Mean Slopes Approach**

This is the simple and first approach that I wanted to test and try on this problem. Here are the steps at a high level used in this approch
1. Find slopes of all the lines that we get using hough transform (handle any division by 0 with a huge slope)
2. Divide the image based on the center of x-axis i.e width of the image to decide which lines to consider for left and right lanes
3. As height of the image in pixels starts with 0 at top left corner and reaches a maximum at the bottom left corner, the slope of left lines are considered negative and the slope of right lines are considered positive.
4. Decide a threshold slope to take lines only beyond that threshold to be considered for extrapolation
5. Identify the left lines and right lines based on the above two points and average slopes and average intercepts for left and right lines
6. Find the starting and ending points of the lines making use of these mean slopes and intercepts and extrapolate the lines

