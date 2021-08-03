# Digital signal and image processing

Acquainting with the methods of digital processing and analysis of information contained in signals and digital images. Basic processing is included in the project.

Tasks and skills
* Implementation of computer systems for image and signal analysis using open source libraries
* Construction of image and signal processing and analysis schemes for problems

The library used is OpenCV (Open Source Computer Vision Library) for programming functions mainly focused on real-time computer vision.
```
import cv2 as cv
```

What does this program do?
* Loads an image
* Processes the histogram
* Shows the image distribution function
* Processes image filters
* Canny edge detection
* Processes gradients
* Plots the changes
* Shows an example of an ECG signal

Code created in the Google Colab repository. 

![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg) https://colab.research.google.com/drive/1QIXgTlZN69AJIrwuIogUt9yBEwhLe3YM

## Histogram

* Image Histogram

  It is a graphical representation of the intensity distribution of an image. It quantifies the number of pixels for each intensity value considered.

* Histogram Equalization

  It is a method that improves the contrast in an image, in order to stretch out the intensity range. The pixels seem clustered around the middle of the available range of intensities.  What Histogram Equalization does is to stretch out this range. After applying the equalization, we get an histogram like the figure in the center.
  ```
  cv.equalizeHist(img)
  ```

* Histogram Calculation

  OpenCV implements the function ``cv::calcHist``, which calculates the histogram of a set of arrays (usually images or image planes). It can operate with up to 32 dimensions.
  ```
  cv.calcHist([img],[i],None,[256],[0,256])
  ```

## Image Filtering

The code uses filters to change the sharpness, contrast, or colors of the original image, for example. The filters used are a Gaussian filter, a median filter, and a filter that turns the image into a negative.
```
blur = cv.GaussianBlur(img,(15,15),0)
median = cv.medianBlur(img,15)
negativ = cv.bitwise_not(img)
```

## Canny Edge

The code is responsible for detecting the Canny's edge. The algorithm is multi-step:
* Noise reduction
* Find the image intensity gradient
* Unlimited attenuation
* Hysteresis (dependence of the current state on the previous ones)

The algorithm performs all steps, which allows you to obtain strong image edges.
```
edges = cv.Canny(img,200,300)
```

## Gradients

The code is responsible for showing the different gradients of the image. Sobel operators include joint Gaussian smoothing and a differentiation operation, which makes them more resistant to noise. The function computes Laplace for the source image by summing the second derivatives x and y as calculated by the Sobel operator. We can specify the direction of capturing derivatives, vertical or horizontal (through the yorder and xorder arguments, respectively).
```
laplacian = cv.Laplacian(img,cv.CV_64F)
sobelx = cv.Sobel(img,cv.CV_64F,1,0,ksize=5)
sobely = cv.Sobel(img,cv.CV_64F,0,1,ksize=5)
```
