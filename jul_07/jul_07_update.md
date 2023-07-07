# July 7 Update

## Training results on single class

To begin training on the YOLO-NAS model, I trained each of the classes on their own to get the best model. I used the same test/train datasets that Supriyo used. The table below indicates how many train/test images and labels there were in each of the sets.

| Class             | Training Images | Training Labels | Test/Val Images | Test/Val Labels |
|-------------------|-----------------|-----------------|-----------------|-----------------|
| Curb Ramp         | 1162            | 1625            | 266             | 370             |
| Missing Curb Ramp | 3350            | 6099            | 932             | 1747            |
| Surface Problem   | 5346            | 7062            | 1389            | 1855            |

## Calculated results 

**Tested results** 
The results for each of these models is recorded in the model below. These results were calculated at an IoU threshold of 0.5 and a confidence threshold of 0.25

| Class             | Precision  | Recall     | mAP@0.50   |
|-------------------|------------|------------|------------|
| Curb Ramp         | 0.286648   | 0.82972974 | 0.57743275 |
| Missing Curb Ramp | 0.27591676 | 0.79679453 | 0.41995525 |
| Surface Problem   | 0.18699603 | 0.78760105 | 0.2690549  |


The following are the provided plots for each of the models. These plots represent the different metrics accross each Epoch of training. To decrease the training time and increase the number of experiments I can do, I chose to limit each training to 50 epochs.

## Plots
| Class             | Precision                                                           | Recall                                                           | mAP@0.50                                              |
|-------------------|---------------------------------------------------------------------|------------------------------------------------------------------|-------------------------------------------------------|
| Curb Ramp         | ![Curb Ramp Precision](/jul_07/plots/ramp_precision.png)            | ![Curb Ramp Recall](/jul_07/plots/ramp_recall.png)               | ![Curb AP](/jul_07/plots/ramp_ap.png)                 |
| Missing Curb Ramp | ![Missing Curb Ramp Precision](/jul_07/plots/missing_precision.png) | ![Missing Curb Ramp Recall](/jul_07/plots/missing_precision.png) | ![Missing Curb Ramp AP](/jul_07/plots/missing_ap.png) |
| Surface Problem   | ![Surface Problem Precision](/jul_07/plots/sf_precision.png)        | ![Surface Problem Recall](/jul_07/plots/sf_recall.png)           | ![Surface Problem AP](/jul_07/plots/sf_ap.png)        |

| Class             | Training Loss                                                            | Validation Loss                                                            |
|-------------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------|
| Curb Ramp         | ![Curb Ramp Training Loss](/jul_07/plots/ramp_train_loss.png)            | ![Curb Ramp Validation Loss](/jul_07/plots/ramp_valid_loss.png)            |
| Missing Curb Ramp | ![Missing Curb Ramp Training Loss](/jul_07/plots/missing_train_loss.png) | ![Missing Curb Ramp Validation Loss](/jul_07/plots/missing_valid_loss.png) |
| Surface Problem   | ![Surface Problem Validation Loss](/jul_07/plots/sf_train_loss.png)      | ![Surface Validation Loss](/jul_07/plots/sf_train_loss.png)                |

## Training results on multiple classes

After completing training on each of the classes alone, I started training models with multiple classes. I first started with both Curb Ramp and Missing Curb Ramp. Once that was finished I trained a model with Curb Ramp, Missing Curb Ramp, and Surface Problems. 

Before training the model I prepared a dataset that was somewhat balanced with a similar number of train/test images for each of the classes. I ensured that any images with labels from more than one class were included in the datasets. 

The following table shows the number of test/train images and labels that were used to train the model with Curb Ramp and Missing Curb Ramp classes. 

### Missing Curb Ramp and Curb Ramp

|-------------------------------------------------------------------------------------------|
| Class             | Training Images | Training Labels | Test/Val Images | Test/Val Labels |
|-------------------|-----------------|-----------------|-----------------|-----------------|
| Curb Ramp         | 1162            | 1625            | 266             | 370             |
| Missing Curb Ramp | 1162            | 2168            | 266             | 498             |
| Total             | 2019            | 3783            | 510             | 868             |


**Tested results** 
The results for this model are shown below. The YOLO-NAS does not directly give the individual metrics for each class. However, after looking through the source code I was able to find where these metrics are calculated and record them. The total metrics are the metrics that are originally recorded by the YOLO-NAS training model. These are an average of all the individual class metrics. 

| Class             | Precision  | Recall     | mAP@0.50   |
|-------------------|------------|------------|------------|
| Curb Ramp         | 0.2647     | 0.7568     | 0.4800     |
| Missing Curb Ramp | 0.2020     | 0.7570     | 0.2895     |
| Total             | 0.23334336 | 0.75689244 | 0.38476145 |


### Missing Curb Ramp, Curb Ramp, Surface Problem

I trained a model using all three classes. The number of images and labels per class are recorded in the table below. 

| Class             | Training Images | Training Labels | Test/Val Images | Test/Val Labels |
|-------------------|-----------------|-----------------|-----------------|-----------------|
| Curb Ramp         | 1162            | 1625            | 266             | 370             |
| Missing Curb Ramp | 787             | 1626            | 204             | 372             |
| Surface Problem   | 1200            | 1626            | 279             | 371             | 
| Total             | 2525            | 4877            | 605             | 1113            | 


**Tested results** 
The following table are the results for the "best" model that the training gave as an output. This is the model with the highest average mAP@0.50.

| Class             | Precision  | Recall     | mAP@0.50   |
|-------------------|------------|------------|------------|
| Curb Ramp         | 0.2157     | 0.7514     | 0.4437     |
| Missing Curb Ramp | 0.2047     | 0.7121     | 0.2462     |
| Surface Problems  | 0.1257     | 0.5380     | 0.1216     |
| Total             | 0.18200349 | 0.66716694 | 0.27050495 |

<!-- 
**Visual Examples**
| Class | False Positive | False Negative | True Positive |
|-------|----------------|----------------|---------------|
| Curb Ramp |
| Missing Curb Ramp |
| Surface Problems |
| Missing Curb Ramp & Curb Ramp |
| Missing Curb Ramp & Surface Problem |
| Missing Curb Ramp & Curb Ramp & Surface Problem |
| Curb Ramp & Surface Problem | -->




## Moving Forward/Notes

I think that most of the issues with the model results are coming from poorly labeled data. Especially for surface problems, not all surface problems are recorded and it is difficult to determine what a surface problem is. I am wondering if it would be worthwhile to hand-label a smaller portion of the data to ensure that it is accurate. Is it better to train the models on a larger dataset with inaccurate labels? Or is it better to have a smaller dataset with accurate labels?

Here are a few things I am interested in doing to try to improve the model
- hand label a small selection of images and try training the model on these images
- Try training the model on the Seattle Dataset to compare the different datasets and the accuracy
- Look into minor improvements that can be implemented in YOLO-NAS (start with the hyperparameters explained [here](https://github.com/Deci-AI/super-gradients/blob/master/src/super_gradients/recipes/training_hyperparams/default_train_params.yaml) along with the [source code](https://github.com/Deci-AI/super-gradients/blob/master/src/super_gradients/training/params.py))
    - different loss functions
    - different learning rates
    - different optimizers & optimizer parameters


Here is a great tutorial for future reference: [Tutorial](https://colab.research.google.com/drive/1q0RmeVRzLwRXW-h9dPFSOchwJkThUy6d#scrollTo=tYZw6UvePBv5)