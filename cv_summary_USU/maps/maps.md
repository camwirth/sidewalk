# Mapping Predicted Lables

In this report, we present our efforts to map the output of an object detection model used for identifying curb ramps in urban environments. Our objective was to visualize the detected curb ramps on a map, both by estimating their individual latitude and longitude and by using the given latitude and longitude of panorama images. We aimed to assess the accuracy of the model's predictions and identify potential areas of improvement.

## 1. Mapping Estimated Lat/Long of individual labels

The first map we generated aimed to plot each detected curb ramp on the map using calculated latitude and longitude values. The coloring of each point on the map indicates the confidence score of the object label, representing the model's certainty in its predictions. It's important to note that this confidence score doesn't determine the quality of the object (e.g., accessible curb ramp), which requires further assessment and validation.

**Calculation of Latitude and Longitude:**
To estimate the latitude and longitude of individual curb ramps, we employed a method previously used and validated by Mikey and the UW team. The core of this estimation lies in calculating the distance from the object to the camera and determining the heading angle. With these two components, along with the latitude and longitude of the panorama image, and the pixel coordinates (x, y) of the object, we derived the approximate latitude and longitude of the curb ramp using the haversine distance formula.

_Calculation of Distance and Heading:_

The first step in our estimation involved calculating the distance from the curb ramp to the camera. We used the formula:

```python
distance = 18.6051843 + 0.0138947 * (pano_height / 2 - y)
```

where `pano_height` represents the height of the panorama image, and `y` denotes the vertical pixel coordinate of the object. This formula provides an estimated distance in meters based on the position of the object within the panorama.

Next, we determined the heading angle, which indicates the object's horizontal direction relative to the camera's view. The heading was calculated using the formula:

```python 
heading = 360 * x / pano_width
```

Here, `x` corresponds to the horizontal pixel coordinate of the object, and `pano_width` denotes the width of the panorama image. This heading angle played a crucial role in orienting the object's position with respect to the camera's field of view.

_Applying the Haversine Distance Formula:_

Having obtained the distance and heading, we combined this information with the latitude and longitude of the panorama image. Using these parameters and the pixel coordinates of the object, we applied the haversine distance formula, a standard method for calculating the distance between two points on the Earth's surface given their latitude and longitude. This approach allowed us to estimate the approximate latitude and longitude of the curb ramp's location within a general area.

_Limitations of the Approach:_

This estimation method has significant limitations. While our approach can estimate the general area of the object's location, it does not guarantee pinpoint accuracy. As shown in the map below (Figure 1), the plotted positions of the detected objects do not align precisely with their actual physical locations. Consequently, this lack of precision may pose challenges when trying to identify the exact placement of curb ramps in urban environments.

Figure 1: Map with Estimated Lat/Long

[Full Map](https://camwirth.github.io/sidewalk/cv_summary_USU/maps/html_files/spgg-curb-test-map.html)

<!-- (map isn't fitting correctly in the iframe right now, look at the link above for the correct map) -->

<iframe src="https://camwirth.github.io/sidewalk/cv_summary_USU/maps/html_files/spgg-curb-test-map.html" width="1000" height="800"></iframe>


## 2. Mapping Lat/Long of Pano

For a more accurate approach, we utilized the given latitude and longitude data of the panorama image. A score was generated for each intersection by calculating the ratio of detected curb ramps to the total number of potential curb ramps `score = (curb ramps / (curb ramps + missing curb ramps))`. Instead of pinpointing the exact location of each object, this method represents general areas of interest on the map and suggests potential areas of improvement.

Figure 2: Map with Lat/Long of Pano

[Full Map](https://camwirth.github.io/sidewalk/cv_summary_USU/maps/html_files/map.html)

<iframe src="https://camwirth.github.io/sidewalk/cv_summary_USU/maps/html_files/map.html" width="1000" height="800"></iframe>
<!-- look into why the images don't pop up?? -->

 It should be highlighted that the predictions displayed in the maps have been filtered to represent an ideal scenario rather than depicting the complete output of the current object detection model. This filtering was done to provide a more focused analysis and facilitate the identification of areas that require attention.

## Conclusions

Based on our mapping efforts, we draw the following conclusions:

1. Generating precise latitude and longitude points for each individual object using the object detection model is challenging and leads to inaccuracies in the plotted locations.

2. Utilizing general scores based on the number of detected curb ramps and missing curb ramps at each intersection provides a more accurate representation of potential areas of improvement.