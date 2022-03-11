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
    sh tools/dist_train.sh 1 configs/strategies/DyRep/cifar.yaml nas_model --model-config configs/models/VGG/vgg16_cifar100.yaml --dyrep --dataset cifar100 --experiment dyrep_cifar100_vgg16
    ```

### ImageNet  
* ResNets  
    ```
    sh tools/dist_train.sh 8 configs/strategies/DyRep/resnet.yaml resnet50 --dyrep --experiment dyrep_imagenet_res50
    ```

* MobileNetV1
    ```
    sh tools/dist_train.sh 8 configs/strategies/DyRep/mbv1.yaml mobilenet_v1 --dyrep --experiment dyrep_imagenet_mbv1
    ```

* RepVGG
    * DyRep-A2
        ```
        sh tools/dist_train.sh 8 configs/strategies/DyRep/repvgg_baseline.yaml timm_repvgg_a2 --dyrep --dyrep_recal_bn_every_epoch --experiment dyrep_imagenet_repvgg_a2
        ```
    * DyRep-B2g4 and DyRep-B3
        ```
        sh tools/dist_train.sh 8 configs/strategies/DyRep/repvgg_strong.yaml timm_repvgg_b2g4 --dyrep --dyrep_recal_bn_every_epoch --experiment dyrep_imagenet_repvgg_b2g4
        ```

## Deploying the Trained DyRep Models to Inference Models  
```
sh tools/dist_convert.sh 8 ${CONFIG} ${MODEL} --resume ${CHECKPOINT}
```

For example, if you want to deploy the trained ResNet-50 model with the best checkpoint, run  
```
sh tools/dist_convert.sh 8 configs/strategies/DyRep/resnet.yaml resnet50 --dyrep --resume experiments/dyrep_imagenet_res50/best.pth.tar
```

Then it will run test before and after deployment to ensure the accuracy will not drop.

The final weights of the inference model will be saved in `experiments/dyrep_imagenet_res50/convert/model.ckpt`.

## Results  

## Citation  
The paper will be released soon.
