# Aug 9 Meeting with Dr. Qi


# 1. Training with bounding boxes on Bus Stop images

To convert from the polygon annotations to the bounding box annotations I found the max (x,y) coordinate from the points and the min (x,y) coordinate. The mid point was calculated to be the average of the points: xmid = (xmax + xmin) / 2, ymid = (ymax + ymin) / 2. The width and height was calculated by taking the difference of xmax and xmin and ymax and ymin respectively. 

| Polygon Annotation | Bounding Box Annotation |
|--------------------|-------------------------|
| ![](/aug_09/polylines.png) | ![](/aug_09/gsv-36543-dR4xCMHTuAjdilURgQfWrQ-1687415947491_jpg.rf.cf020d190e4177560aaee1c58463f1f0.jpg) |

| Class    | Train Images | Train Labels | Valid Images | Valid Labels | Test Images | Test Labels |
|----------|--------------|--------------|--------------|--------------|-------------|-------------|
| Seating  | 216          | 274          | 58           | 70           | 30          | 39          |
| Shelter  | 296          | 305          | 85           | 87           | 40          | 41          |
| Signage  | 377          | 377          | 102          | 102          | 57          | 57          |
| Trashcan | 250          | 254          | 67           | 67           | 34          | 34          |
| Total    | 462          | 1210         | 132          | 362          | 67          | 171         |

Total Images: 661
Total Labels: 1,743


**Results**

| Class    | Precision | Recall | Average Precision | F1     |
|----------|-----------|--------|-------------------|--------|
| Seating  | 0.4857    | 0.8718 | 0.7790            | 0.6239 |
| Shelter  | 0.8667    | 0.9512 | 0.9505            | 0.9070 |
| Signage  | 0.8088    | 0.9649 | 0.9562            | 0.8800 |
| Trashcan | 0.6667    | 0.9412 | 0.9333            | 0.7805 |
| Total    | 0.7069    | 0.9322 | 0.9047            | 0.7978 |


The results for these objects are significantly better than the results from the curb ramp object detection. I don't believe this is because these objects are more recognizeable, I believe that the quality of the images significantly affects the outcome of the model. It is worthwhile to consider ways we can extract higher quality images for curb ramps. 

## Moving Forward 
- research ways to estimate the bearing angle of a curb ramp object
- extract data for bus stops in different locations and see how the model compares
- continue to work with Minchu on knowledge transfer of BusStopCV

<!-- ## 2. Find ways to download better data from Google API

Google Streetview API has a variety of resources to download the images. We can download the panoramas in the same way the UW team has done, or we can transition to downloading single images of a given view. 

This view is similar to the screenshot taken for the Bus Stop location. The panorama image gives a 360 degree view of a location. Specifying the bearing angle (angle from north) that is desired, will give a single view of that panorama image, rather than the entire 360 view. 

Given 2 lat/long locations this bearing angle is easily calculated. Given the bearing angle, the correct view of the object in the image can be found. Figure 1 shows an explanation of this bearing angle form 2 points. 



This is a simple task with Bus Stop data because it is easy to locate the lat/long of the Bus Stop in the city data. Once the nearest panorama image is found, calculating the bearing angle between the lat/long point of the panorama and the lat/long coordinates of the Bus Stop is possible. With this information, a better view of the bus stop is achieved without any required user input. 

Below are screenshots of the 3 nearest panoramas to a Bus Stop location. The bearing has been calculated to point the camera towards the bus stop in each of these images. 

I believe it is possible for us to do something similar to calculate the desired bearing angle for a given view at an intersection for curb ramps. However, this task becomes more difficult. We do not have lat/long data on where curb ramps should be located throughout the city. However, I have some ideas for how we can estimate a bearing angle given the direction of the intersections. -->