# UrbanLF

This is the official repository of the UrbanLF dataset. For technical details, please refer to: UrbanLF: A New Light Field Dataset For Semantic Segmentation of Urban Scene.

## Dataset

UrbanLF is a high-quality and challenging urban scene light field dataset, containing real samples as well as synthetic samples.  The details are shown in table.

| Type         | Device      | Angle Resolution | Spatial Resolution | Element                                                      |
| ------------ | ----------- | ---------------- | ------------------ | ------------------------------------------------------------ |
| UrbanLF-Real | Lytro Illum | 9×9              | 623×432            | sub-aperture images, label annotations of central view.      |
| UrbanLF-Syn  | Blender     | 9×9              | 640×480            | sub-aperture images, label annotations of central view, depth and disparity information of central view. |

![1637998845990](images/fig1.png)

The effective value of depth does not exceed 100 meters and the depth value of sky that can not be measured is set to 200.

## Benchmark

Our benchmark is available at [here](http://112.74.92.70:8080/main/).

### Semantic Segmentation

#### Class Selection

There are 14 classes for evaluation and their definitions are shown in the table. 

| Name         | Label | RGB           | Definition                                                   |
| ------------ | ----- | ------------- | ------------------------------------------------------------ |
| bike         | 1     | [168,198,168] | <font size = 2>Bicycles, motorcycles, tricycles, and other transport without windows.</font> |
| building     | 2     | [198,0,0]     | <font size = 2>Skyscrapers, houses, bus stops, tents and other buildings, including billboards, glass, scaffolding, poles, and other objects attached to them with no more than 20% in pixels.</font> |
| fence        | 3     | [202,154,198] | <font size = 2>Fence with holes and plates or boards used for isolation, including objects can be seen through the holes of fence in real scene data.   </font> |
| others       | 4     | [0,0,0]       | <font size = 2>All objects that do not belong to the above classes, such as soil, sand, grass, stone, trash can, chair, thing with large diameters attached to pole.</font> |
| person       | 5     | [100,198,198] | <font size = 2>People who walk upright or stand still, including objects that are carried by people but not in contact with the ground. This class also include someone pushing a bike or standing next to it with both legs on the same side.</font> |
| pole         | 6     | [198,100,0]   | <font size = 2>Vertically oriented pole with horizontal part and brackets on it, such as sign pole and traffic light pole, including objects attached to the pole that do not belong to the traffic sign and the diameter at most twice of the pole in pixels.</font> |
| road         | 7     | [52,42,198]   | <font size = 2>The ground which is designed for vehicles drive on, including small objects and markings on it.</font> |
| sidewalk     | 8     | [154,52,192]  | <font size = 2>The ground which is designed for pedestrians, including the part with a height difference from the boundary of the road. Vehicles are not allowed to drive on it.</font> |
| traffic sign | 9     | [198,0,168]   | <font size = 2>Signs that provide traffic information for pedestrians and drivers, such as traffic signs, parking signs, direction signs, and traffic lights without their poles.</font> |
| vegetation   | 10    | [0,198,0]     | <font size = 2>Tree and shrub with a certain height from the ground, including objects can be seen through the thin gaps between leaves and trunk in real scene data.</font> |
| vehicle      | 11    | [198,186,90]  | <font size = 2>Cars, buses, trucks and other common large vehicles consist of 4 or more wheels and include all objects visible through the window.</font> |
| bridge       | 12    | [108,107,161] | <font size = 2>Bridge with a certain height from the ground.</font> |
| rider        | 13    | [156,200,26]  | <font size = 2>People who drive bikes, including objects that are carried by people but not in contact with the ground.</font> |
| sky          | 14    | [158,179,202] | <font size = 2>Open sky includes thin electrical wires in front of it.</font> |

#### Dataset Splitting

UrbanLF-Real consists of 580 training, 80 validation and 164 test samples and the number of UrbanLF-Sys is 172, 28 and 50 respectively. They can be used for RGB, video, light field semantic segmentation and UrbanLF-Sys can also be used for RGB-D semantic segmentation. Note 

**The metrics (mIoU, mAcc, Acc) are calculated only in full resolution of central view image.**

#### Data Link

Data is publicly available in Baiduyun (code: xjur) and Google.



### Super Resolution

#### Data generation

Our benchmark provides ×2 and ×4 light field spatial super resolution (LFSSR). The bicubic interpolation with a factor of 2 and 4 is applied to generate low resolution images of different scales. Due to the limitation of resolution, the real images are preprocessed before generating the test data. For ×2 task, we crop 1 pixel width on the right.  For ×4 task, we crop 2 pixel width on the right and 1 pixel width on the left. 

#### Dataset Splitting

UrbanLF-Real consists of 744 training, 80 validation and 80 test samples and the number of UrbanLF-Sys is 222, 28 and 30 respectively. 

**The metrics (PSNR, SSIM) are calculated by averaging over all sub-aperture images.  The spatial resolution of the prediction for real images should be 622×432 for ×2 task and 620×432 for ×4 task. **

#### Data Link

Data is publicly available in Baiduyun (code: xjur) and Google.



### Depth Estimation

#### Dataset Splitting

Only UrbanLF-Sys is used for depth estimation with disparity range [-0.47,1.55] pixels. We exclude samples that contain the sky. UrbanLF-Sys consists of 170 training, 30 validation and 30 test samples. 

**The metrics (MSE, BP) are calculated only on central view image with cropping 15 pixels at each border.**

#### Data Link

Data is publicly available in Baiduyun (code: xjur) and Google.



## Citation

If you find our work useful in your research, please consider citing:

```

```



## Statement