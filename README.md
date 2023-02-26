# Wisconsin-Autonomous-
![answer](https://user-images.githubusercontent.com/99217383/221426737-814b89b5-8495-48c3-a8ba-f514c7b912f4.png)
**Methodology**

1. Started by converting the BRG imaging to an HSV image because it is easier to detect the red colour that we are interested in.
2. I started by using a masking feature to get all the red colours in the image. I did this using the inRange function from the OpenCv module and took the    red colours by sitting upper and lower bound pixel values for red colours. I took a lower a lower threshold and an upper threshold to get all the red      colours in the picture and combined them using the bitwise_or function from OPenCv
3. Using the morphologyEx function from OpenCv I’m removing the unwanted pixels that were detected as red colours in the above-mentioned threshold            filtering. The morphologyEx function takes images in form of binary pixel values and removes noise from pixel value 1. In this process, the white region    which has value 1 is reduced in size and increased back to the normal size. 
4. The next is followed by finding contours to detect the edges of the cone. 
5. Once the contours have been found there are still some pixels that are being detected apart from the cones. I am using the boundingRect function from      OpenCv to get the X and Y coordinates followed by the width and height of the contours. I use this information to filter the cones on the basis of the      ratio of their width and height, the distances between the two columns and the distances between each consecutive cone in a single column. 
6. The final step is to draw lines through the cones. This can be done using the line() function from OpenCv. But we need to draw lines that extend from      the edges of the image. The drawLine() function does that. 
7. The last step is to save the final product using the imwrite() function from OpenCv.

**What did you try and why do you think it did not work?**

1. I used a GitHub page that had code for detecting the cones(https://gist.github.com/razimgit/d9c91edfd1be6420f58a74e1837bde18). Initially, I started        using all the code from there. But I faced two issues- All the cones were detected but there were parts of the red door also being detected or 13 cones    were being detected. I realized this was the case because of the convex_hull_pointing_up() that was being used. It was custom-made for that picture. So    I made my own version of the manual filtering.
2. I also realized that I didn’t need most of the code and it was redundant, so I filtered out all the unwanted code. I basically didn't end up using          anything apart from the morphologyEx function. 

**What libraries are used**

1. import numpy as np
2. import cv2 
3. from matplotlib import pyplot as plt

