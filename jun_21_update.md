# June 21 NSF Convergence Update

## Training Results


I have trained both the Surface Problem and Curb Ramp alone using the YOLOX-m model. The table below records the training time and the quantity of train/test input data. 

| Object          | Training Time | Train Images | Train Bounding Boxes | Test Images | Test Bounding Boxes |
|-----------------|---------------|--------------|----------------------|-------------|---------------------|
| Curb Ramp       | 6 hours       | 1,156        | 1,626                | 265         | 371                 |
| Surface Problem | 24 hours      | 5,352        | 7,070                | 1,390       | 1,855               |

### Evaluation Results

The mAP and mAR of the best model saved during the training process are shown in the table below. 

|Object           | mean Average Precision | mean Average Recall |
|-----------------|------------------------|---------------------|
| Curb Ramp       | 31.653                 | 39.773              |
| Surface Problem | 8.403                  | 21.962              |

The folowing are screenshots of the results after running the evaluation program using the best model saved in the training process. These results are measured with a given confidence threshold of 0.25.

| Curb Ramp                                                     | Surface Problem                                                     |
|---------------------------------------------------------------|---------------------------------------------------------------------|
| ![Curb Ramp Results](/jun_21_eval_results/curb_ramp_eval.png) | ![Surface Problem Results](/jun_21_eval_results/surface_problem_eval.png) |


These images plot the total loss and the average precision throughout the training at each epoch. This evaluation uses the default confidence threshold parameter of 0.1 to calculate the mAP@0.5

| Object          | Total Loss                                                              | mAP@0.5                                                                     |
|-----------------|-------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Curb Ramp       | ![Curb Ramp Total Loss](/jun_21_plots/total_loss_coco.jpg)              | ![Curb Ramp MAP@0.5](/jun_21_plots/average_precision_coco.jpg)              |
| Surface Problem | ![Surface Problem Total Loss](/jun_21_plots/total_loss_coco_sf_640.jpg) | ![Surface Problem MAP@0.5](/jun_21_plots/average_precision_coco_sf_640.jpg) |




## Image Examples
After testing the model on the trained model, I found some examples of the model output compared with the ground truth. In many cases, the model properly detects curb ramps. The input data is not perfect as can be seen in these examples. I believe that is affecting the results of the model the most. 

| Pano ID                | Curb Ground Truth                                                                   | Curb Ramp Output                                                        |
|------------------------|-------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| N2oWxkP_2T2B85pDtg6Y2g | ![N2oW Ground Truth](/jun_21_img/curb_ramp/ground_truth/N2oWxkP_2T2B85pDtg6Y2g.jpg) | ![N2oW Output](/jun_21_img/curb_ramp/output/N2oWxkP_2T2B85pDtg6Y2g.jpg) |
| TvLEfMjoTzEBcdjSIBBqlg | ![TvLe Ground Truth](/jun_21_img/curb_ramp/ground_truth/TvLEfMjoTzEBcdjSIBBqlg.jpg) | ![TvLe Output](/jun_21_img/curb_ramp/output/TvLEfMjoTzEBcdjSIBBqlg.jpg) |
| 2xgwttEdq2xtqbe93VweTw | ![2xgw Ground Truth](/jun_21_img/curb_ramp/ground_truth/2xgwttEdq2xtqbe93VweTw.jpg) | ![2xgw Output](/jun_21_img/curb_ramp/output/2xgwttEdq2xtqbe93VweTw.jpg) |



| Pano ID                | Surface Problem Ground Truth                                                              | Surface Problem Output                                                        |
|------------------------|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| -PTEVxc8LDlAwvw0a-gy7Q | ![-PTE Ground Truth](/jun_21_img/surface_problem/ground_truth/-PTEVxc8LDlAwvw0a-gy7Q.jpg) | ![-PTE Output](/jun_21_img/surface_problem/output/-PTEVxc8LDlAwvw0a-gy7Q.jpg) |
| 06dlc7TBXKu475EJNqK_zA | ![06dl Ground Truth](/jun_21_img/surface_problem/ground_truth/06dlc7TBXKu475EJNqK_zA.jpg) | ![06dl Output](/jun_21_img/surface_problem/output/06dlc7TBXKu475EJNqK_zA.jpg) |
| -DUyiIN28nK_3TnJKWpLwg | ![-DUy Ground Truth](/jun_21_img/surface_problem/ground_truth/-DUyiIN28nK_3TnJKWpLwg.jpg) | ![-DUy Output](/jun_21_img/surface_problem/output/-DUyiIN28nK_3TnJKWpLwg.jpg) |


<!-- | Pano ID | Missing Curb Ramp Ground Truth | Missing Curb Ramp Output|
|---------|--------------------------------|-------------------------| -->


## Improvements to try on YOLOX-m

After reading different papers there are a few improvements that I would like to try on my model. I will try these improvements changing one thing at a time. 
First starting with Curb Ramp to discover if training result if different. Most improvements that I have read about only improve the output of the model by 2-3%. 

- Implement DecIoU loss function with YOLOX
    - approximately 2.6% increase in performance
    - source: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10105761
- Article on creating a T-YOLOX to better detect fire
    - approximately 2.24% increase in performance
    - source: https://www.hindawi.com/journals/wcmc/2022/9666265/
- Try changing backbone to CSP-Darknet53
    - source: https://www.mdpi.com/2227-7390/10/15/2650


# Moving Forward

I am hoping to have trained the model using the missing curb ramp dataset by the end of the week. By next week, I hope to implement one change and evaluate the results of training the model with one of the improvements mentioned above. 

I have also read about different models and I am curious to explore the YOLO-NAS model. It was released in May of this year and is said to have performance comparable to YOLOv5 and v8. 

<!-- ## Trained data using YOLO-NAS

### Training Settings using YOLO-NAS

### Evaluation Results for Curb Ramp -->


