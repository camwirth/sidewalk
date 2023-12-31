# June 27 NSF Convergence Update 

## YOLOX

After spending some time examining the results of YOLOX I discovered why the results are so poor. YOLOX uses pycoco tools and the default coco evaluation metrics. The Average Precision and Average Recall that are saved are evaluated at AP@0.5:95 and AR@0.5:95 which is the average of the AP and AR evaluated at different IoU thresholds ranging from 0.5 to 0.95. 

I took some time to go through the code and change it to extract the AP@0.5 and AR@0.5. I also changed the confidence threshold to be 0.25 during training rather than the default 0.01. This confidence threshold stays consistent throughout all training and evalutation.  After making these changes I retrained the curb-ramp. The following table records the training results. 


#### Curb Ramp Training
| AP@0.5  | AR@0.5  |
|---------|---------|
| 0.542   | 0.673   |


Evaluation Results with added code to record AP@0.5 and AR@0.5

![YOLOX Eval Results](/jun_27/jun_27_eval_results/yolox/curb_ramp_results.png)

Plots of AP@0.5 and AP@0.5:95 for each epoch

![YOLOX Curb Ramp Results](/jun_27/jun_27_tensorboard/yolox/cr_map.png)

I believe that these results are more comparable to the other models; however, they are still limited. I will try to spend more time on YOLOX changing hyperparameters and trying to look into the loss function. 

**Note**
After reading the article Dr. Qi emailed today, I looked into the YOLOX code to understand the evaluation metrics that it is calculating. From examining the code, I believe the mean Precision and Recall are being calculated at different IoU thresholds. . YOLOX saves the best model which produces the highest AP@0.5:95. 

## YOLO-NAS

Using super-gradients, I created scripts to train and evalutate the YOLO-NAS model. There is not much documentation about this model; however, there are some tutorials on how to train the model on a custom dataset. I followed these tutorials to train the model on the curb ramp dataset. I used the default hyperparameters suggested in training YOLO-NAS to begin with. 

The following are the results from the first run of training the model on the curb ramp 

### Curb Ramp Training (YOLO-NAS version 1)
| mAP@0.50 | Recall | Precision | Epoch |
|----------|--------|-----------|-------|
| 0.497    | 0.7094 | 0.383     | 59    |


| mAP@0.5                                                                           | Recall                                                                         | Precision                                                                            |
|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| ![YOLO-NAS Curb Ramp mAP@0.50](/jun_27/jun_27_tensorboard/yolonas/v1/map@0.5.png) | ![YOLO-NAS Curb Ramp Recall](/jun_27/jun_27_tensorboard/yolonas/v1/recall.png) | ![YOLO-NAS Curb Ramp Precision](/jun_27/jun_27_tensorboard/yolonas/v1/precision.png) |

Training Loss

![YOLO-NAS Curb Ramp Train Loss](/jun_27/jun_27_tensorboard/yolonas/v1/train_loss.png)

Validation Loss

![YOLO-NAS Curb Ramp Valid Loss](/jun_27/jun_27_tensorboard/yolonas/v1/valid_loss.png)


The results weren't as promising as I had hoped, so I made some adjustments to the hyper parameters trying to improve the training results. After the following adjustments, I saw around a 5% increase in training performance. The following are the results from the second run of training the model on the curb ramp.

### Curb Ramp Training (YOLO-NAS version 2)
| mAP@0.5 | Recall | Precision | Epoch |
|---------|--------|-----------|-------|
| 0.5431  | 0.7882 | 0.4313    | 22    |

| mAP@0.5                                                                           | Recall                                                                         | Precision                                                                            |
|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| ![YOLO-NAS Curb Ramp mAP@0.50](/jun_27/jun_27_tensorboard/yolonas/v2/map@0.5.png) | ![YOLO-NAS Curb Ramp Recall](/jun_27/jun_27_tensorboard/yolonas/v2/recall.png) | ![YOLO-NAS Curb Ramp Precision](/jun_27/jun_27_tensorboard/yolonas/v2/precision.png) |

Training Loss

![YOLO-NAS Curb Ramp Train Loss](/jun_27/jun_27_tensorboard/yolonas/v2/train_loss.png)

Validation Loss

![YOLO-NAS Curb Ramp Valid Loss](/jun_27/jun_27_tensorboard/yolonas/v2/valid_loss.png)

## Comparison of YOLOX and YOLO-NAS

| Performance Metric | YOLO-NAS | YOLOX |
|--------------------|----------|-------|
| Precision          | 0.4313   | 0.542 |
| Recall             | 0.7882   | 0.673 |
| mAP@0.5            | 0.5431   | ?     |

The results for both YOLO-NAS and YOLOX are very similar. YOLO-NAS has a higher Recall by 11.52%; however, YOLOX has a higher precision by 11.07%. I am assuming that the mAP@0.5 for YOLOX would be somewhat similar to YOLO-NAS. At this point, I think I can move forward with implementing improvements to improve the results in both YOLOX and YOLO-NAS. I would like to look into the evaluation of YOLOX more and see if I can understand how to evaluate all of the performance metrics that I need. 

## Model Output Map Visualization 

I created a way to visualize the output of the cv model. Using the predicted bounding box from model, the lat/long of the object is estimated using code given by Mikey and others working at University of Washington. The estimated lat/long of the object is not perfect. It has an error up to 10-15 meters. I made this map plotting the estimated lat/long points of the detected object. The color of the point is determined based on the confidence score of the detected output. 

[Interactive Map](https://htmlpreview.github.io/?https://github.com/camwirth/sidewalk/blob/main/jun_27/spgg-curb-test-map.html)

## Moving Forward

- Change the loss function in YOLOX by implementing the DecIoU loss function 
- analyze default hyperparameters in YOLOX and try changes to improve results of curb-ramp detection. 
- go through YOLO-NAS code & understand loss function used.
- create map with markers at lat/long coordinates from panorama image and include output image of model predictions
