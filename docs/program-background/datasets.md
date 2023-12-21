# Datasets

## Background

Within FY23, the JATIC Program is focused on developing AI T&E capability for CV Classification and Object Detection. In order to provide targets for the main uses cases on which our tools should apply, we've identified four mission use cases and corresponding datasets to focus on:

1. Satellite Imagery - CV Object Detection
1. Medical Imaging - CV Classification
1. UAV - CV Object Detection
1. Autonomous Driving - CV Object Detection

These should not preclude application to other tasks, but serve as use cases to keep in mind during development. 

For most of the above use cases, we are working with DoD partners to apply our tools into T&E workflows for these mission types. For each of the above use cases, we select an open-source dataset which "represents" the mission to serve as our working target. These selected datasets should be used in any realisitic demonstrations.

Below, we provide further info on the chose open-source datasets.

## Selected datasets

### Satellite imagery

### Medical Imaging

### UAV
The VisDrone dataset (Zhu et al., '20) was collected by the [AISKYEYE team](http://aiskyeye.com/home/) from Tianjin University, China. The dataset contains 288 video clips with 261,908 frames and 10,209 static images, captured by various drone-mounted cameras. These frames have been manually annotated with more than 2.6 million bounding boxes of targets of interest. Scenes vary in location (14 different cities in China), environment (urban and country), objects (pedestrians, vehicles, bicycles, etc.), and density (sparse and crowded scenes). Challenges with the dataset include: 1) long-tailed distributions, 2) small objects, 3) visually similar classes, and 4) wide scale range of objects. The dataset can be used for five different tasks, although we focus primarily on object detection in images:

**Task 1**. Object detection in images  
**Task 2**. Object detection in videos  
**Task 3**. Single-object tracking  
**Task 4**. Multi-object tracking  
**Task 5**. Crowd counting

[Paper](https://arxiv.org/abs/1804.07437)  
[Dataset](https://github.com/VisDrone/VisDrone-Dataset)

### Autonomous driving
