# July 11 Update


## Observations on Training Data

After going through images of the ground truth labels on the training data, I have noticed a few problems with the data. 

1. Inaccurate Labeling

![](/jul_11/images/examples/1j1MTLjaGwlSFr2RjnGcTw.jpg)

![](/jul_11/images/examples/6H2KpDa0Gboi0XudOD-a4Q.jpg)

2. Bounding boxes are too large - contain more than one object in a single bounding box

![](/jul_11/images/examples/_0K_L3M_OR-IbXZmFhjnKw.jpg)

![](/jul_11/images/examples/1QEkjYFjMfSxADowiEUcqw.jpg)

![](/jul_11/images/examples/1VH6rGLPKXvSVs8nbIXtng.jpg)

3. Lack of labeling ALL objects

![](/jul_11/images/examples/1-TDKHxOg03ctPUdatwpiw.jpg)

![](/jul_11/images/examples/2DSyVoKzjM8AyDjn_QSFiA.jpg)

4. Too many annotations for a single object - confusing data

![](/jul_11/images/examples/_64uLj04uXCbTz3XliN-Lg.jpg)


5. Unclear what object actually is

![](/jul_11/images/examples/3Edc2psr5ZSqKcUb-wavLw.jpg)

6. Curb Ramps include driveways, this makes the data more confusing. Are we trying to detect driveways along with curb ramps? 

![](/jul_11/images/examples/1CqUBKMM8nTvzNc6CiS4OA.jpg)

![](/jul_11/images/examples/1rDmu7cR1Nd8PdNMrHLJhw.jpg)

![](/jul_11/images/examples/2Dm9IkK0CmAk32WUwV9Uzw.jpg)

7. other objects obstruct view of the object

![](/jul_11/images/examples/0u3i98En30QZU9SCkc1tPA.jpg)

![](/jul_11/images/examples/2hP9T94nA5NkM_P9wYYQAQ.jpg)

## Visualizing Testing

I went through the testing data and selected 6 different sets of images

| Sets                                   |
|----------------------------------------|
| Good Curb Ramps                        |
| Bad Curb Ramps                         |
| Good Missing Curb Ramps                |
| Bad Missing Curb Ramps                 |
| Good Curb Ramps and Missing Curb Ramps |
| Bad Curb Ramps and Missign Curb Ramps  |


Each of these sets of images along with notes on why they were chosen in the set can be found here 

I tested these sets on 3 different models:

| Models                          |
|---------------------------------|
| Curb Ramp Only                  |
| Missing Curb Ramp Only          |
| Curb Ramp and Missing Curb Ramp |


### Curb Ramp Only Model 

**Good Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/2xgwttEdq2xtqbe93VweTw.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/2xgwttEdq2xtqbe93VweTw.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/DN_D0ZzDYDvr1t2sUfMQpQ.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/DN_D0ZzDYDvr1t2sUfMQpQ.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/GkCEcsZ5yQx6bVvDJ05QNg.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/GkCEcsZ5yQx6bVvDJ05QNg.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/IhjJ9BHIcEBjUF5U_ZKNzA.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/IhjJ9BHIcEBjUF5U_ZKNzA.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/Os8sNJzOnIjLDr6qERterw.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/Os8sNJzOnIjLDr6qERterw.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/t09X7en_-fpdxS2uJa-X1Q.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/t09X7en_-fpdxS2uJa-X1Q.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/T0FZdWTmyKZQvpXGGLRNwA.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/T0FZdWTmyKZQvpXGGLRNwA.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/tQYcQbZbzm2hh2GAX_kt0w.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/tQYcQbZbzm2hh2GAX_kt0w.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/U_dcYzS-OI6XaVrDreD6Ww.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/U_dcYzS-OI6XaVrDreD6Ww.jpg) | 
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/gt/WaJz9uhTx5yAMLogGbU0tA.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_good/pred/WaJz9uhTx5yAMLogGbU0tA.jpg) |

| Precision | Recall | mAP@0.5 |
|-----------|--------|---------|
| 0.2653    | 0.4333 | 0.4082  |

**Bad Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/hgc6apPdGlUZXZRdvAQ1PQ.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/hgc6apPdGlUZXZRdvAQ1PQ.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/l-m0dscGN-E3kcGFLNNh5Q.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/l-m0dscGN-E3kcGFLNNh5Q.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/MGA7FbhAQDCGNbYdlzEX7Q.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/MGA7FbhAQDCGNbYdlzEX7Q.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/ofZ646HA4HsIUZ-y151Ulg.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/ofZ646HA4HsIUZ-y151Ulg.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/pjUmTXVER87Nnl5GsT0lRQ.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/pjUmTXVER87Nnl5GsT0lRQ.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/PwRfPZfEIlBhwH9Pccj8Rg.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/PwRfPZfEIlBhwH9Pccj8Rg.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/pWXNFcJ6p892U42DpNInIw.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/pWXNFcJ6p892U42DpNInIw.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/rayfRMi7daH5adHoNz4H4A.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/rayfRMi7daH5adHoNz4H4A.jpg) | 
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/rzaoXBZUKrnYyqdq6SWskQ.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/rzaoXBZUKrnYyqdq6SWskQ.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/SMzV08dieVqN0ca6EsvgFg.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/SMzV08dieVqN0ca6EsvgFg.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/sRaNg3oSc29X-vRYI6CezA.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/sRaNg3oSc29X-vRYI6CezA.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/STp5_jCM8VHyY_KMIUIZ8g.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/STp5_jCM8VHyY_KMIUIZ8g.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/t54GYH89ZEwQzhR6X2j8Yg.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/t54GYH89ZEwQzhR6X2j8Yg.jpg) |
| ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/gt/TvLEfMjoTzEBcdjSIBBqlg.jpg) | ![](/jul_11/images/curb_ramp_exp/curb_ramp_bad/pred/TvLEfMjoTzEBcdjSIBBqlg.jpg) |


| Precision | Recall | mAP@0.5 |
|-----------|--------|---------|
| 0.0816    | 0.2105 | 0.09173 |

The "good" data for Curb Ramp had significantly better performance compared to the "bad" data. Although the good data performance is similar to the ovearall performance of this model on the entire test set. 


<!-- **Good Curb Ramps and Mising Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|

| Precision  | Recall | mAP@0.5   |
|------------|--------|-----------|
| 0.2682927  | 1.0    | 0.7306112 |

**Bad Curb Ramps and Missing Curb Ramps SetSet**

| Ground Truth | Prediction |
|--------------|------------|

| Precision | Recall | mAP@0.5 |
|-----------|--------|---------|
| 0.2093    | 0.75   | 0.5745  | -->


### Missing Curb Ramp Only Model 

**Good Missing Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/0z5JHo1wG5blvgE6JkMlQg.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/0z5JHo1wG5blvgE6JkMlQg.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/1f8ENWBKnGQPd3YFYCxG3A.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/1f8ENWBKnGQPd3YFYCxG3A.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/1UlqKyA-Af6KEIlDG-iJVA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/1UlqKyA-Af6KEIlDG-iJVA.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/5PZdl-VkLWhXBKaxXL0nVA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/5PZdl-VkLWhXBKaxXL0nVA.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/5zJDWf92tSfWimkaF7dG6Q.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/5zJDWf92tSfWimkaF7dG6Q.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/6EpZo7SFgedjCkrykNLZjg.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/6EpZo7SFgedjCkrykNLZjg.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/6u6paZ2nZ4HhTtVHW2KkuQ.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/6u6paZ2nZ4HhTtVHW2KkuQ.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/7sEDcEDSXEvQJVfbPoKrtg.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/7sEDcEDSXEvQJVfbPoKrtg.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/8j9t1-2sS2w0JPIWdXBojQ.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/8j9t1-2sS2w0JPIWdXBojQ.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/937NunwvqZYj238qODhmeg.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/937NunwvqZYj238qODhmeg.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/bmSClOa75RSp1Tt435TdUA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/bmSClOa75RSp1Tt435TdUA.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/Eu3nvL0-99Y2uKWnfr7HUw.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/Eu3nvL0-99Y2uKWnfr7HUw.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/gt/Gn_moi_faa5L69wKyq2IUQ.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_good/pred/Gn_moi_faa5L69wKyq2IUQ.jpg) |


| Precision | Recall | mAP@0.5 |
|-----------|--------|---------|
| 0.3333    | 0.8965 | 0.5982  |

**Bad Missing Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/1Fv6Xd3o1K1OuqyqU36vUw.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/1Fv6Xd3o1K1OuqyqU36vUw.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/1msQvM1iFLS4VJk-bGlTYw.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/1msQvM1iFLS4VJk-bGlTYw.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/1mUyLqcASxqOnknEZMUkww.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/1mUyLqcASxqOnknEZMUkww.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/a3TPcy7s3hdWPxAhd-emqw.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/a3TPcy7s3hdWPxAhd-emqw.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/cLiLAvKlwQm-Ek0Tza5lJg.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/cLiLAvKlwQm-Ek0Tza5lJg.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/d-4MlTZca5ficmc50gOrLA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/d-4MlTZca5ficmc50gOrLA.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/D00VCbqovq5HCuuh-wxioA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/D00VCbqovq5HCuuh-wxioA.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/F9ctqTYCzCF7zVeXIhzItw.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/F9ctqTYCzCF7zVeXIhzItw.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/IjhL0vRYp79_eKEWJ1zufA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/IjhL0vRYp79_eKEWJ1zufA.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/jz59VWHXW4dhX8Gf5xsUng.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/jz59VWHXW4dhX8Gf5xsUng.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/k7NlJm6twINYnPfgNYoP0A.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/k7NlJm6twINYnPfgNYoP0A.jpg) |
| ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/gt/LhlOMcOFve6XhYmVbtn7dA.jpg) | ![](/jul_11/images/missing_curb_ramp_exp/missing_curb_ramp_bad/pred/LhlOMcOFve6XhYmVbtn7dA.jpg) |



| Precision  | Recall    | mAP@0.5    |
|------------|-----------|------------|
| 0.31428573 | 0.5116279 | 0.22819425 |

The output of the "good" data from the Missing Curb Ramp model has a better performance from the output of the model when tested on the entire test set. The performance is significantly greater than the performance of the "bad" data. 

<!-- **Good Curb Ramps and Mising Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|

| Precision  | Recall     | mAP@0.5    |
|------------|------------|------------|
| 0.13043478 | 0.64285713 | 0.24626675 |

**Bad Curb Ramps and Missing Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|

| Precision | Recall | mAP@0.5 |
|-----------|--------|---------|
| 0.2698    | 0.7391 | 0.5440  | -->


### Curb Ramp and Missing Curb Ramp Model 

**Good Curb Ramps Set**

<!-- | Ground Truth | Prediction |
|--------------|------------|

| Class     | Precision | Recall | mAP@0.5 |
|-----------|-----------|--------|---------|
| Curb Ramp | 0.2825    | 0.6833 | 0.4475  |

**Bad Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|

| Class     | Precision | Recall | mAP@0.5 |
|-----------|-----------|--------|---------|
| Curb Ramp | 0.16      | 0.2105 | 0.1238  |

**Good Missing Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|

| Class             | Precision | Recall | mAP@0.5 |
|-------------------|-----------|--------|---------|
| Missing Curb Ramp | 0.3291    | 0.8965 | 0.6312  | 

**Bad Missing Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|

| Class             | Precision | Recall     | mAP@0.5 |
|-------------------|-----------|------------|---------|
| Missing Curb Ramp | 0.3958    | 0.4634     | 0.2224  | -->
 

**Good Curb Ramps and Mising Curb Ramps Set**

| Ground Truth | Prediction |
|--------------|------------|
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/cq-CpV1HK8Jr7Z3Vv3GCjw.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/cq-CpV1HK8Jr7Z3Vv3GCjw.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/d-E6o_zIA-EfkjmpIPpkXA.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/d-E6o_zIA-EfkjmpIPpkXA.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/FyvPYcPs-fCjS4ZsHf4Z3w.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/FyvPYcPs-fCjS4ZsHf4Z3w.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/Im0pmxmBw1x62_hqSDtVGg.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/Im0pmxmBw1x62_hqSDtVGg.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/lNXJEsd7oh2JwR2EJmej-A.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/lNXJEsd7oh2JwR2EJmej-A.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/MIuJl50-N-d8VDHKTMvDGQ.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/MIuJl50-N-d8VDHKTMvDGQ.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/pNS0Zf4RQzuzMuaFbJqlGQ.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/pNS0Zf4RQzuzMuaFbJqlGQ.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/RcBWl03glK0AN1QnCUlufA.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/RcBWl03glK0AN1QnCUlufA.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/Rxk_ZENQVt2HyxKVk3K6Ow.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/Rxk_ZENQVt2HyxKVk3K6Ow.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/gt/T6GuLc7Ijh1kFbGPGCqd_A.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_good/pred/T6GuLc7Ijh1kFbGPGCqd_A.jpg) |


| Class              | Precision | Recall     | mAP@0.5    |
|--------------------|-----------|------------|------------|
| Curb Ramp          | 0.4783    | 1.0        | 0.8669     |
| Missing Curb Ramp  | 0.2143    | 0.6429     | 0.2723     |
| Total              | 0.3462733 | 0.82142854 | 0.56961113 |


**Bad Curb Ramps and Missing Curb Ramps SetSet**

| Ground Truth | Prediction |
|--------------|------------|
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/8EMgWqetgnB5je81KvM6iQ.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/8EMgWqetgnB5je81KvM6iQ.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/FD89SREoJ6ptzurGkRLLvQ.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/FD89SREoJ6ptzurGkRLLvQ.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/FmE52lBC2DDfRCilrGCfHw.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/FmE52lBC2DDfRCilrGCfHw.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/hjioPqzmikFshgTZwrDalw.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/hjioPqzmikFshgTZwrDalw.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/Ihindr9wFtfLcluquQnMkw.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/Ihindr9wFtfLcluquQnMkw.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/ILCYE223HNPg_lA-owXkOw.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/ILCYE223HNPg_lA-owXkOw.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/IwPvg2u_kFw_zZzR4I4OAQ.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/IwPvg2u_kFw_zZzR4I4OAQ.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/NHUDRUuaEBZfNREypd-0Ig.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/NHUDRUuaEBZfNREypd-0Ig.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/NRQQNTEJyWxe-rH81SVXdA.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/NRQQNTEJyWxe-rH81SVXdA.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/PUUJWP3yNLJhtK5qWBZk0w.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/PUUJWP3yNLJhtK5qWBZk0w.jpg) |
| ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/gt/QD06Ws1KiprZr0WP5WCCQA.jpg) | ![](/jul_11/images/missing_and_curb_exp/missing_and_curb_bad/pred/QD06Ws1KiprZr0WP5WCCQA.jpg) |


| Class             | Precision | Recall | mAP@0.5 |
|-------------------|-----------|--------|---------|
| Curb Ramp         | 0.3600    | 0.7500 | 0.5556  |
| Missing Curb Ramp | 0.3721    | 0.6957 | 0.5291  |
| Total             | 0.3660    | 0.7228 | 0.5424  |

The output of this test is interesting. With the "good" dataset, the performance for Curb Ramp is really high. However, the perfromance for Missing Curb Ramp is really low. The overall performance for both of these sets are comparable. 



## Observations and Conclusions

The data that we have is noisy and difficult to get good results from. Even manually labeling the objects is difficult as the objects are small in the panoramas and dificult to detect with the human eye. We need to look into ways to improving our models to detect the slight differences in the objects while using noisy data. Below are some ideas/articles that I have found that could potentially help improve the models. 
1. Removing images with the worst labels from both training and testing
2. Implement changes to model to adjust for inaccuracy in bounding boxes (some ideas are in these papers)
    - [Robust Object Detection With Inaccurate Bounding Boxes](https://www.ecva.net/papers/eccv_2022/papers_ECCV/papers/136700052.pdf)
    - [Combating noisy labels in object detection datasets](https://arxiv.org/abs/2211.13993)
    - [Noisy Annotation Refinement for Object Detection](https://www.bmvc2021-virtualconference.com/assets/papers/0778.pdf)
3. adjusting and comparing different bounding box generation methods
<!--4. Implementing different cropping methods to provide more data with higher resolution images (rather than resizing the images and altering the aspect ratio - crops are made from the images of higher resolution)-->
