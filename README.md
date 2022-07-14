# Object Detection and Distance Measurement

**_Authors: Asif Rot & Hay Asa_**

### About the project
We trained a model which will detect and measure the the distnace between the camera to a tree in the forest.
In order to do that, we used object detection and depth algorithms.

### Object Detection
For detecting the trees in the forest, we used YOLOv5 model.
There are almost no models to detect trees so we had to be creative and train the model with images we found.
Image for example from the video we worked on:
![tree_detect](https://user-images.githubusercontent.com/74010095/179062363-16a85ca4-7ce6-4962-8e60-aa28546c9d7e.png)

For the full video - [Click here](https://github.com/Asif-Rot/Object-Detection-and-Distance-Measurement/blob/main/converted_detection.mp4)

### Distance Measurement
For measuring the distance between the camera and the objects, we took every frame's depth and calculated the coordinates.
Hod did we do it - We did a loop on a large number of frames, every time saving each depth:
```
depth_frame = frames.get_depth_frame()
depth_image = np.asanyarray(depth_frame.get_data())
distance_mm = depth_image[320,240]
cv2.circle(color_image,(320,240),6,(0,0,255),-1)
cv2.putText(color_image,"{} mm".format(distance_mm),(320,230),0,1,(0,0,255),2)
```

### Instructions
  * Get a .Bag file - We used a bag file that was created with RealSense camera
  * Go to our "[BagFileToVideo](https://github.com/Asif-Rot/Object-Detection-and-Distance-Measurement/blob/main/BagFileToVideo.ipynb)" Colab project
  * Attach the bag file and change the name of our `test.bag` to the name of your bag file
  * Go to the next Colab project "[YOLOv5_Trees Detection](https://github.com/Asif-Rot/Object-Detection-and-Distance-Measurement/blob/main/YOLOv5_Treesdetection.ipynb)" and follow the steps.
  
  
