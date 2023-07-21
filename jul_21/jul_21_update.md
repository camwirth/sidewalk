# July 21 Update

# DivideMix Issues

Working with the DivideMix algorithm for Object Detection has been difficult. DivideMix is designed for Image Classification, and adapting it for Object Detection would be complex and time-consuming. I ran DivideMix on a modified dataset for binary classification on Curb Ramps by taking crops of various labels. It did not yield satisfactory results. The issues I have encountered with DivideMix are:

1. DivideMix is not suitable for Binary Classification, leading to label imbalance and difficulties in splitting based on entropy or pseudo-labeling.

2. The algorithm introduces new hyperparameters that require extensive fine-tuning, adding to the complexity of training.

3. DivideMix utilizes two models to be trained simultaneously. This doubles the time required, and converting the Image Classification output to bounding box labels complicates the process further.

4. DivideMix produced inaccurate predictions for the Binary Image Classification of Curb Ramps, achieving only around 50% accuracy.

## Proposed Steps Forward
Based on the challenges faced, I have decided to move forward with the following:

1. Discontinue experiments with DivideMix, as fine-tuning hyperparameters is time-consuming and unlikely to produce satisfactory results.

2. Train the Object Detection Model (YOLO-NAS) using an improved test set. A more accurate test set was created during the DivideMix experiment by combining predicted labels from the Curb Ramp Only model with confidence scores of 0.25 or higher. I then manually removed inaccurate labels from the images leaving only the most high-quality labels.

3. Explore Self-Supervised training. Given that missing labels are a major problem with the data, incorporating predictions from the Object Detection model during training, especially those with high confidence scores, may be helpful. Refer to this paper [here](https://ojs.aaai.org/index.php/AAAI/article/view/16385) for more insights into self-supervised training and incorporating predictions into the training data.
