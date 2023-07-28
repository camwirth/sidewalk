# Problems with Crowdsourced Project Sidewalk Data

- disclaimer: this section deals specifically with curb ramps and missing curb ramps (see [Object Explanation]() section for why)

We discovered 3 major problems in the crowdsourced data from project sidewalk (These problems were found both in SPGG and Seattle but images from SPGG will be referred to)

1. Missing Labels
2. Inaccurate Bounding Boxes
3. Incorrect Labels
4. Labeling of Driveways


## Missing Labels
- not all objects at each intersection are labeled
- some objects are labeled multiple times (can remove this at risk of removing labels for differing objects)

## Inaccurate Bounding Boxes
- labels for objects include only centerpoints 
- estimating bounding boxes is not always correct due to the nature of the panorama (used crop code linked [here]())
- center points for labels are off-centered making it more difficult to include the object within the bounding box

## Incorrect Labels
- using the agree count > dissagree count labels were filtered to promote accuracy
- there continue to remain errors in the object labels (specifically in the missing curb ramp category)

## Labeling of Driveways
- classifying driveways as curb ramp is inconsistent and incomplete
- some driveways are marked as missing curb ramps confusing the computer 


## Images of Intersections
- images of intersections as a whole provide more consistent and accurate results 
* example image and link to the streetview of that location

## Images of Streets
- images taken at streets are more difficult to detect due to the driveway training data and lack of curbs/missing curbs. The view of the curb ramps/ missing curb ramps is also significantly farther away making the objects in the image smaller and more difficult to detect
* example of image farther from intersection 
* example of image close to intersection 
* link to streetview of location

- images on streets with no intersection nearby have lower-quality results
* example of image on the street
* link to streetview of location

## different perspectives and panoramas for the same intersections
- a single street or intersection has multiple panoramas that can be produced. Some perspectives provide better results than others as the image is clearer
- multiple images can be given and multiple predictions will result. These predictions must be combined in some way and disagreeing predictions for the same intersection but different panoramas must somehow be addressed

## Conclusions
- Easiest way to improve the models is to provide good, clean training data
- Discuss whether curb ramps/ missing curb ramps are desired to be detected within a street or if the focus is at intersections
    - Prediction quality will be much higher at high-quality images of a single intersection
- What is the desire with a driveway? Should they be included as curb ramps or missing curb ramps? 


