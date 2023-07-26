# Evaluating Computer Vision Model Performance: Understanding Key Metrics

Evaluating the performance of Computer Vision Models is essential to ensure their accuracy and effectiveness in real-world applications. Three key metrics, Precision, Recall, and Average Precision, play a crucial role in assessing the model's capabilities. These metrics compare the model's predictions on a 'test set' with the ground truth labels, providing valuable insights into the model's strengths and weaknesses.

## Three main metrics

1. **Precision:** Precision measures how accurate the model's predictions are. It's the ratio of correctly predicted curb ramps to all the predicted curb ramps (both correctly and incorrectly predicted). A higher precision means fewer false positives (incorrect predictions).

2. **Recall:** Recall measures how well the model can find all the possible curb ramps in the image. It's the ratio of correctly predicted curb ramps to all the actual curb ramps present in the image. A higher recall means fewer false negatives (missed detections).

3. **Average Precision:** Average Precision combines both precision and recall by calculating the area under the curve when plotting precision against recall. It provides an overall measure of the model's performance.

## Confidence Threshold

In an object detection model, each prediction is associated with a confidence score, indicating the model's level of certainty about the predicted object's existence. The confidence threshold determines which predictions should be considered valid during evaluation. For instance, using a confidence threshold of 0.25 means that only predictions with a confidence score of 25% or higher will be taken into account during evaluation.

## Trade-off between Precision and Recall

Choosing a confidence threshold involves balancing the trade-off between precision and recall. Lower thresholds increase the chances of detecting all curb ramps but may include more false positives. Higher thresholds focus on high-confidence predictions, improving precision but potentially missing some curb ramps.

The table below illustrates the impact of different confidence thresholds on precision, recall, and average precision, using the YOLO-NAS model trained on a set of images containing curb ramps.

| Confidence Threshold | Precision | Recall | Average Precision |
|----------------------|-----------|--------|---------|
| 0.0                  | 0.0097    | 0.9976 | 0.7856  |
| 0.1                  | 0.1025    | 0.9789 | 0.7843  |
| 0.2                  | 0.3911    | 0.9297 | 0.7697  |
| 0.25                 | 0.4889    | 0.8805 | 0.7526  |
| 0.3                  | 0.5665    | 0.8173 | 0.7158  |
| 0.4                  | 0.7264    | 0.7400 | 0.6719  |
| 0.5                  | 0.8282    | 0.5761 | 0.5408  |
| 0.6                  | 0.9183    | 0.4215 | 0.4096  |
| 0.7                  | 0.9591    | 0.2201 | 0.2233  |
| 0.8                  | 1.0       | 0.0444 | 0.0495  |

As shown in the table, changing the confidence threshold from 0.0 to 0.8 significantly affects the model's performance. Lower confidence thresholds, such as 0.25, result in higher recall scores, indicating the model detects a larger portion of the true curb ramps present in the images. However, this comes at the cost of decreased precision, leading to more false positive predictions.

On the other hand, higher confidence thresholds, like 0.8, improve precision by considering only high-confidence predictions, resulting in fewer false positives. However, this leads to a lower recall, meaning the model may miss detecting many true curb ramps.

## Questions and Conclusions

Evaluating the performance of computer vision models using metrics such as Precision, Recall, and Average Precision is crucial for optimizing their effectiveness in the real-world application of our project. When assessing the performance of our model for curb ramp detection, we must carefully consider the confidence threshold to find the right balance between accurately identifying all curb ramps and minimizing false positives.

**Questions:**
1. What specific objectives does our project aim to achieve with the curb ramp detection model? Are we prioritizing high recall to ensure all curb ramps are identified, or are we focused on maximizing precision to reduce false positives?

2. What is the impact of different confidence thresholds on precision and recall? Can we identify a threshold that balances both metrics effectively?

3. Which metrics should be prioritized and presented to the audience of the paper? Should we focus on explaining each metric's relevance, or highlight the most critical metric(s) that align directly with our project's objectives and decision-making process?
