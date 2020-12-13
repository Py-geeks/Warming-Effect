# Warming Effect
Here we are with another filter effect **Warming Effect**.<br>
In this session you will know about how to utilize and build *lookup_table*,splitting RGB channels,<br>
applying mapping to channels & merging channels.<br>
As we are manipulating warming effect hecnce we have to work with Only red & blue channels,<br>
we don't need to distort green channel.<br>
This is an important project to sharpen your skills on openCV.<br>
## Tools and Languages:
<img align="left" alt="OpenCV" width="26px" src="opencv.png">
<img align="left" alt="VS Code" width="26px" src="visual-studio-code.png">
<img align="left" alt="pip" width="26px" height="34px" src="pip.png">
<img align="left" alt="Python" width="26px" src="python.png">
<br>


## Installation
Use the package manager [pip](https://pip.pypa.io/en/stable/) to install cv2 and numpy.


```bash
pip install cv2
pip install numpy
```

## Import
Use [import](https://www.w3schools.com/python/ref_keyword_import.asp) keyword to import modules.
```python
import cv2
import numpy as np
```

## Reading image from file

```python
img = cv2.imread("cat.png")
```

## Steps to be followed:
1.First create a copy of the image to work on.<br>
2.Set original x & y-axis values.<br>
3.Create and set Lookup Table of both channels.<br>
4.Split the channels.<br>
5.Apply Lookuptable-mapping into both channels.<br>
6.For desired output merge the channels. 

## Step-1:
```python
result = np.copy(image) #stored into result variable
```
## Step-2:
```python
#Original x-axis values
originalValues = np.array([0, 50, 100, 150, 200, 255])
#changes Y-axis values for red and blue channel
redValues = np.array([0, 80, 150, 190, 220, 255])
blueValues = np.array([0, 20, 40, 75, 150, 255])
```
## Step-3:
```python
#create lookup table for red channel
allValues = np.arange(0, 256)
redLookupTable = np.interp(allValues, originalValues, redValues)

#create lookup table for blue channel
blueLookupTable = np.interp(allValues, originalValues, blueValues)
```
## Step-4:
```python
#split into channels
B, G, R = cv2.split(result)
```
## Step-5:
```python
#apply mapping to red channel
R = cv2.LUT(R, redLookupTable)
R = np.uint8(R)

#apply mapping to blue channel
B = cv2.LUT(B, blueLookupTable)
B = np.uint8(B)
```
## Step-6:
```python
#mege the channels
result = cv2.merge([B, G, R])
```
# Now we are going to apply windows to display images.
Windows are used to manipulate out-put screen or screens to be displayed.
```python
#create windows to display images
cv2.namedWindow("image", cv2.WINDOW_NORMAL)
cv2.namedWindow("result", cv2.WINDOW_NORMAL)
```
## Comparing original vs grayscale

```python
cv2.imshow("image", image)
cv2.imshow("result", result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## Images
<p align="center">
	<img src="cat.png" alt="Original png", height=250px,width=350px>
	<img src="warming effect.PNG" alt="Warmed", height=250px,width=340px>
</p>

### Developed by
 [Ashish ku. Behera](https://github.com/ashish-max "Github Id")
