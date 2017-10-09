
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "Result 1"
[image2]: ./test_images_output/solidWhiteRight.jpg "Result 2"
[image3]: ./test_images_output/solidYellowCurve.jpg "Result 3"
[image4]: ./test_images_output/whiteCarLaneSwitch.jpg "Result 4"
[image5]: ./test_images_output/video_output_1.png "Result 5"
[image6]: ./test_images_output/video_output_2_.png "Result 6"
[image7]: ./test_images_output/video_output_3_.png "Result 7"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.
First i converted image to grayscale.
Since the lanes are yellow or white color, first i masked to image to get only pixels which are of yellow and white color.
To get yellow pixels mask I used HSV image as it works properly for creating mask of yellow color.
To get white pixels mask I used the gray image.
Then I applied the gaussain blur to remove noise from the image which helps in next step.
In next step we detect edges in image.
To connect the pixels which forms lines in the edges image I used the Hough Transform.
To draw the annotated solid lines i created a new function draw_connected_lines.
First i removed the lines which have unwanted slopes. The values of unwanted slopes established by Trial and Error method.
To average out the slope and intercept of left and right line I used weighted average. The weights are length of line.
So the line with more length will contribute more in avg slope and intercept.

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]
![alt text][image7]


### 2. Identify potential shortcomings with your current pipeline


The potential shortcoming is not having proper field of view. Especially on turns where we will have lots of unwanted pixels.


### 3. Suggest possible improvements to your pipeline

A possible improvement technqiue could be to transform the frames in such a way that we have more road pixels then surrounding.
The other improvement could be to consider past frames and try to introduce probalistic object segmentation as what pixels could be road and lanes.
