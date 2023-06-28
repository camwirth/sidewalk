# June 28 Personal Meeting 

## YOLO-NAS

### Training on Missing Curb-Ramp dataset

I used the same dataset that Supriyo used in training his model. 

| Training Images | Training labels | Test/Val Images | Test/Val labels |
|-----------------|-----------------|-----------------|-----------------|
| 3352            | 6452            | 932             | 1747            |

### Results

| Precision | Recall | mAP@0.50 | Epoch |
|-----------|--------|----------|-------|
| 0.3914    | 0.7344 | 0.4133   | 50    |


| Precision | Recall | mAP@0.50 |
|-----------|--------|----------|
| ![YOLO-NAS Missing Ramp Precision](/jun_28/precision.png) | ![YOLO-NAS Missing Ramp Recall](/jun_28/recall.png) | ![YOLO-NAS Missing Ramp mAP@0.50](/jun_28/map.png) |

Training Loss

![YOLO-NAS Missing Curb Train Loss](/jun_28/train_loss.png)

Validation Loss

![YOLO-NAS Missing Curb Valid Loss](/jun_28/valid_loss.png)

I first ran the training for 150 epochs, but certain settings made the training hit a peak after 17 epochs and then steadily decrease in performance. I changed some settings and re-ran the training for 50 epochs to get the results that are shown on this page

This is the ouptut of the training results at every epoch. 

![YOLO-NAS Results](/jun_28/results.png)
