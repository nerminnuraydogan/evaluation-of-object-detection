# Evaluation of Object Detection

The presented notebook consists of implementation of Average Precision and Average Recall for object detection.

>### Average Precision

The implementation of Average Precision is mainly based on the 11-point Interpolated Average Precision that is proposed in the book ['Introduction to Information Retrieval'](https://nlp.stanford.edu/IR-book/html/htmledition/evaluation-of-ranked-retrieval-results-1.html).

The implementation of the Average Precision in this notebook is adapted from the 101 Point Interpolation AP evaluation metric that is introduced by MS COCO in 2014.

- AP is calculated at 101 points rather than 11 points, on ranging recall values from 0 to 1 at a step of 0.01
- AP is calculated for a set of 10 different IoU thresholds and then averaged. The IoU threshold ranges from 0.5 to 0.95 at a step frequency of 0.05

For step-by-step tutorial, check out [this blog post](https://learnopencv.com/mean-average-precision-map-object-detection-model-evaluation-metric/).

<img src='https://learnopencv.com/wp-content/uploads/2022/08/mean-average-precision-map-how-to-interpolate-11-points-precision.jpg' width=50% height=50% />

>### Average Recall

The implementation of Average Recall is mainly adapted from the paper ['What makes for effective detection proposals?'](https://arxiv.org/pdf/1502.05082.pdf).

- AR is calculated as 2 times area under the recall-iou curve
- Recall is calculated for 5 different IoU thresholds starting from 0.5 to 1 at a step frequency of 0.1

---

Some of the considerations for the evaluation is explained below:

- Unmatched detecting bounding boxes are considered FP
- Matched detecting bounding boxes with IoU overlap greater than or equal to IoU threshold are considered TP
- Precision is calculated as TP / (TP + FP)
- TP + FP is calculated as the number of predicted bounding boxes
- Recall is calculated as TP / (TP + FN)
- TP + FN is considered as the total number of ground truth bounding boxes for dataset
- Detected bounding boxes with confidence score less than score threshold are not included in the evaluation
- **The implementation considers only bounding boxes for evaluation and omits classification**

