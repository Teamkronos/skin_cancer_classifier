The purpose of this file is to create a separate preprocessed dataset to feed through the framework file, allowing for preprocessing while
saving time, as the process will not have to be performed for every image each time an image is retrieved. This should be done after the 
utilities, such that the dataset has already been augmented, and separated into three classes. While the process can be done prior to 
augmentation to reduce run time, this will allow for experimentation with variables, as doing before augmentation will then require usage
of augmentation each time after each preprocessing.

The actual processes involved in the preprocessing including a dull razor algorithm designed to remove hair to ease interpretation by the 
cnn model. While originally soft attention was planned,  it was not ultimately implemented in this file. Note that it is still implemented
in the base framework if one wishes to test it out, though this comes with the caveat of excessive runtimes; this is simply an alternative 
to performing the preprocessing via the framework, though should take significantly less time than attempting to train with preprocessing 
through the framework.

Of note most importantly are the parameters under #HYPER-PARAMETERS FOR DULL RAZOR. These control how the preprocessing is performed. Each 
variable has been detailed in regards to their purpose.

Regarding image paths, ensure that the image_path and image_path_test are set to the respective input training and test sets. Regarding the 
image output paths, if set to an existing folder, existing files within that directory will be deleted. If set to a folder that does not exist,
that directory will be created. Please set create_output_directory to true or false depending on whether the existing folder exists or not.

Note there may be issues in relation to PADUFES if the augmented images are outputted as jpg since the base is png; Commenting out line 22
#if file.endswith('.jpg') of the loadImages function should rectify this.

To run this is fairly simple; if dealing with the base classes of others, bcc, and mel:
- 1. Ensure image input paths and output paths are correctly specified in #DRIVE PATH
- 2. Use desired preprocessing variables in #HYPER-PARAMETERS FOR DULL RAZOR
- 3. Ensure that file type specified in loadImages matches the image type of the dataset and reduceddataset = FALSE
- 4. Restart kernel and run all

Note if one wishes to experiment on other class setups (i.e. all 7 classes), this would require some modification, essentially repeating the
code (not including function definitions on variable definitions) for each of the classes.