# Things About Repositories

Index

* [How to download and open a repositorie](#How-to-download-and-open-a-repositorie)
* [How to use a deep learning library](#How-to-use-a-deep-learning-library)
* [How to understand and learn a deep learning library](#How-to-understand-and-learn-a-deep-learning-library)
* [How to modify a deep learning library](#How-to-modify-a-deep-learning-library)
* [Appendix](#Appendix)

## How to download and open a repositorie
- Download Zip (Not recommended, but available.)

    Download the compressed package on Github extract the file open with VSCode.

- git clone (recommended)

    Click `Code` and copy the Https URL. Open the git bash and do git clone open with VSCode.

## How to use a deep learning library

Readme is definitely important for repositories on Github, read the 'Readme' before doing everything.

### The environment configuration
The environment configuration section requires the repository provider to provide the environment to use. Some developers provide this requirements, others may simply mention it in the Readme.

   1. Contains requirements: all the python libraries you need in `requirements.txt`.
    
   2. Not contains requirements: see the `README`. If nothing there, use other library.

### Training
1. Training common data set

    Start with Readme, which usually has a guide to getting started. The key word is usually "train" and needs to be searched. Without a guide, library developers are often unreliable, and the advice is to abandon the library. All the training really needs is a command, and once run, if the environment is configured correctly, it should automatically download the data set and start training. However, since they are all automatically configured, they may not be suitable for you. Once you're familiar with the repository, you can try modifying it. If you are not familiar with it, the default value is recommended.

2. Train your own data set

    If you're training your own data set, you'll have to look at the Readme. There is usually a guide to getting started. Without a guide, library developers are often unreliable. First of all, my advice is to give up the library.

### predicting

The prediction part is mainly based on Readme, which generally provides a beginner's guide. Keywords are predict or Inference (there are also other words, such as detect, image, etc.), which should be searched. Without a guide, then again, the developer of the library is generally unreliable. For starters, my advice is to abandon the library.

## How to understand and learn a deep learning library
Generally speaking, the functions of deep learning library include two parts, one is to train the model, the other is to use the model for prediction.When training the model, it is necessary to consider the model itself, training parameters, data loading and loss functions.When predicting the model, it is necessary to consider the model itself, data loading and post-forecast processing.In summary, a functional deep learning library needs to contain the following five parts:
- Model itself
- training parameters
- data loading
- loss function
- predictive post-processing.

### Model
Generally speaking, the name of the model itself in the warehouse is net or model. The part of the network structure is stored in the Model folder. Basically, the composition and construction of the network will be completed in this part.

### Parameter of training
Training parameters are usually accompanied by training files. Therefore, in the 'train.py' file, each library specifies parameters in different ways. Some prefer to specify parameters through the 'yaml' file, some prefer to specify parameters through the 'cfg' file, and some even specify parameters through the 'py' file, which are all different. But most libraries can be found in the 'train.py' file.

### Data loading

#### Training data
Training the data loading is actually very important, which is directly related to the training of the model. The data loaded by the supervision model during training is generally divided into two parts. One part is the input variable, which is usually the picture. The other part is the label, which is the coordinate of the frame corresponding to the picture in object detection and the type of each pixel in semantic segmentation. In general, the data loading section, the model itself is named Data, datasets, or dataloader in the warehouse.

#### The prediction part
Compared with the training data loading, the predicted data loading is less about data enhancement and label processing, so it will be relatively simple. The main task is to preprocess the input image.Since it is the data preprocessing of the prediction part, we need to start from the prediction file.

### Function of loss
Generally speaking, the name of the Loss function in the warehouse is Loss. The Loss function is the target of model optimization. In theory, the more optimized the loss is, the smaller it will be in the training process. For the composition of Loss, each warehouse has different composition ways, so the analysis is very difficult. Especially in target detection, positive samples are selected in various ways, so it is difficult to directly have an overall cognition of Loss. In order to further understand the work of Loss, it is usually necessary to conduct a line by line analysis of loss.

### Predictive post processing
The post-processing of prediction mainly includes decoding of prediction results and visualization of prediction pictures. Since this is the post-processing part of the prediction, we need to start looking in the prediction file.

## How to modify a deep learning library
After learning a deep learning library, if you want to meet the different requirements of your project or paper, most of you need to modify the warehouse.  At this time, how to locate the modification position and analyze and modify the variables becomes very important.

### Modifying Target Location
First, the task of counting needs to be analyzed, and the analysis results are as follows:
1. Counting has nothing to do with the model itself.
2. We can't count before we predict.
3. Counting has nothing to do with training.
4. Counting occurs after the prediction.
So counting is something that belongs to predictive post-processing. We first locate the post-processing part of the prediction.

### Analysis of variables
Analyzing the predicted results, the output of 'self.net' is 'outputs'.'results' is the result of non-maximal suppression. The next step is to decompose the results after non-maximum suppression to obtain labels, confidence, and prediction frame coordinates.

### Modifying the Code
Since we are counting, we need to determine which class each prediction box belongs to. In python, matrices are used to determine the whole, so we loop through self.class_names and determine that top_label is equal to the number of each class.

## Appendix
Tutorial from :
- [Bubbliiiing](https://space.bilibili.com/472467171/channel/series)

- [Bubbliiiing](https://blog.csdn.net/weixin_44791964?type=blog)
