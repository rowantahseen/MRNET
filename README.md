# MRNET
 Deep-learning-assisted diagnosis for knee magnetic resonance imaging 
https://stanfordmlgroup.github.io/projects/mrnet/
1- Augemented the image and repeated the Greyscale to 2 channels to make it 3D
2- Used Pretrained NASNet to extract the features of each 

1- input to the pretrained NASNet has dimensions s × 224 × 224 x 3, where s is the number of images in the MRI series.
2- each 2-dimensional MRI image slice is passed through a feature extractor to obtain a s × 1056 × 7 × 7 tensor containing features for each slice. 
3- A global average pooling layer is then applied to reduce these features to s × 1056. 
4- global max pooling across slices to obtain a 1056-dimensional vector

Note:
- we pass the images to the pretrained model as we load the data to make best use of RAM resources
- save the extracted features in .csv files in order to be able to use it later

5- Pass the Features to a Dense Layer to train the model
6- Repeat it for the 9 models ( 3 views: Axial, Sagittal, Coronal with each symptom of Abnormal, ACL, meniscal tears)
7- Get the average of each symptom with the 3 views 
