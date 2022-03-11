# DyRep: Bootstrapping Training with Dynamic Re-parameterization 
Official implementation for paper "DyRep: Bootstrapping Training with Dynamic Re-parameterization", CVPR 2022.

By Tao Huang, Shan You, Bohan Zhang, Yuxuan Du, Fei Wang, Chen Qian, Chang Xu.

## Updates  

### March 11, 2022  
The code is available at [image_classification_sota](https://github.com/hunto/image_classification_sota).

## Getting started  
### Clone training code  
```
git clone https://github.com/hunto/image_classification_sota
```

The prepare your environment and datasets following the `README.md` in `image_classification_sota`.

### Implementation of DyRep  
The core concept of DyRep is in `lib/models/utils/dyrep.py`.

## Reproducing our results  
### CIFAR  
* CIFAR-10
    ```
    sh tools/dist_train.sh 1 configs/strategies/DyRep/cifar.yaml nas_model --model-config configs/models/VGG/vgg16_cifar10.yaml --dyrep --experiment dyrep_cifar10_vgg16
    ```
* CIFAR-100
    ```
    sh tools/dist_train.sh 1 configs/strategies/DyRep/cifar.yaml nas_model --model-config configs/models/VGG/vgg16_cifar10.yaml --dyrep --experiment dyrep_cifar10_vgg16
    ```