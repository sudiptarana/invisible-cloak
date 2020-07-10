# invisible-cloak
invisible cloak using openCv-python

## Getting Started

If you are a Harry Potter fan , you would know what an Invisibility Cloak is.
Yes! It’s the cloak that makes Harry Potter invisible.
 This happen with few line of python code in OpenCV.

1. Capture and store the background frame [ This will be done for some seconds ]
2. Detect the red colored cloth using color detection and segmentation algorithm.
3. Segment out the red colored cloth by generating a mask. [ used in code ]
4. Generate the final augmented output to create a magical effect.

### Prerequisites

You need to install the following libraries

```
import cv2
import time
import numpy as np

```

### Installing

Aa step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo


## Running the tests

# in order to check the cv2 version  
```python
print(cv2.__version__)   
```

# taking video as input through webCam 
```python
cap = cv2.VideoCapture(0) 
```

# give the camera to warm up 
```python
time.sleep(2)
background=0  
```

# capturing the background in range of 60 
```python
for i in range(30):
    ret,background = cap.read()
```

# we are reading from video 
```python
while(cap.isOpened()):
    ret , img = cap.read()

    if not ret:
        break
```
# convert the image - BGR to HSV 
# as we focused on detection of red color  
  
# converting BGR to HSV for better  
# detection or you can convert it to gray 
```python
 hsv = cv2.cvtColor(img , cv2.COLOR_BGR2HSV)
```

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc