# FCN8_VGG16Backbone
Image segmentation on a subset of CamVid dataset using VGG-16 Feature Extractor followed by FCN-8 decoder

## Dataset
The dataset images and annotations. The images contain the video frames while the annotations contain the pixel-wise label maps. Each label map has the shape (height, width , 1) with each point in this space denoting the corresponding pixel's class. Classes are in the range [0, 11] (i.e. 12 classes) and the pixel labels correspond to these classes:
| Value  | Class Name    |
| -------| -------------| 
| 0      | sky |
| 1      | building      |
| 2      | column/pole      |
| 3      | road |
| 4      | side walk     |
| 5      | vegetation      |
| 6      | traffic light |
| 7      | fence      |
| 8      | vehicle     |
| 9      | pedestrian |
| 10      | byciclist      |
| 11      | void      |
## Model
### VGG-16 Network
The backbone used is VGG-16, without the fully connected layers, initialized with pretrained weights. The architecture of a VGG-16 network is as follows:
<br>
<img src='https://iq.opengenus.org/content/images/2019/01/vgg_layers.png' alt='vgg-16'>

### FCN-8
FCN-8 is a fully convolutional network which upsamples the feature extracted by encoder and creates a pixel-wise labelmap
<img src='https://drive.google.com/uc?export=view&id=1lrqB4YegV8jXWNfyYAaeuFlwXIc54aRP' alt='fcn-8'>

## Metrics
Metrics used are IoU and Dice Score.
<br>
![](https://latex.codecogs.com/svg.image?%5Cbg%7Bwhite%7DIoU%20=%20%5Cfrac%7Barea%5C_of%5C_overlap%7D%7Barea%5C_of%5C_union%7D)
<br>
![](https://latex.codecogs.com/svg.image?\inline&space;Dice&space;Score&space;=&space;\frac{area\_of\_overlap}{combined\_area})
<br>
A smoothing factor can be added in both numerator and denominator to avoid 0 division
