# ResNet-50_on_CIFAR10
<br>
Deeper neural networks are more difficult to train. Residual learning was introduced to ease the training of networks that are substantially deeper than those used previously. ResNet explicitly reformulates the layers as learning residual functions with reference to the layer inputs, instead of learning unreferenced functions. On the ImageNet dataset this method was evaluated with residual nets with a depth of up to 152 layers---8x deeper than VGG nets but still having lower complexity. An ensemble of these residual nets achieves 3.57% error on the ImageNet test set. This result won the 1st place on the ILSVRC 2015 classification task. This technique can also be applied to the CIFAR-10 with 100 and 1000 layers. 

ResNet was introduced in the following paper:

* K. He, X. Zhang, S. Ren, and J. Sun. [Deep residual learning for image recognition](https://arxiv.org/abs/1512.03385). arXiv preprint arXiv:1512.03385,2015.

What is a residual?

* [Residual](https://www.merriam-webster.com/dictionary/residual): an internal aftereffect of experience or activity that influences later behavior

To implement a ResNet we need to give Keras the notion of a residual block.  This is essentially two dense layers with a "skip connection" (or residual connection).  A residual block is shown in Figure 6.SKIP.


**Figure 6.SKIP: Skip Layers**
![Skip Layers](https://raw.githubusercontent.com/jeffheaton/t81_558_deep_learning/master/images/skip-layer.png "Skip Layers")

Residual blocks are typically used with convolutional neural networks (CNNs).  This allows very deep neural networks of CNNs to be created.  Figure 6.RES shows several different ResNets.

**Figure 6: ResNets**
![ResNets](https://raw.githubusercontent.com/jeffheaton/t81_558_deep_learning/master/images/resnet.png "ResNets")

### **Implementation on ImageNet**
 
- Our implementation for ImageNet follows the practice in [21, 41]. The image is resized with its shorter side ran-domly sampled in [256,480] for scale augmentation [41].A 224×224 crop is randomly sampled from an image or its horizontal flip, with the per-pixel mean subtracted [21].The standard color augmentation in [21] is used. We adopt batchnormalization (BN) [16] right  after each convolution and before activation, following [16]. We initialize the weights as in [13] and train all plain/residual nets from scratch. We use SGD with a mini-batch size of 256. The learning rate starts from 0.1 and is divided by 10 when the error plateaus,and the models are trained for up to 60×104 iterations. Weuse a weight decay of 0.0001 and a momentum of 0.9.  We do not use dropout [14], following the practice in [16].In testing, for comparison studies we adopt the standard 10-crop testing [21]. For best results, we adopt the fully-convolutional form as in [41, 13], and average the scoresat multiple scales (images are resized such that the shorterside is in{ 224,256,384,480,640 })

### CIFAR Dataset

The [CIFAR-10 and CIFAR-100](https://www.cs.toronto.edu/~kriz/cifar.html) datasets are also frequently used by the neural network research community.  These datasets were originally part of a competition. 

The CIFAR-10 data set contains low-res images that are divided into 10 classes.  The CIFAR-100 data set contains 100 classes in a hierarchy. 


### Resource's
[Deep Understand of ResNet](https://cv-tricks.com/keras/understand-implement-resnets/#:~:text=The%20major%20differences%20between%20ResNet,the%20form%20of%20identity%20connection)<br>
[Video by Jeff Heaton](https://youtu.be/qMFKsMeE6fM)<br>
[Code](https://github.com/keras-team/keras-applications/blob/master/keras_applications/resnet50.py)<br>
[Visualization of ResNet](http://ethereon.github.io/netscope/#/gist/db945b393d40bfa26006)<br>
[Object Detection](https://www.kaggle.com/shivamb/objects-bounding-boxes-using-resnet50-imageai)
