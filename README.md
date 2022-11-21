# Sorting pizza images from food images
Sort images into pizza and not pizza images. Project for ECS 171


# Data Exploration
[Link to data-exploration python notebook](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/tree/main/data-exploration.ipynb)

We have two classes: Pizza and Not Pizza. We have 983 images each

We also notice that more than half of the images are of the size 512x512 and the rest of them are less than 512x512

### What we will do in preprocessing:

We will use the PIL library to resize the images to a standard size of 512x512.

Then we will use np.array and Image.open() to convert the images to a 2d array of rgb values, and then store them into a pandas dataframe.
i.e. each image is converted to a 3d array of dimensions [512][512][3]

Team Members
-Kaoushik Murugan
-Usha Sah
-Mansi Agarwal
-Gerrik Labra
-Yuwei Wang
