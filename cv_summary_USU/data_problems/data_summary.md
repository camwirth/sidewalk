# Problems with Crowdsourced Project Sidewalk Data

As we have been working with the Project Sidewalk data, we have encountered significant challenges in adapting it for our object detection task. The Project Sidewalk data was originally designed to validate cropped images rather than gather data for all objects in a single panorama. This poses difficulties, as labels created for objects at a given intersection may be spread across different panoramas. While the entire intersection is essentially "labeled," Google Street View's multiple panoramas contribute to this dispersal. The filters we use during pre-processing, particularly the agree_count > disagree_count filter, may lead to the exclusion of labels for objects simply because they haven't been validated yet. As we employ this data for object detection, we have identified four major problems:

1. Missing Labels: Some objects in a panorama intersection are not labeled, leaving gaps in the data.
2. Inaccurate Bounding Boxes: The way objects are labeled often includes only centerpoints, making it challenging to precisely estimate the object's boundaries within the panorama.
3. Incorrect Labels: Despite efforts to filter data based on agreement, errors remain in the object labels, particularly regarding the missing curb ramp category.
4. Labeling of Driveways: Inconsistent and incomplete classification of driveways as curb ramps causes confusion during the object detection process.

**1. Missing Labels**
One of the primary challenges we face with the Project Sidewalk data is the issue of missing labels in panorama intersections. While the Project Sidewalk software aims to label objects at these intersections, not all objects in each panorama image are consistently labeled, resulting in incomplete data. 

Objects are commonly labeled multiple times in the same panorama, leading to confusion and difficulties in handling data associated with different objects. To mitigate this, we have implemented filters to limit duplicate labels; however, this approach carries the risk of inadvertently removing labels that pertain to distinct objects.

Another factor contributing to missing labels is the application of initial quality filters during data pre-processing. While these filters aim to ensure data accuracy, they may inadvertently exclude valid labels that have not yet been fully validated. Disagreements among individuals labeling the objects may result in certain labels being filtered out, especially in cases where there is uncertainty about whether an object is a curb ramp or not.

Examples of panorama images with missing labels are included below. 

| ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/missing_labels/0ZxrPRUFN51hrdr9y2KL4g.jpg) | ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/missing_labels/4kOxGkIgHq-Ea5NvoLP44A.jpg) | ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/missing_labels/4kOxGkIgHq-Ea5NvoLP44A.jpg) |

**2. Inaccurate Bounding Boxes**
Another significant challenge we encounter with the Project Sidewalk data is the issue of inaccurate bounding boxes for labeled objects. The labeling process in Project Sidewalk provides only centerpoints to indicate the object's presence. This limited information makes it difficult to estimate precise bounding boxes that encompass the entire object accurately. As a result, the generated bounding boxes may not fully encapsulate the object, leading to inaccuracies in the data.

Additionally, the off-centered nature of center points for labels adds another layer of complexity to the bounding box generation process. Ensuring that the object is correctly enclosed within the bounding box becomes more challenging due to the lack of precise location information.

Refer to the [Bounding Box Generation](https://camwirth.github.io/sidewalk/cv_summary_USU/bounding_box/box.html) docmument for more information about methods we have employed to estimate boudning boxes for each object.

**3. Incorrect Labels**
Even though we use the "agree count > disagree count" filter to make the labels more accurate, we still face challenges with misclassifications, especially when trying to distinguish between missing curb ramps and existing curb ramps. This difference in interpretation makes it difficult to achieve consistent and precise labeling. As a result, some objects that should be marked as missing curb ramps might mistakenly receive curb ramp labels, and vice versa.

Examples of panorama images with incorrect labels are included below. 

| ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/incorrect_labels/6H2KpDa0Gboi0XudOD-a4Q.jpg) | ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/incorrect_labels/FD89SREoJ6ptzurGkRLLvQ.jpg) | ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/incorrect_labels/hgc6apPdGlUZXZRdvAQ1PQ.jpg) |


**4. Labeling of Driveways** 
The classification of driveways in the data is both inconsistent and incomplete. Driveways are consistently marked as both missing curb ramps and curb ramps, which can create confusion for the computer vision models. This misclassification makes it unclear what specific properties the computer should look for when detecting and distinguishing driveways as either a curb ramp or missing curb ramp. This inconsistency poses challenges in accurately identifying and labeling driveways, leading to potential errors in the object detection process. To address this issue, we need to establish clearer guidelines and criteria for accurately labeling driveways.

Examples of panorama images this confusion of inconsitent labeled driveways are included below. 

| ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/driveways/5C3Pb2g_q6gSXdccde-cPg.jpg) | ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/driveways/6bjoRhtmn6IyawXd-_SY5A.jpg) | ![](https://camwirth.github.io/sidewalk/cv_summary_USU/data_problems/driveways/5C3Pb2g_q6gSXdccde-cPg.jpg) |

<!-- ## Analyzing Highest Quality data
When analyzing the highest quality data in Project Sidewalk, we have observed some important findings:

1. Utilizing images of entire intersections tends to yield more consistent and accurate results for our object detection task. By capturing the entire scene in a single image, we can better understand the context and spatial relationships between objects, which enhances the accuracy of object detection.

2. A single street or intersection can be captured from multiple panoramas. We have noticed that some perspectives provide clearer and more informative images compared to others. Choosing the most informative panoramas for labeling and training our models can significantly improve the overall performance of our object detection system.

3. When multiple images are available for a single street or intersection, multiple predictions are generated. We must develop a method to effectively combine these predictions. Moreover, addressing disagreements between predictions for the same intersection from different panoramas is crucial. By developing mechanisms to reconcile conflicting predictions and leveraging the strengths of multiple images, we can improve the accuracy and robustness of our object detection models. -->

## Conclusions
In conclusion, several key takeaways have emerged from our analysis of the Project Sidewalk data for our object detection task:

* **Importance of Clean Training Data:** The easiest way to improve the performance of our object detection models is to have good, clean training data. Addressing the challenges of missing labels, inaccurate bounding boxes, incorrect labels, and confusion in driveway classification will be essential to enhance the data's quality and reliability.

* **Clarifying Driveway Classification:** We must decide on a clear and consistent approach for classifying driveways as either curb ramps or missing curb ramps. Providing explicit guidelines to contributors and refining the labeling process can help ensure accurate and unambiguous driveway classification.

* **Adapting Project Sidewalk Data:** Converting the Project Sidewalk data to suit our specific object detection task requires careful consideration. Several approaches can be explored, including manual data labeling, using the existing sidewalk data to train a preliminary model, and leveraging the predictions of the preliminary model to validate further training data. Additionally, creating dedicated validation software for object detection can streamline the data adaptation process and improve the efficiency of model training.



