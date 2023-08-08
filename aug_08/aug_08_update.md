# August 8 Update

## Bus Stop Data

**BusStopCV**

I have been working with Minchu on the BusStopCV project. Working on this, I have learned the following about the BusStopCV project

1. The data found [here](https://universe.roboflow.com/projectsidewalk/streetscapecv/dataset/10) has been created using Polygon annotations rather than bounding box annotations. Polygon annotations should work with YOLOv5 and YOLOv8 as explained in [this article](https://blog.roboflow.com/polygons-object-detection/). However, for the other object detection algorithms, we must convert these annotations to bounding box annotations. 
2. The images used for the train/test data for the object detection task were taken as Google Street View screenshots in the BusStopCV application. This means that the images are more zoomed in and focused on the objects. 
3. The BusStopCV project attempts to use computer vision to aid users in labeling objects.

## Mapping Panoramas to Intersections

I have created a script to map the panorama images with intersections in a given city. Below is a map of all intersections and panorama images. 

<iframe src="https://camwirth.github.io/sidewalk/aug_08/intersections_panos.html" width="1000" height="800"></iframe>

A csv file of these panorama images mapped to the intersection id can be found [here](https://github.com/camwirth/sidewalk/blob/main/aug_08/Intersection_Seattle(1).csv)