# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
1. I converted the images to grayscale.
2. I used the Canny Transform to distinguish the bright lines from everything else. 
3. The canny transform is blurred with the aid of Gaussian blur.
4. A mask is then used in order to crop out the area of the image that we wish to process.
5. A hough transform is used on this mask in order to determine the lane lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slopes and the center of those slopes, determining which slope each line segment belonged to. This was done by comparing the slope to values that the line segments were most likely to take. After doing this, an average slope and center was calculated or each side, as well as a bias in order to place the new lines in their correct respective positions. Using the new formula for the lines, the top and bottom points for each side were obtained, and used to draw straight red lines on each side.




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when curves are introduced. When this happens, the straight lines no longer represent the lane lines quite as accurately as they would otherwise. 

Another shortcoming could be if the lane lines were filmed from a different location on the vehicle, as shown in the challenge video. This placing introduces more lines that need to be filtered out.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to adapt the pipeline so that it can handle curves. What might help here is if, instead of drawing one long line for each side, all the individual line segments are connected to each other for each side.

Another potential improvement could be to allow for a different location to be used when filming the lane lines.
