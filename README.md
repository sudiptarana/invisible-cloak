# invisible-cloak
invisible cloak using openCv-python

## Getting Started

If you are a Harry Potter fan , you would know what an Invisibility Cloak is.
Yes! It’s the cloak that makes Harry Potter invisible.
This happen with few line of python code in OpenCV.

### It's working principle
1. Capture and store the background frame [ This will be done for some seconds ]
2. Detect the red colored cloth using color detection and segmentation algorithm.
3. Segment out the red colored cloth by generating a mask. [ used in code ]
4. Generate the final augmented output to create a magical effect.

### Installing

* [Python](https://www.python.org/downloads/) - Install Python
* [opencv-python 4.3.0.36](https://pypi.org/project/opencv-python/) - Wrapper package for OpenCV python

### Let’s Start
You need to import the following libraries

```python
import cv2
import time
import numpy as np
```

### in order to check the cv2 version  
```python
print(cv2.__version__)   
```

### taking video as input through webCam 
```python
cap = cv2.VideoCapture(0) 
```

### give the camera to warm up 
```python
time.sleep(2)
background=0  
```

### capturing the background in range of 60 
```python
for i in range(30):
    ret,background = cap.read()
```

### we are reading from video 
```python
while(cap.isOpened()):
    ret , img = cap.read()

    if not ret:
        break
```
### convert the image - BGR to HSV  
```python
 hsv = cv2.cvtColor(img , cv2.COLOR_BGR2HSV)
```

### depending upon the color of your cloth , the block of code could be replaced

```python
 #-------------------------------------BLOCK----------------------------# 
    # ranges should be carefully chosen 
    # setting the lower and upper range for mask1 
    lower_red = np.array([0,120,70])
    upper_red = np.array([10, 255, 255])
    mask1 = cv2.inRange(hsv , lower_red , upper_red)
    # setting the lower and upper range for mask2  
    lower_red = np.array([170, 120, 70])
    upper_red = np.array([180, 255, 255])
    mask2 = cv2.inRange(hsv, lower_red, upper_red) 
    #----------------------------------------------------------------------# 
```

### Refining the mask corresponding to the detected red color
```python
    mask1 = cv2.morphologyEx(mask1, cv2.MORPH_OPEN,
                             np.ones((3,3),np.uint8),iterations=2) #Noise Removal
    mask1 = cv2.morphologyEx(mask1, cv2.MORPH_DILATE,
                             np.ones((3,3), np.uint8), iterations=1) #smmoting the image

    mask2 = cv2.bitwise_not(mask1)
```

### Generating the final output 
```python
    res1=cv2.bitwise_and(background , background , mask = mask1)
    res2 = cv2.bitwise_and(img , img , mask = mask2)

    final_output = cv2.addWeighted(res1,1,res2,1,0)
```

### final output screen 
```python
    cv2.imshow("Hey invisible..!", final_output)
    k = cv2.waitKey(10)
    if k == ord('s'):
        break
```

### Destroy All Screen 
```python
cap.release()
cv2.destroyAllWindows()
```

## Authors

* **invisible-cloak** - [sudiptarana](https://github.com/sudiptarana)

## Acknowledgments

* geeksforgeeks
* medium