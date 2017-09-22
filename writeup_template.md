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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied gaussian filter then canny edge detection then I have created a mask with region of interest then detect and draw line with hough transform then I have combined the lines with initial image   

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by for each line segment I got average x1 y1 x2 y2 and then extrapolate to the top and bottom of the lane.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline
One potential shortcoming would be
fixed region of interest (polygon vertices vertices = np.array([[(0,imshape[0]),(470, 320), (490, 320), (imshape[1],imshape[0])]], dtype=np.int32) )
and it didn't dynamically changed base on car direction, 

Another shortcoming could be
(no distinguish between lane lines and other objects) 
it will not work if there are other objects in the region of interest(car, tree, curb, etc...) all these objects will detect their edges and considered as lines and will draw lines for its edges. as example in (challenge.mp4 video) there is a lot of tree and curbs in the region of interest. the algorithm detect theses trees edges and draw lines for its edges. 



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to 
to dynamic calculate region of interest based on car direction polygon vertices vertices as function of car direction
vertices = calculate_region_of_interset(car_direction)


Another potential improvement could be 
the algorithm should be able to distinguish between lane lines and other objects in the region of interest (car, tree, curb, etc...)
algorithm should analyse the different detected edges. and distinguish between lane lines and other objects

