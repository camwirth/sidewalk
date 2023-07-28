# Summary of Object Detection Progress by the USU CV Team

This document, along with the subsequent documents in this folder, offers a comprehensive summary of the work completed by the USU CV team on the Universal Pathways project. Here, we provide an overall summary of our team's methodologies, the challenges we faced, and the results we obtained. For a more in-depth exploration of specific topics and issues, we have included additional documents in this folder. Each of these supplementary documents delves into distinct aspects of our research, presenting detailed explanations, insights, and findings. Brief summaries of the information covered in these additional documents are provided below:
- [Data Problems](): Summary of issues found in the crowdsourced data from Project Sidewalk
- [Mapping Object Detection Output](): Explanation of potential output conversion in maps
- [Evaluation Metrics for Object Detection Models](): Explanation of different evaluation metrics used to explain quality of Object Detection models along with discussion questions on how best to present the models
- [Bounding Box Generation](): Summary of approaches used to generate the bounding box labels given the point source object labels from Project Sidewalk

## Methods

**Algorithms:** We have explored multiple object detection algorithms to conduct a comprehensive comparison for our task. With a primary focus on YOLO-based models, our team also investigated the incorporation of self-attention mechanisms by selecting the Swin Transformer. The five distinct algorithms we have worked with are as follows:

1. YOLOv8
2. YOLOv5
3. YOLOR
4. YOLO-NAS
5. Swin Transformer

Among these algorithms, we have emphasized YOLO-based algorithms due to their popularity and well-established performance. Additionally, Anny's research efforts have been dedicated to assessing the capabilities of the Swin Transformer, a novel approach that introduces a hierarchical attention structure to efficiently process large-scale image recognition tasks.

By employing this diverse set of object detection algorithms, we are working to create comprehensive and insightful comparisons of the strengths and weaknesses of these algorithms in our specific object detection task.

**Datasets:** In our object detection task, we have conducted our research using two primary datasets: San Pedro Garza Garcia, Mexico (SPGG) and Seattle, Washington.

The Seattle dataset stands out for the quantity and quality of the data. With this dataset, we aim to explore object detection performance under optimal conditions and assess the capabilities of the algorithms in a well-developed infrastructure.

On the other hand, the SPGG dataset consists of fewer images and a lower quality infrastrucutre. By utilizing data from SPGG, we seek to investigate the object detection algorithms' ability to detect objects under more challenging circumstances. This dataset offers an opportunity to evaluate the models' robustness and adaptability in locations with fewer resources.

Through the use of these two contrasting datasets, we compare the algorithms' effectiveness across different infrastructural contexts found in different nations. By analyzing the results obtained from both datasets, we can gain valuable insights into the algorithms' performance under varied conditions, leading to a more informed understanding of their real-world applications and limitations.

Table 1 outlines the allocation of different object detection models to individual students and the datasets they have focused on for their research.

Table 1: Object Detection Models and Assigned Datasets

| Object Detection Model | Student | Dataset |
|------------------------|---------|---------|
| YOLOv8                 | Braxton | SPGG    |
| YOLOv5                 | Gavin   | Seattle |
| YOLOR                  | Supriyo | SPGG    |
| YOLO-NAS               | Camille | SPGG    |
| Swin Transformer       | Anny    | Seattle |

**Data Preparation:** Before running training with the data on our algorithms, we pre-processed the data to filter the object labels. To avoid redundancy and overlapping information, we eliminated any datapoints within a 200-pixel radius of each other, attempting to extract a single label for each of the objects in the image. We also filtered out labels using the agree_count and disagree_count variables found in the label metadata. Labels with disagree_count >= agree_count were removed from the data to ensure that only high-quality labels remained in the trained dataset. 

To evaluate the performance of our models and assess possible improvements, we focused on detecting two specific objects of interest: curb ramps and missing curb ramps. These objects hold critical significance in the context of accessibility and urban infrastructure.

1. Curb Ramp:
    - We trained our models to identify existing curb ramps, which are vital for ensuring mobility and access for pedestrians.

2. Missing Curb Ramps:
    - Detection of missing curb ramps is equally crucial to address accessibility gaps and identify areas in need of infrastructure improvements.

While we aimed to include data related to obstacles and surface problems, we encountered challenges due to inconsistent and noisy data. As a result, achieving accurate results for these categories proved difficult. Therefore, we decided to focus our efforts on the curb ramps and missing curb ramps, where we could obtain reliable and meaningful results.

For the Seattle dataset, we created a subset to improve training speed while still preserving a representative sample, given its large size. In contrast, the SPGG dataset retained the entire quantity of filtered data.

After applying the initial data filtration process, Table 2 and Table 3 present the approximate number of images and corresponding labels for the train and test sets associated with the 'Curb Ramp' and 'Missing Curb Ramp' classes for each dataset. 

Table 2: Approximate Quantity of Post-Filtration Data for SPGG Dataset

| Class             | Train Images | Train Labels | Test Images | Test Labels |
|-------------------|--------------|--------------|-------------|-------------|
| Curb Ramp         |
| Missing Curb Ramp |

Table 3: Approximate Quanitty of Post-Filtration Data for Seattle Dataset

| Class             | Train Images | Train Labels | Test Images | Test Labels |
|-------------------|--------------|--------------|-------------|-------------|
| Curb Ramp         |
| Missing Curb Ramp |

Refer to the document [Bounding Box Generation]() for detailed information on the approaches we use to generate bounding box annotations for each of the respective datasets. 

## Challenges
Our research work on different object detection algorithms and datasets has been accompanied by several challenges. This section provides a summary of these encountered problems:

**Poor data quality with crowdsourced labels:** Despite implementing pre-processing steps, the quality of crowdsourced labels obtained from Project Sidewalk has posed significant issues. The main challenges arise from incomplete labeling, inaccurate bounding boxes, and the presence of false labels in the dataset. These problems not only affect the model training process but also make it challenging to accurately evaluate the model's performance. Ground truth comparisons for testing data become unreliable due to inaccuracies in the data labels. For a more detailed analysis of these data-related challenges, refer to the [Data Problems]() document.

**Challenges in distinguishing objects:** Detecting curb ramps, in particular, has proven to be a difficult task, even for human observers. The panorama images used in the project are significantly large, leading to image resizing to expedite processing, but resulting in a loss of resolution and aspect ratio. Furthermore, the similarities between missing curb ramps and curb ramps create a challenge in distinguishing between the two objects accurately. The minute differences between these objects and their similarity to other features make precise detection and classification demanding.

**Difficulty in accurate location extraction:** Extracting accurate location information, specifically latitude and longitude, from the detected objects has been a complex undertaking. The object detection output provides coordinates in pixel values on the image, making the conversion to real-world geospatial coordinates challenging. As a consequence, a considerable margin of error exists in the calculated location, impeding the precise mapping of the detected objects. Further insights into this matter can be found in the [Maps]() document.

## Object Detection Results
In this section, we present the results obtained from the evaluation of our different object detection algorithms applied to the 'Curb Ramp' and 'Missing Curb Ramp' classes. The testing dataset used for evaluation was derived from the crowd-sourced annotations provided by Project Sidewalk. However, it is important to note that the testing data includes inaccuracies, which influence the evaluation of the various models' performances.

For a more comprehensive understanding of the evaluation metrics provided in the following tables, refer to the [Object Detection Metrics]() document, which explains the metrics in detail. It is worth mentioning that each of the tests was conducted using an IoU threshold of 0.5 and a confidence threshold of 0.25.

Table 4: Object Detection Results for Curb Ramp Class

| Model            | Dataset | Precision | Recall | Average Precision |
|------------------|---------|-----------|--------|-------------------|
| YOLOv8           | SPGG    | 
| YOLOv5           | Seattle |
| YOLOR            | SPGG    | 0.611     | 0.55   | 0.777             |
| YOLO-NAS         | SPGG    | 0.286     | 0.829  | 0.577             |
| Swin Transformer | Seattle |

Table 5: Object Detection Results for Missing Curb Ramp Class

| Model            | Dataset | Precision | Recall | Average Precision |
|------------------|---------|-----------|--------|-------------------|
| YOLOv8           | SPGG    | 
| YOLOv5           | Seattle |
| YOLOR            | SPGG    | 0.279     | 0.19   | 0.278             |
| YOLO-NAS         | SPGG    | 0.275     | 0.796  | 0.419             |
| Swin Transformer | Seattle |

Anny and Camille made efforts to manually improve the given test set for their respective datasets. This was done in hopes to achieve a more accurate representation of the test dataset and provide more precise testing results. Table 6 showcases the results for their respective models and datasets based on the manually improved test set. These modifications demonstrated enhanced accuracy for the 'Curb Ramp' class:

Table 6: Object Detection Results for Missing Curb Ramp Class (Improved Test Set)
| Model            | Dataset | Precision | Recall | Average Precision |
|------------------|---------|-----------|--------|-------------------|
| YOLO-NAS         | SPGG    | 0.5227    | 0.8618 | 0.7445            |
| Swin Transformer | Seattle |

Considering the impact of the improved test set on the model performance, it is reasonable to anticipate similar improvements in the results of the other Object Detection models when evaluated with a more accurate test set. These findings underscore the importance of data quality and its influence on the object detection outcomes, further emphasizing the need for robust and precise datasets to enhance the reliability of model evaluations.


## Conclusion and Questions

In conclusion, our USU CV team has made significant progress in object detection to detect Curb Ramps and Missing Curb Ramps. We have explored various algorithms and datasets, gaining valuable understanding of the complex nature of the data, its challenges, and potential.

We have found that one of the key factors critical to the success of our research is the need for higher quality data. Our experiences with the crowdsourced data from Project Sidewalk have highlighted the importance of improving data quality to minimize issues such as incomplete labeling, inaccurate bounding boxes, and false labels. A more accurate and reliable test set is vital for assessing model performance accurately.

As we move forward, our team is working to refine our models to overcome the challenges posed by noisy data and improve data quality. We are researching potential ways to create more robust models to work with the data provided. 

**Questions**
1. How can we enhance the quality of crowdsourced data obtained from Project Sidewalk to mitigate issues like incomplete labeling, inaccurate bounding boxes, and false labels?
2. In addition to the ongoing work with curb ramps and missing curb ramps, what other objects should our team prioritize for detection to further enhance urban accessibility (bus stops, crosswalks, surface problems, etc.)?
3. Which specific performance metrics should we emphasize to showcase the strengths and capabilities of our object detection models more effectively?
