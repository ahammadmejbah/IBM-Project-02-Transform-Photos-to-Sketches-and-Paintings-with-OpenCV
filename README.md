<div align="center">
      <h1> <img src="https://github.com/ahammadmejbah/IBM-Transform-Photos-to-Sketches-and-Paintings-with-OpenCV/blob/main/Additional%20Files/SN_web_lightmode.svg" width="300px"><br/>IBM Transform Photos to Sketches and Paintings with OpenCV</h1>
     </div>

<p align="center"> <a href="https://github.com/ahammadmejbah" target="_blank"><img alt="" src="https://img.shields.io/badge/Website-EA4C89?style=normal&logo=dribbble&logoColor=white" style="vertical-align:center" /></a> <a href="https://twitter.com/ahammadmejbah" target="_blank"><img alt="" src="https://img.shields.io/badge/Twitter-1DA1F2?style=normal&logo=twitter&logoColor=white" style="vertical-align:center" /></a> <a href="https://www.facebook.com/ahammadmejbah" target="_blank"><img alt="" src="https://img.shields.io/badge/Facebook-1877F2?style=normal&logo=facebook&logoColor=white" style="vertical-align:center" /></a> <a href="https://www.instagram.com/ahammadmejbah/" target="_blank"><img alt="" src="https://img.shields.io/badge/Instagram-E4405F?style=normal&logo=instagram&logoColor=white" style="vertical-align:center" /></a> <a href="https://www.linkedin.com/in/ahammadmejbah/}" target="_blank"><img alt="" src="https://img.shields.io/badge/LinkedIn-0077B5?style=normal&logo=linkedin&logoColor=white" style="vertical-align:center" /></a> </p>
# Description
Have you wanted to transform your photographs in an artistic sketch or painting to showcase your creativity? Well using some built in OpenCV functions you can do exactly that! OpenCV is a powerful computer vision and image processing library. In this guided project you will learn how to transform your photos to sketches and paintings using OpenCV in python.

# Features
## Objectives:

After completing this lab, you will be able to:

*   Convert colored images to grayscale
*   Apply the Gaussian filter to smooth an image
*   Detect the edges of an image using the Gradient Magnitude
*   Convert a grayscale image to a binary image
*   Create a pencil sketch of an image in OpenCV
*   Create a water painting of an image in OpenCV

**Get ready to start!**
## Table of Contents

*   [Exercise 1: Import Libraries and Load your Images](#Exercise1)
*   [Exercise 2: Turning a Photograph into a Sketch](#Exercise2)
    *   [Task A: Convert Your Image To Grayscale](#TaskA)
    *   [Task B: Smooth Your Image](#TaskB)
    *   [Task C: Detect the Edges](#TaskC)
    *   [Task D: Get the Threshold of the Image](#TaskD)
*   [Exercise 3: Pencil Sketch Effect](#Exercise3)
*   [Exercise 4: Water Color Painting Effect](#Exercise4)
*   [Exercise 5: Experiment With Your Own Photos!](#Exercise5)
*   [Exercise 6: Practice!](#Exercise6)
    *   [Task A: Smooth an Image](#Task6A)
    *   [Task B: Get the Water Painting Image of a Colored Image ](#Task6B)
    *   [Task C: Convert a Grayscale Image to a Binary Image](#Task6C)



``` python
import requests
import os

# Make a folder to hold our images called "images" if it doesn't already exist
!mkdir -p ./images

# To add the image we will be using to this lab to the folder
if not os.path.isfile("./images/LandscapePhotograph.jpeg"):
    r = requests.get("https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/transform-photos-to-sketches-and-paintings-with-opencv/images/LandscapePhotograph.jpeg")
    f = open("./images/LandscapePhotograph.jpeg", mode = "wb+")
    f.write(r.content)
    f.close()

```

#### Detect the Edge

The edges of an image are the parts of an image where the brightness changes quickly. To detect the edges of an image, we need to compute something called the gradient magnitude of an image. The gradient magnitude of an image measures how quickly the image is changing and it is used for edge detection. To get a sketch for our photograph, we will compute the gradient magnitude of the image.

To get the gradient magnitude of an image, we need to calculate the verticle and horizontal components of the gradient of the image. In other words, we need to calculate how much the image changes in the horizontal direction (the x component of the gradient), $dx$, and the verticle direction (the y component of the gradient), $dy$. To calculate how much the image changes in the each direction, we apply a filter called the Sobel filter to the images. To do this in OpenCV, we use the method **cv2.Sobel()**.

The formula for the gradient magnitude is $\sqrt {\left( {dx} \right)^2 + \left( {dy} \right)^2 }$.


``` python
sobelx = cv2.Sobel(blur,cv2.CV_64F,1,0,ksize=5) # Change in horizonal direction, dx
sobely = cv2.Sobel(blur,cv2.CV_64F,0,1,ksize=5) # Change in verticle direction, dy
gradmag_sq = np.square(sobelx)+np.square(sobely) # Square the images element-wise and then add them together 
gradmag = np.sqrt(gradmag_sq) # Take the square root of the resulting image element-wise to get the gradient magnitude

plt.imshow(gradmag, cmap ='gray')

```

### Authors:
[Yasmine Hemmati](https://www.linkedin.com/in/yasmine-hemmati-80592119b/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkQuickLabstransformphotostosketchesandpaintingswithopencv28748434-2021-01-01)


| Date (YYYY-MM-DD) | Version | Changed By | Change Description      |
| ----------------- | ------- | ---------- | ----------------------- |
| 2021-08-06        | 0.1     | Yasmine    | Initial Version Created |

© IBM Corporation 2021. All rights reserved.

<!-- </> with 💛 by readMD (https://readmd.itsvg.in) -->
    
