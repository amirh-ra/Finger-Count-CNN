# Finger-Count-CNN
## Pytorch Lightning based Convolutional Neural Network for Counting Fingers in Hand Gestures

Takeaways from this project:

   - SGD as the optimizer was totally unable to train the network as the loss stayed constant. However, switching to Adam optimizer fixed the problem.
   - Had to move Mydataset to a separate python file(fix.py) and then import it. Otherwise there would be a cuDNN error: CUDNN_STATUS_MAPPING_ERROR or a similar error concerning MPS.

| CNN final conv output | CNN structure  after secondReLU | MLP Number of layers | MLP Final activation | Accuracy |
| --------------------- | ------------------------------- | -------------------- | -------------------- | -------- |
| 1*1*64                | AvgPool2d(4,4)                  | 2                    | none                 | 88%      |
| 4*4*64                | none                            | 2                    | none                 | 93%      |
| 4*4*64                | none                            | 2                    | Sigmoid              | 95%      |
| 1*1*128               | MaxPool + Conv2d + Relu         | 2                    | Sigmoid              | 77%      |
| 4*4*16                | none                            | 2                    | Sigmoid              | 81%      |
| 4*4*32                | none                            | 2                    | Sigmoid              | 94%      |
| 4*4*32                | none                            | 1                    | Sigmoid              | 93%      |

