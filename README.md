# Sorting pizza images from food images
Sort images into pizza and not pizza images. Project for ECS 171


# Data Exploration
[Link to data-exploration python notebook](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/tree/main/data-exploration.ipynb)

We have two classes: Pizza and Not Pizza. We have 983 images each

We also notice that more than half of the images are of the size 512x512 and the rest of them are less than 512x512

### What we will do in preprocessing:

We will use the PIL library to resize the images to a standard size of 512x512.

Then we will use np.array and Image.open() to convert the images to 3 layers of 2d array of rgb values, and then store them into a pandas dataframe.
i.e. each image is converted to a 3d array of dimensions [512][512][3]

Team Members
-Kaoushik Murugan
-Usha Sah
-Mansi Agarwal
-Gerrik Labra
-Yuwei Wang

### Preprocessing & First Model:

For our preprocessing, we standardized the image sizes to 512x512. We also made a new directory with the resized images. 
To train our data, we split the data to 80,20. We then used convolution layers, acitivation functions, and made a sequential model. 
We evaluated the model by using a classification reprt and compared the error values from the training and testing data.
2 Layers of convolution. Using relu as our activation funciton, and sigmoid as our classification funciton.
We had overfitting in our model, with training data having an accuracy of 70%, but testing at 51%.
with batch sizes regulated to below 100 or else the code wouldnt run.
We plan to implement SVM prediction scores to our testing dataset, to see if that will increase accuracy. Basically, predict images using svm, then imput the images and svm scores into the neural net.
