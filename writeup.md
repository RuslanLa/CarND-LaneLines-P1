# **Finding Lane Lines on the Road**

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[solidWhiteCurve] (./output_imgs/solidWhiteCurve.jpg "Solid white curve")
[solidWhiteRight] (./output_imgs/solidWhiteRight.jpg "Solid white right")
[solidYellowCurve] (./output_imgs/solidYellowCurve.jpg "Solid yellow curve")
[solidYellowCurve2] (./output_imgs/solidYellowCurve2.jpg "Solid yellow curve 2")
[solidYellowLeft] (./output_imgs/solidYellowLeft.jpg "Solid yellow left")
[whiteCarLaneSwitch] (./output_imgs/whiteCarLaneSwitch.jpg "Solid white car lane switch")
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of several steps. First, I converted the images to grayscale, then I applied GaussianBlue to suppress noize.
I used Canny algorithm to detect edges on gray blur picture. Then I filtered edges by region in order to apply line selection only on the area where lines can be located on a picture.
Using hough lines I detected lines on a picture, filtered lines again by region and then applied found lines on an initial picture.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function and grouped lines by slope in two groups to detect left and right lines. Then I computed median slopes and intercepts of two groups and computed two points for every line using formula: y = slope * x + intercept

![gray] (./output_imgs/pipeline_output/gray.jpg)
![gray blur] (./output_imgs/pipeline_output/gray_blur.jpg)
![edges] (./output_imgs/pipeline_output/edges.jpg)
![image filtered by region] (./output_imgs/pipeline_output/image_filtered_by_region.jpg)
![hough lines] (./output_imgs/pipeline_output/hough_lines.jpg)
![solidWhiteCurve] (./output_imgs/solidWhiteCurve.jpg)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a lane has a curve edges that can't be described with line

Another shortcoming could be relying on certain points on computation of points for line. It may happen that these points are located on lines outside an image


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change points computation in draw_lines and to find points on edges of filtered region

Another potential improvement could be to detect curve lanes and for that case use only the nearest part of lane to draw a line
