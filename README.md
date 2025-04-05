# Image-Portrait-Mode-with-SAM
This application use Meta's pretrained SAM model to extract the subjects of an image and blur the background with the subject unchanged. 
You can adjust the blurring kernel size (bigger kernel size means stronger blurring effect). Plus, you can also upload another image
to replace the original background, and you can choose to blur the new background. For both functions, set kernel size = 1 if you don't 
want to blur. 

You can run this app on Google colab: 
<a target="_blank" href="https://colab.research.google.com/drive/1uqNvFRZJU8UkRb_sy5NIqw46eVUiWEpp?usp=sharing">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

# Example

Here is an example of the effect of the background blurring and backgroung replacement functions: 

Original image:
![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/2.jpg?raw=true)

Background blurred:
![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/blurred_2.jpg?raw=true)

Background replaced:
![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/background_replaced_2.jpg?raw=true)

# Suggestions
During the implementation of the program, I found that when using bounding box prompts, SAM is
actually not very good for multiple object segmentation in large areas, but good for single-or-few object
segmentation in small areas.
So, in this program, I suggest you to draw boxes in a few-object-and-small-area but multiple-box
way, and you will see the performance gets much better, example below:

First, we draw a big box that includes all the persons:

![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/ex1.png?raw=true)

And the result is poor, the girl on the left lost her entire body: 

![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/ex2.png?raw=true)

But if we draw multiple boxes, and each box only includes one or two persons:

![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/ex3.png?raw=true)

The result will be literally perfect: 

![](https://github.com/zdshen-hkbu/Image-Portrait-Mode-with-SAM/blob/main/sample%20images/ex4.png?raw=true)
