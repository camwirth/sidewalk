# July 25 Update 

## Improved Test Set

I spent a large amount of time last week creating a more accurate test set to ensure that the Curb Ramp Object Detection models I'm running are being accurately tested. Examples of improved image labels are shown below. 

| Original Labels for Image | Improved Labels for Image |
|---------------------------|---------------------------| 
|![](/jul_25/original_images/22t3BWEMJhtwxRXEc1jwmw.jpg) | ![](/jul_25/improved_images/22t3BWEMJhtwxRXEc1jwmw.jpg) |
| ![](/jul_25/original_images/4kOxGkIgHq-Ea5NvoLP44A.jpg) | ![](/jul_25/improved_images/4kOxGkIgHq-Ea5NvoLP44A.jpg) |
| ![](/jul_25/original_images/5WwhGZim8Z_YQWuiSWXiFQ.jpg) | ![](/jul_25/improved_images/5WwhGZim8Z_YQWuiSWXiFQ.jpg) |


I created this test set by including all predicted labels that had a confidence score greater than 0.25. Using both the predicted lables and the given labels, I then manually went through each test image and removed the inaccurate labels. 

I would like to review the test set again to ensure that the changes made represent a quality dataset. 

### Training Results

After creating the new test set, I then re-ran the training using the given train dataset. I added a pre-processing step to remove duplicate bounding boxes by removing bounding boxes that had an iou > 0.5 with another label on the image. 

After training with this dataset and the new test dataset, the results showed a small improvement. A comparison of the performance metrics of the original model, and the new model trained with a more accurate test set can be seen below.

| Model              | Precision | Recall | mAP@0.5 | 
|--------------------|-----------|--------|---------|
| Original Test Set  | 0.2866    | 0.8297 | 0.5774  |
| New Test Set       | 0.5227    | 0.8618 | 0.7445  |

The precision had the greatest increase of about 24% and the recall increased around 3%. I believe this is due to the increased number of accurate labels in the test set. Because of the lack of labeling in the test set previously, the model would accurately predict curb ramps, but these predictions would be counted as false positves becasue the ground truth labels did not represent the object as a curb ramp.

## Ideas to move forward with

I have read some articles about how to move forward and there are 3 papers that interest me the most. These papers are listed below

2. Co-training: Predict pseudo labels for unlabeld data & expand labeled data
    -  https://www.cs.cmu.edu/~avrim/Papers/cotrain.pdf
3. Self-Supervised Learning: self-training approach that uses 'selective net' to identify positive bounding boxes & designate negative examples to a 'safe zone' to prevent negative examples from interfering with training process
    - https://arxiv.org/pdf/2007.09162.pdf
4. Co-mining: based on siamese network & enhances multi-view learning to mine unlabeled instances in sparsely annotated object detection
    - https://arxiv.org/pdf/2012.01950.pdf
    - https://github.com/megvii-research/Co-mining
    

