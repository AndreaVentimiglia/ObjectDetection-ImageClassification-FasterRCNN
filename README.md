# ObjectDetection-ImageClassification-FasterRCNN
Training a deep learning model (Faster R-CNN) to perform image classification on a dataset characterized by a domain shift between training and test data. The network is trained to distinguish different types of objects by inserting a set of training images. Once the network has been trained, it will be possible to use a set of test images so that the network is able to recognize, with a certain degree of accuracy, which object the test image represents.

## Dataset
During training, the model expects both the input tensors and a targets (list of dictionary), containing:
- boxes (FloatTensor[N, 4]): the ground-truth boxes in [x1, y1, x2, y2] format, with 0 <= x1 < x2 <= W and 0 <= y1 < y2 <= H;
- labels (Int64Tensor[N]): the class label for each ground-truth box.

So, we implement from scratch ObjectDataset class – where target is a dictionary {'boxes’ : boxes, 'labels’ :labels}.
![image](https://github.com/AndreaVentimiglia/ObjectDetection-ImageClassification-FasterRCNN/assets/63006903/ab4d8cec-a0a7-4bc8-98e8-620fd454d01a)

![image](https://github.com/AndreaVentimiglia/ObjectDetection-ImageClassification-FasterRCNN/assets/63006903/cbd3ad4a-da75-4700-b599-5cbd998d2456)


## Training
During training the model tries to achieve the objects in the images correctly thanks to the ObjectDataset which helps it to focus the learning in the indicated regions.
![image](https://github.com/AndreaVentimiglia/ObjectDetection-ImageClassification-FasterRCNN/assets/63006903/d235a938-3b2e-41d1-a616-ff5bad4d7074)

To train the model we used:
The SGD optimizer with learning rate of 0.01
Dataset that was split into batches of size 16
20 epochs![image](https://github.com/AndreaVentimiglia/ObjectDetection-ImageClassification-FasterRCNN/assets/63006903/ba727452-8b89-4dbf-87ae-3460302b66ad)
