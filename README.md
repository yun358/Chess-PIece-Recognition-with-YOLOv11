# Chess-PIece-Recognition-with-YOLOv11

We take a dataset of chess pieces images from https://www.kaggle.com/datasets/imtkaggleteam/chess-pieces-detection-image-dataset.

The dataset was fed through a YOLOv11 model instance, consisting of a YAML file with chess pieces' names and directory names to train, validation, test sets.
Also, a .csv file with columns: filename,	width,	height,	class,	xmin,	ymin,	xmax,	ymax
For example: 5c19d3260762f5daa632d952bc0074d6_jpg.rf.250c45a5fed7c606ee8fe28810a219a2.jpg,	416,	416,	white-bishop,	213,	197,	235,	253

"Oriented Bounding Boxes Object Detection (OBB)
Oriented object detection goes a step further than standard object detection by introducing an extra angle to locate objects more accurately in an image.
The output of an oriented object detector is a set of rotated bounding boxes that precisely enclose the objects in the image, along with class labels and confidence scores for each box. 
Oriented bounding boxes are particularly useful when objects appear at various angles, such as in aerial imagery, where traditional axis-aligned bounding boxes may include unnecessary background."
From https://docs.ultralytics.com/tasks/obb/

The dataset has the Standard Object Detection variant and Oriented Bounding Boxes variant, though we use the standard variant for now.
Hence traditional upright bounding boxes rather than oriented bounding boxes.

The model was trained on the dataset for 50 epochs, and batch size of 16.

_______________________________________________________________________________________________________________________________________________________________________________________________________________
Evaluation metrics:

Box(P):	Precision. The proportion of positive identifications (predicted pieces) that were actually correct. A high value means the model has a low rate of false positives (detecting something that isn't the piece).

R:	Recall. The proportion of actual positives (real pieces) that were correctly identified. A high value means the model has a low rate of false negatives (missing an actual piece).

mAP50:	mean Average Precision at an IoU threshold of 0.50. This is the average AP (Area Under the Precision-Recall Curve) across all classes, calculated using a IoU (Intersection over Union) threshold of 50% to determine if a detection is correct. It is a good indicator of how well the model localizes and classifies the objects.

mAP50-95:	mean Average Precision across IoU thresholds from 0.50 to 0.95. This is the average mAP calculated at IoU thresholds starting at 0.50 and increasing up to 0.95 (in steps of 0.05). This is a more stringent metric as it requires tighter bounding boxes to be considered a correct detection.
_______________________________________________________________________________________________________________________________________________________________________________________________________________

Overall, the model achieves an excellent performance, with overall precision at 0.967, recall at 0.983, average AUC PR of 0.98.
