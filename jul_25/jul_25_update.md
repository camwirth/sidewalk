# July 25 Update 

## DivideMix

DivideMix is built around Image Classification rather than Object Detection. Because of this, I ran into some difficulty implementing DivideMix with our dataset. I did however try some tests using the algorithm and provided code to fit generated crops of "noisy" labels using a binary classification. The procedure and results for these tests are explained below.

1. Produce noisy dataset for DivideMix
    - Generate crops from all given labels and label them as 1 (Curb Ramp)
    - Generate crops from all predicted labels using the Curb-Ramp model previously trained
        - labels with a confidence score greater than 40% were labeled as 1 (Curb Ramp)
        - labels with a confidence score greater than 25% but less than 40% were labeled as 0 (not Curb Ramp)
2. Alter DivideMix code to work with dataset
3. Run the DivideMix training for 50 epochs 
4. Evaluate Results

DivideMix was not created with Binary Classification in mind. 
- Label Imbalance
- Entropy-based splitting 
- pseudo-labeling splitting

DivideMix also introduces many more hyperparameters which must be finetuned to the dataset making the problem more complicated 
Along with larger complexity it must be trained. The use of two models in DivideMix doubles the training time 

After testing and working with DivideMix I don't believe that the algorithm will work well with our dataset. Not only does the algorithm work only with Image Classification, but it also 

## Self-Supervised training approach

The major problem in our data is lack of labeling (especially in the test set) This leads to inaccurate results. I looked into a self-supervised training approach where the result data from the model is used as further training data. 

1. Create a reliable test set. 
    - using the results from my Curb Ramp model, I examined the bounding boxes for all predictions that had a confidence level of 0.25 or above. 

2. Run the self-supervised training


Resources:

Self-supervised
https://arxiv.org/pdf/2102.11614.pdf

https://arxiv.org/abs/1705.07115


