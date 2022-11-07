# Introduction

U-Net is a convolutional neural network that was first introduced in a paper titled “U-Net: Convolutional Networks for Biomedical Image Segmentation” by Olaf Ronneberger, Philipp Fischer, and Thomas Brox. To start from the basics, a convolutional neural network is a network architecture for deep learning that is often used for image classification. This is due to the fact that CNN’s are able to recognize different objects in images. There is however a major  difference between the applications of U-Nets and standard CNNs. A standard CNN is more so used for overall image classification whereas U-Net can go deeper and assign a class label to each pixel. This makes U-Nets useful in fields such as medicine, hence the original application, where an image needs to be segmented in different parts and examined from there. Another popular example of U-Net application is aerial imagery segmentation- taking a satellite image and highlighting the different parts whether it is a road, body of water, building, etc. As for performance, U-Net outperforms the prior best method: a sliding-window convolutional network. On its own, U-Net is quite fast as segmentation of a 512x512 image takes not even a second.

![Figure1](https://user-images.githubusercontent.com/98201516/200215586-9d6284b7-2021-4951-b464-c60d0fac35c3.jpg)

# U-Net Architecture

U-Net gets its name from its U-shaped architecture, as illustrated in Figure 2. The left side is known as the contracting side and the right side is the expansive path. In the contracting path,  there are repeated applications of two 3x3 convolutions followed by a rectified linear unit (ReLU) and 2x2 max pooling operation with stride 2 for downsampling. A convolution layer is the main building block of a CNN and contains a set of filters to an input that with repeated application results in a feature map which summarizes the detected features. A ReLU is used as the default activation function in CNNs and allows the model to learn faster and perform better. The max pooling operation calculates the maximum value in each patch of the feature map resulting in a downsampled feature map which highlights the most present features instead of averaging them. 
In the expansive path, instead of downsampling there is upsampling of the feature map followed by a 2x2 convolution in which the number of feature channels is halved and two 3x3 convolutions, each followed by a ReLU. The main idea is that we want to restore the condensed feature map to the original size of the input image. Specifically, upsampling is done to match the corresponding concatenation blocks from the left. As seen from the complicated architecture, semantic segmentation requires discrimination at pixel level as well as a method to project the discriminative features learnt at different stages of the contracting path onto the pixel space. 

![Figure2](https://user-images.githubusercontent.com/98201516/200215681-840c6c6c-a595-4f0e-9f4e-7368288e5a9c.jpg)

# Applying U-Net to a Dataset 

Before a U-Net model can be applied to a dataset, the data needs to be preprocessed. Images can come in many sizes, but in order to capture these images into numpy arrays, they need to be cropped into patches of 256x256. This can be done using patchify and Pillow, python libraries, as demonstrated in figure 3(a). Furthermore, the masks (ground truth of segmentation) are in RGB while information of each segment is provided as HEX color code, as demonstrated in figure 3(b). The HEX code must be converted to RGB values. The labels are then converted to integer values and lastly to one hot encoded. After the images are resized and labels are converted, one can then apply the U-NET model and train it using the dataset.

![figure 3](https://user-images.githubusercontent.com/98201516/200215790-ff6459ce-ea80-46bb-bef1-b911bba130c9.jpg)

# Conclusion 

All in all, u-net is a convolutional neural network that allows for fast and precise segmentation of images. In this project, U-Net is used in conjunction with a dataset full of 8 tiles of 9 images each. Each image has a corresponding mask aka the ground truth segmentation. Training occurred with 100 epochs and the results are as follows. 

# Results

## Plots of 10 Segmented Images

![1](https://user-images.githubusercontent.com/98201516/200215929-587ff112-849d-4f17-b034-61921fb6cdb6.jpg)
![2,3](https://user-images.githubusercontent.com/98201516/200215957-3b79b37d-5b93-4032-9556-dcecce520d7a.jpg)
![4,5](https://user-images.githubusercontent.com/98201516/200215965-897b05b1-8662-495c-a595-944d6c617207.jpg)
![6,7](https://user-images.githubusercontent.com/98201516/200215984-b7922539-c4a3-4097-940d-b3a104618cd3.jpg)
![8,9](https://user-images.githubusercontent.com/98201516/200216771-18e8b0f9-be24-4c32-aad4-6493230a5782.jpg)
![10](https://user-images.githubusercontent.com/98201516/200216013-d08e116d-271b-47b7-9cd7-d77c44315aee.jpg)

## Training and Validation Loss vs Epochs

![trainvalloss](https://user-images.githubusercontent.com/98201516/200216066-15939d84-911e-43b9-a122-09ac22089643.jpg)

## Precision-Recall Curve

![precision-recall](https://user-images.githubusercontent.com/98201516/200216083-82ef11b0-f0f7-4e72-9fa7-2f96baa319ae.jpg)
