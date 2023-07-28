
# Bounding Box Estimation

For our object detection tasks, we have been using the crowdsourced data provided by Project Sidewalk. The project sidewalk data pinpoints the 'center' of the objects in the image. However, to utilize object detection models effectively, a general bounding box surrounding the object is required, indicating that the object falls within the confines of the bounding box. This report explores the process of estimating bounding boxes for objects in panorama images and delves into the challenges faced due to the distortion of objects at different locations within the panorama.

## Challenges in Bounding Box Estimation

The primary challenge in estimating bounding boxes for panorama-based object detection arises from the nature of panorama images themselves. As objects are captured from varying perspectives across the panorama, they are distorted and appear in different sizes, depending on their location within the image. This distortion makes it difficult to establish a uniform approach for bounding box estimation.

Another obstacle lies in the fact that the 'center' coordinates provided by the project sidewalk data may not always align perfectly with the actual center of the object. This misalignment poses a considerable challenge, as it hinders the accurate inclusion of the entire object within the bounding box.

To tackle these challenges, each member of our team has adopted different methods for estimating the bounding box of objects in panorama images. While the specific techniques may vary, the underlying goal remains constant: to create bounding boxes that encompass the objects with precision and accuracy. The different methods we have used are explained below.

## Use Crop Code from Project Sidewalk to Generate Bounding Box
Anny and Gavin have adopted a method that leverages the [predict_crop_size]() code provided by Project Sidewalk, which takes the y-coordinate and height of the panorama image as input and returns the size of the bounding box. The bounding box is generated based on the original panorama size, and any resizing applied to the image for object detection also scales the bounding box accordingly.

This approach offers several advantages, providing a reasonably accurate general bounding box for the detected objects. However, it does have some limitations. One notable drawback is that the bounding box often fails to encompass the entire object. Especially when dealing with off-centered center points, the resulting bounding box may only cover a small portion of the actual object, leading to incomplete representations.

Moreover, the method generates square bounding boxes, which may not be optimal for detecting objects like Curb Ramps and Missing Curb Ramps, which tend to exhibit a more rectangular shape. This mismatch between the object's actual shape and the square bounding box can affect the precision and accuracy of the object detection algorithm.

To illustrate the performance of this method, visual examples of both high-quality and low-quality bounding boxes are presented below. These examples highlight the varying degrees of accuracy achieved by the bounding box estimation approach

<!-- PROVIDE EXAMPLES  -->

## Use Crop Code from Project Sidewalk after Image Scaling


Camille and Supriyo have adopted a similar method for generating bounding boxes using the [predict_crop_size](https://github.com/ProjectSidewalk/sidewalk-panorama-tools/blob/d4cbe8dad16d51b922726e9d355a6881c281e50e/CropRunner.py#L133-L150) code provided by Project Sidewalk. However, they have introduced a key modification in their approach. In this method, the panorama image is first scaled to a fixed size of 1280x1280 pixels. The new scaled y-value and height of the object are then utilized as inputs to the function, instead of relying on the pre-scaled values. Consequently, the bounding boxes generated through this method are notably larger compared to the previous version.

The utilization of such large bounding boxes offers several advantages. Most notably, it ensures that the entire object is encompassed within the bounding box, eliminating the issue of incomplete representations faced in the previous method. This enhancement contributes to more accurate object detection, especially for objects like Curb Ramps and Missing Curb Ramps that require complete coverage.

However, the considerable increase in bounding box size also presents some challenges. Due to their large dimensions, each bounding box may contain multiple objects or overlap significantly with adjacent bounding boxes. As a result, identifying the specific object within a bounding box can become confusing and potentially hinder the accuracy of object recognition.

To provide a comprehensive overview of the method's performance, visual examples of both high-quality and low-quality bounding boxes are presented below. These examples demonstrate the varying outcomes of the bounding box generation process and highlight the implications of using larger bounding boxes.


<!-- PROVIDE EXAMPLES  -->

## Use the canvas_width and canvas_height information on the metadata for each label

Braxton has adopted a final approach that utilizes the canvas_width and canvas_height data provided in the metadata for each label file. In this method, the specified width and height in the metadata are applied to the pre-scaled panorama image. Any subsequent resizing of the image for training purposes further scales the bounding box accordingly. This approach aims to generate bounding boxes that are more appropriate for the object's aspect ratio, as opposed to the square bounding boxes used in previous methods.

One notable advantage of this approach is that it typically produces non-square bounding boxes, which better fit the aspect ratio of the detected objects. This aspect-ratio-aware bounding box contributes to more accurate and visually representative object detection results.

However, there are some limitations to consider. The bounding boxes generated using this method tend to be relatively small. Particularly, when dealing with off-centered images, these small bounding boxes may encompass only a limited portion of the actual object, resulting in incomplete representations.

To illustrate the performance of this approach, visual examples of both high-quality and low-quality bounding boxes are presented below. These examples showcase the varying outcomes of the bounding box generation process, highlighting the challenges posed by small bounding boxes, especially in cases of off-centered images.

<!-- PROVIDE EXAMPLES  -->

## Conclusions

It is evident that each method used in generating bounding boxes for object detection in panorama images has its advantages and challenges. While some methods may provide reasonably accurate bounding boxes, they may fail to encompass the entire object or result in square bounding boxes that do not fit the objects' aspect ratio. On the other hand, other methods may generate larger bounding boxes to include the entire object but could lead to confusion when multiple objects are enclosed within a single box.

The diverse approaches we have adoped demonstrate a thorough exploration of potential solutions to mitigate the issues associated with inaccurate bounding boxes. By evaluating these different methods, we can gain insights to the strengths and limitations of each approach.

As the project progresses, it will be essential to further analyze the performance of these methods rigorously. Comparing the models based on their accuracy, precision, recall, and other relevant metrics will help identify the best approach for generating bounding boxes in panorama-based object detection. The evaluation should consider both the visual representation of bounding boxes and the object detection model's overall performance.