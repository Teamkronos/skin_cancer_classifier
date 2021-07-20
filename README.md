# Topic: Skin Cancer Classifier: Skin Cancer Pattern Extraction and Prediction Using Deep Convolutional Neural Networks

* The dataset chosen for this comparative analysis is titled Human Against Machine with 10,000 training images (HAM10000)
* It contains 10,015 (450 x 600 x 3) coloured high-resolution images of skin lesions labelled into three classes.
* Trained five CNNs: ResNet, InceptionV3, Xception, VGG-16 and DenseNet with hyper-parameters via the HAM10000 dataset and detailed the performance of these models. 
* Also tested the final model ResNet50 with custom weights on two external datasets being ISIC-2019 and PAD-UFES-20. 
* The benefits of this study include a novel approach to melanoma detection using CNNs, as well as an important aid for melanoma diagnosis in clinical settings.
* Achieved validation accuracy of 89% and recall rate of 82%

Guide to use Framework to train HAM10000 dataset from scratch.
Refer notebook “Skin Cancer Pattern Extraction and Prediction Using Deep Convolutional Neural Networks”
STEP 1
Place the data at below folder in AWS
'/home/ubuntu/data/HAM10000_all_images'

STEP 2
Run the ‘Utilities’ code ONCE and images gets classified to folders based on their respective classes. By default, there are 7 classes but using the mapping variable 
they were mapped to 3 classes ‘MEL’, ‘BCC’ and ‘Others’. In future if the couple or more classes must be clubbed together, alter the mapping accordingly
Images per class folder will be created at below path
/home/ubuntu/data/3classes/HAM10000_by_class/

STEP 3
Training & Test data path are set. By default, pointing to 
all_data_dir = '/home/ubuntu/data/3classes/HAM10000_by_class/'
training_data_dir = '/home/ubuntu/data/3classes/HAM10000_train_by_class/'
testing_data_dir = '/home/ubuntu/data/3classes/HAM10000_test_by_class/'
The above variables are passed to function ‘split_dataset_into_test_and_train_sets’ that creates training and test folders for the images in their respective classes.
 
STEP 4
Run code with ‘Data_augmentation’ Class for up sampling. Make sure the training data path is changed if it was changed earlier. Default path is as below:
/home/ubuntu/data/3classes/HAM10000_train_by_class/
Default augmentation size is 8500. This can be changed if a different dataset is preferred.
(optional): Process data via Preprocessing_Prior.ipynb: This will create a dataset which has been processed via dull razor and blurred. Ensure the source paths 
are as above, and choose appropriate output paths, ideally reflecting the parameters used for that dataset; these will be use in lieu of both /HAM10000_train_by_class/ 
and /HAM10000_test_by_class/ in the steps below if one wishes to use this.

STEP 5
Configure YAML with different hyper parameter only if different architectures need to be tried. Leave the default RESNET 50

STEP 6
Run below classes in the order they present in the Jupyter notebook
Classes Ham10000Attention, ModelTrainer() , and Data_augmentation don’t have to modified. If preprocessing has to be turned on then uncomment the below paramters 
in function get_generators() in Class ModelTrainer() as below
 
STEP 7
Run Base & Resnet50 functions
Run the model by loading the configuration from yaml
Class weights can be assigned at this time

STEP 8
Train the model with 33 or higher Epochs
Plot confusion Matrix to observe the Validation Accuracy

STEP 9 
Pass an image to the model to get its class accuracy
Set the path of the image to be tested in variable ‘image’
Pass this ‘image’ to model_trainer.predict() function and Print the probabilities

OPTIONAL
STEP 10 
To use the weights of Pretrained model run on HAM10000 on ISIC2019, use other notebook ISIC2019_Dataset_run, ensuring relevant model
is loaded.

OPTIONAL 
STEP 11
To use the weights of Pretrained model run on HAM10000 on PADUFES, use other notebook PADUFES-20_Dataset_run, ensuring relevant model
is loaded.

![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/1_Overview.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/0_data_analysis.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/2_resources.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/3_softattention.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/4_raw_preprocessed.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/5_YAML.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/6_parameter1.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/7_parameter2.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/7_parameter3.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/9_accuracy.PNG)
![](https://github.com/Teamkronos/Eugene_Portfolio/blob/main/images/10_recall.PNG)
