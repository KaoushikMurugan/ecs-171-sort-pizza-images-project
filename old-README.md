# Sorting pizza images from food images
Sort images into pizza and not pizza images. Project for ECS 171

Dataset acquired from [Kaggle](https://www.kaggle.com/datasets/carlosrunner/pizza-not-pizza)

# Data Exploration
[Link to data-exploration python notebook](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/tree/main/data-exploration.ipynb)

We have two classes: Pizza and Not Pizza. We have 983 images each

We also notice that more than half of the images are of the size 512x512 and the rest of them are less than 512x512

### What we will do in preprocessing

We will use the PIL library to resize the images to a standard size of 512x512.

Then we will use np.array and Image.open() to convert the images to 3 layers of 2d array of rgb values, and then store them into a pandas dataframe.
i.e. each image is converted to a 3d array of dimensions [512][512][3]


# Preprocessing & First Model

[Link to first model python notebook](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/tree/main/first-model.ipynb)

1. For our preprocessing, we resized all the image sizes to 512x512. We also made a new directory with the resized images. 
2. We split the data 80-20 to get our training and testing dataset.

3. Next, we constructed a sequential neural network model with 2D Convolution Layers. 
    - ANN info: 2 Layers of convolution. Using `tanh` and `relu` as our activation funciton, and `sigmoid` as our classification funciton.
4. Then, we evaluated the model using a classification reprt and compared the error values from the training and testing data.

### Conclusion: 
Our model **overfitted** the training data, since the training data had an accuracy of *almost 100%*, while the testing data was barely better than a coin toss with an accuray of *56%*.

On the fitting curve, our first model would lie as follows:

![Fitting Curve](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/fitting_curve.png)

## Ideas for the future

We plan to implement SVM (Support Vector Machine) prediction scores to our dataset, to see if that will increase accuracy. In other words, create a rough model with SVM to predict if an image is of a pizza or not, then use both the images and svm predictions into the neural net.

# Team Members
- Gerrik Labra
- Kaoushik Murugan
- Mansi Agarwal
- Usha Sah
- Yuwei Wang