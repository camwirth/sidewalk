# Mapping Predicted Lables

- generated two different maps for visualizing the output of the object detection task

## 1. Mapping Estimated Lat/Long of individual labels

- this map aims to plot each of the detected curb ramps on the map using a calculated latitude/longitude
- the coloring of each of the points is based on the confidence of the label (make distinction from whether labels are good or bad objects)

**Calculation of Latitude and Longitude:**
- used method explained by Mikey that the UW team has previously used
- calculate the distance using code linked here
- using the distance and the given lat/ long data from the pano image calculate the lat /long using the haversine distance formaula


This lat/long is not precise. It is within a general area, but it does not pinpoint the exact object 

<iframe src="https://raw.githubusercontent.com/camwirth/sidewalk/main/cv_summary_USU/maps/html_files/map" width="600" height="400"></iframe>

As can be seen in this map, the objects do not land in accurate locations and it is difficult to pinpoint where the object should actually stand

## 2. Mapping Lat/Long of Pano

- more accurate approach was to use the given latitude longitude for the panorama image
- a score was generated for the image (intersection) by taking the number of detected curb ramps and divide it by the total number of potential curb ramps (curb ramps / curb ramps + missing curb ramps)
- rather than trying to pinpoint the exact location of the object general areas of interest are represented (suggested areas of improvement)

<iframe src="https://raw.githubusercontent.com/camwirth/sidewalk/main/cv_summary_USU/maps/html_files/map" width="600" height="400"></iframe>

- note that predictions on images have been filtered to represent an ideal situation rather than the complete total output of the current object detection model.


## Conclusions

- generating latitutde and longitude points for each individual object is difficult and inaccurate
- general scores based on number of curb ramps and missing curb ramps can be generated for each intersection