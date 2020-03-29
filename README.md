# Train CIFAR10 with PyTorch

I'm playing with [PyTorch](http://pytorch.org/) on the CIFAR10 dataset.

## Prerequisites
- Python 3.6+
- PyTorch 1.0+

## Accuracy
| Model                                                | Acc.   |
| ---------------------------------------------------- | ------ |
| [VGG16](https://arxiv.org/abs/1409.1556)             | 92.64% |
| [ResNet18](https://arxiv.org/abs/1512.03385)         | 93.02% |
| [ResNet50](https://arxiv.org/abs/1512.03385)         | 93.62% |
| [ResNet101](https://arxiv.org/abs/1512.03385)        | 93.75% |
| [MobileNetV2](https://arxiv.org/abs/1801.04381)      | 94.43% |
| [ResNeXt29(32x4d)](https://arxiv.org/abs/1611.05431) | 94.73% |
| [ResNeXt29(2x64d)](https://arxiv.org/abs/1611.05431) | 94.82% |
| [DenseNet121](https://arxiv.org/abs/1608.06993)      | 95.04% |
| [PreActResNet18](https://arxiv.org/abs/1603.05027)   | 95.11% |
| [DPN92](https://arxiv.org/abs/1707.01629)            | 95.16% |

## Accuracy detail

**Params** and **MACs** are evaluated using [thop](https://github.com/Lyken17/pytorch-OpCounter)

| Model           | Params     | MACs     | Acc.   |
| --------------- | ---------- | -------- | ------ |
| LeNet           | 62,007     | 0.71     | 75.44% |
| Vgg11           | 9,231,114  | 153.22   | 91.67% |
| Vgg13           | 9,416,010  | 229.02   | 93.55% |
| Vgg16           | 14,728,266 | 314.03   | 93.49% |
| Vgg19           | 20,040,522 | 399.05   | 93.45% |
| ResNet18        | 11,173,962 | 556.65   | 94.39% |
| ResNet34        | 21,282,122 | 1161.45  | 94.85% |
| ResNet50        | 23,520,842 | 1304.71  | 94.81% |
| PreActResNet18  | 11,171,146 | 556.52   | 93.92% |
| PreActResNet34  | 21,279,306 | 1161.32  | 93.39% |
| PreActResNet50  | 23,509,066 | 1303.66  | 94.41% |
| PreActResNet101 | 42,501,192 | 2519.16  | 93.38% |
| PreActResNet152 | 58,144,840 | 3735.44  | 94.85% |
| GoogLeNet       | 6,166,250  | 1529.43  | 94.27% |
| ResNeXt29_2x64d | 9,128,778  | 1416.64  | 95.19% |
| ResNeXt29_4x64d | 27,104,586 | 4242.25  | 93.70% |
| ResNeXt29_8x64d | 89,598,280 | 14121.32 | -      |
| ResNeXt29_32x4d | 4,774,218  | 779.63   | 92.58% |
| DenseNet121     | 6,956,298  | 898.06   | 95.10% |
| DenseNet161     | 26,482,378 | 2485.99  | 93.69% |
| DenseNet169     | 12,493,322 | 1071.71  | 94.12% |
| DenseNet201     | 18,104,330 | 1379.51  | 94.80% |
| MobileNetsV1    | 3,217,226  | 47.18    | 91.84% |
| MobileNetsV2    | 2,296,922  | 94.61    | 94.34% |
| ShuffleNetG2    | 887,582    | 41.09    | 91.71% |
| ShuffleNetG3    | 862,768    | 40.38    | 89.24% |
| ShuffleNetV2    | 1,263,854  | 46.13    | 91.84% |
| SENet18         | 11,260,354 | 556.74   | 93.65% |
| DPN26           | 11,574,842 | 670.31   | 94.01% |
| DPN92           | 34,236,634 | 2053.89  | 94.36% |
| EfficientNetB0  | 2,912,089  | 27.92    | 88.52% |

## Learning rate adjustment

I manually change the `lr` during training:
- `0.1` for epoch `[0,150)`
- `0.01` for epoch `[150,250)`
- `0.001` for epoch `[250,350)`

Resume the training with `python main.py --resume --lr=0.01`
