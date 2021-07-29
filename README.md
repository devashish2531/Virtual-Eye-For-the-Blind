# Virtual-Eye-For-the-Blind
The project, "Virtual Eye for the Blind," aims to implement object detection algorithms in order to successfully recognize objects in real time from a live camera feed. Furthermore, it aims to use Google's text to speech conversion API in order to showcase our result in an audio format, thus, allowing us to create a device that will recognize the objects in a pedestrian's path and warn them accordingly in an audible manner. 

## Object Detection
For object detection we will be implementing the YOLO or the You Only Look Once algorithm. The YOLO algorithm is one of the fastest and simplest (in terms of complexity of the neural network) for performing object detection. Vigorous research over the years has lead to a rapid decrease in not only the complexity of the network structure but also the time taken by it to perform object detection.

The way YOLO excels is by converting complex object detection problems into much simpler regression problems involving class probabilities. First, a frame is divided into a grid of a predetermined size. Now, a sliding window is used to parse through the grid, mini box by mini box, determining the probability of each mini box containing an object. 

After a single iteration, all the boxes with a higher probability (say >= 0.5) of containing an object class are taken into consideration and bounding boxes are drawn accordingly. These bounding boxes will most likely contain the detected objects respectively.


In order to ensure that the same object is not detected more than once, we introduce 
the concept of non maximum suppression or NMS. In NMS, we consider the boxes with the highest 
confidence value and calculate their IOU (Intersection over union) with other boxes. 

The IOU is the ratio of the area common between two bounding boxes and the total area occupied by both boxes, hence the name, intersection over union. Now, all the boxes having a high IOU with our chosen box are eliminated as they are most likely to be representing the same object. The same process is repeated for the bounding box with the next highest confidence value, until we get our final bounding boxes, each representing a unique object.

## Text To Speech	
Once, the objects have been accurately recognized and their classes determined, we will be using Google's official text to speech conversion API to obtain an audio output of the objects in the viewer's frame, thus completing our device's function

## IMPLEMENTATION 

For feature extraction, we implement a convolutional neural network known as the Darknet 53. 
The dark net 53 is a fully convolutional network comprising of 53 convolutional layers along with 
batch normalization and Leaky ReLu activation layers. No pooling is done.

Once we obtain the extracted features in the form of input, we use them as input for the YOLO model. The yolo comprises of 3 sub models, each with a similar structure in terms of convolutional layers. The three sub models run parallelly, each with a different sized sliding window, thus hoping to locate different sized objects.

In order to detect images, we have used the OpenCV library available in python. This library helps us access stored images on the computer or even use any cameras attached to the device to click a picture on the spot. The clicked picture frame is then passed onto the Yolo Model's "detect image" function, also available in our utils.py. This function, along with the required arguments, runs the detection algorithm on the image and returns it along with the bounding boxes.
 
For our next step, we used Google's official text to speech conversion API. This API offered by google allows us to quickly and accurately convert text into extremely natural sounding speech. It also offers a variety in terms of choice of voices and languages, thus making our project more customer savvy.

## SUMMARY

Therefore, by studying various concepts of deep learning and object detection, and applying them correctly, we have managed to complete our project, “Virtual Eye for the blind” in the given time frame. A more refined version of the project, trained and tested with a high end GPU support will be capable of performing real time object detection thus allowing any needy person to reap its benefits.
