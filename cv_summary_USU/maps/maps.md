# Mapping Predicted Lables

## 1. Mapping Estimated Lat/Long of individual labels

- lat/long for each predicted label is generated using code from Mikey
- the coloring is based on the confidence of the label (NOT whether the label marks a 'good' or 'bad' object)
- lat/long is not precise.. it is within the general area, but it does not pinpoint the object exactly where it is. 

<iframe src="https://github.com/username/repository/raw/main/path/to/your/map.html" width="600" height="400"></iframe>

## 2. Mapping Lat/Long of Pano

- 'score' determined for each pano (#curb ramps / total number of ramps)
- suggests areas of improvement rather than locating each ramp/missing ramp

<iframe src="https://github.com/username/repository/raw/main/path/to/your/map.html" width="600" height="400"></iframe>


## Conclusions

- generating latitutde and longitude points for each individual object is difficult and inaccurate
- general scores based on number of curb ramps and missing curb ramps can be generated for each intersection
- prediction quality is significant for finding curb ramps on intersections rather than on general sidewalks (see the [Data Problems]() section in the github repo)