# Pizza Identifier

## Introduction

We first started off with trying to identify different EEG patterns to wave brain classes using Neural Nets, but the files themselves were difficult to parse, and as beginners it was not feasible. We got hungry during the first project meeting, and joked, *“Why not pizza?”* A pizza dataset was found on kaggle, along with previous projects to compare our models to.  Pizza identification is a popular project. However, ours evolved into integrating multiple machine learning methods, such as SVM. 


## Figures

**Kaggle Source of our images:**
https://www.kaggle.com/datasets/carlosrunner/pizza-not-pizza
 
![Kaggle Screenshot](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/kaggle-Image.png)

**SVM inspiration:**
https://www.kaggle.com/code/ashutoshvarma/image-classification-using-svm-92-accuracy/notebook)

![SVM inspo screenshot](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/SVM-inspo-image.png)

An idea of what our data was and how SVM identified the data. Each pixel has 3 values, and each image is n by m pixels. We can't visually show that, but the idea is we created a hyperplane that divided the data, and based on where the data fell on that division, and the importance of the convolutions, we could determine whether the image was a pizza. 

![SVM explanation Image](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/SVM-explanation.png)

Source: https://medium.com/@skilltohire/support-vector-machines-4d28a427ebd


## Methods

### [Pre-processing and Data Exploration](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/ebaa6f7d9f57446dfedbb5ced0320f533e0665f0/data-exploration.ipynb)

This data set contained many images of pizzas and food items that weren’t pizzas. We then had to preprocess our data, and we decided to resize all our images to 512x512 for uniformity.

In the beginning, we had trouble working with imaging data and we weren’t sure how to resize or use images for our classifier. We had to search online a lot, and we found the PIL library to be useful. We also were not able to load images into our jupyter notebooks initially, but after some searching we were able to utilize the OS library and we used that to access and create new modified images directories in our code.
### [Model 1 - Simple Convolution Neural Network](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/34bd8bdfdaa629d078f94a834c52ebc06f09d260/first-model.ipynb)

Our first model was a simplistic approach where we trained our preprocessed data on sequential CNN and over a few convolutional layers, to which we got an overfitting model.

### [Model 2 - SVM, CNN and Naïve Baye's Classifier](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/183848bc4727d33c6a578a81e94129c8dda9c209/second-model.ipynb)

Improving on the first model, we ran our training data through SVM(support Vector Machine) with Naive Bayes before feeding into our neural network to tackle the problem of overfitting.

### [Model 3 - Final - SVM and Convolution Neutral Network](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/183848bc4727d33c6a578a81e94129c8dda9c209/svm-cnn-final.ipynb)

For the final model, we decided to downsize the image size to 128x128 pixels to make the model more time efficient. Use used a SVM to get a partial guess that we could then feed into the neural network after the convolutional layers and flattening

![CNN SVM Diagram](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/CNN-SVM-diagram.jpg)

## Results

### [Model 1 - Simple Convolution Neural Network](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/34bd8bdfdaa629d078f94a834c52ebc06f09d260/first-model.ipynb)
![SVM inspo screenshot](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/Model-1.png)

Our basic CNN model got around **99%-100%** accuracy for the **training** set, but about **49%-51%** accuracy for the **testing** set. This means we overfitted the training set and the model works as well as a coin flip for the testing set

### [Model 2 - SVM, CNN and Naïve Baye's Classifier](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/183848bc4727d33c6a578a81e94129c8dda9c209/second-model.ipynb)

This model worked better than the first model with a **60%** accuracy with the **testing** set

### [Model 3 - Final - SVM and Convolution Neutral Network](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/183848bc4727d33c6a578a81e94129c8dda9c209/svm-cnn-final.ipynb)

This model worked better than the previous two with about **91%** accuracy on the **training** set and **65%-73%** accuracy on the **testing** set.

![Best accuracy results](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/best-SVM-CNN-model.png)

![Model Outputs](https://github.com/KaoushikMurugan/ecs-171-sort-pizza-images-project/blob/main/images/example-model-output.png)

## Discussion

We made a pizza identifier because we wanted to gain more experience using a neural network and other machine learning methods, like an SVM. We thought this would be a fun way to implement what we learned in class into a project. When we were discussing this project, we first had to decide what kind of data we wanted to work with. We were able to find a ‘pizza and not pizza’ dataset on Kaggle, which we used in our project.

For this reason, our second model was to include an SVM classification model and add it into the neural network as an attribute.  However, the SVM could not be imputed with the rest of the image, because of how keras input layers work, and convolution. If the SVM was added as a pixel, or was added as a separate dimension, then the convolution layer of the NN wouldn't work. Sidestepping the issue,  Categorical Naive Bayesian was used to aggregate the NN and SVM outputs. The rounded logistic regression output of the Neural net was imputed as attribute x1, and SVM was imputed as x2. The two model predictions are independent, since their classification methods are completely different. Therefore, the images could be classified using Naive Bayes. In essence, the second model said this,  “The prediction If Neural Net says this, and SVM says this, is it pizza?” Our model did work, but was so expensive to run, 20 images was the max to train, and 10 to test the model. This reduced confidence in the classification report.

Our third model input the SVM values later into the NN. It was much more computationally intensive, but worked. The SVM had to be fitted and predicted first, then after the convolution and flattening steps was concatenated to the image data as an attribute, before logistic regression. We have seen between 65% and 72% accuracy. Overall broader impact is that we made model predictions using multiple machine learning methods, in a non-sequential, or sequential manner. We went above and beyond the requirements of the project, but also learned how to take a theory, build a conceptual data processing pipeline, then develop different species of that pipeline. 

Computation Expenses Notes: We first resized to 512x512 across the images, to normalize the data using PIL library methods for our first model.  To improve runtime and memory, image element values changed from float 64 to uint 8 for the second. Computation was still expensive for our 1000 images, with  requirements going over our personal computer capabilities. We compensated by downsizing images further to 128x128x3. Color was a practical necessity to classify the images, so Grayscaling was nonviable.

Even our final model has some flaws, when we try adding more dense layers, we sometimes get better outputs, but when trying to re-run the model, we got a strange result: all of the predicted values from the model were the same. Searching online we found out that this can be caused when the model doesn't really learn anything, which could be caused due to having low number of layer and nodes in the model, or having too many nodes or even having too much training data or epoches. We've tried various methods, but were able to improve upon what we achieved, so we stuck to it.

## Conclusion

In the future, we plan on making our model more precise by adding more activation layers and seeing if using a Gaussian model would help with our accuracy. We plan on increasing the scope of the classifier and possibly having it classify different types of pizzas, like whether it is thin crust or a deep dish pizza. Since this kind of classification is more nuanced, it would be interesting to see what methods would be useful for this implementation and how we could further enhance our model to deal with those situations. Overall, we all were able to gain a deeper understanding of neural networks and convolution. 

## Collaboration

**Note**: *We are not following the format since it's difficult to distinguish between the ourselves since we all did a little bit of everything*

The first team meeting was to discuss and pick the data we wanted to analyze, and for what purpose. In the second meeting we identified the attributes needed for machine learning, and analyzed our dataset. Gerrik researched and shared resources about the file format in the dataset. Kaoushik and Gerrik were the main model coders, method researchers, and debuggers. 

For the preprocessing and first model deadlines, we brainstormed ideas over a group call where one person shared their coding environment, and everyone else helped the person coding through googling resources, or syntax or brainstorming ideas and suggesting codes implementations. 

For the final project deadline, we each tried to implement different things since we felt it was more effective than only one person running the code on their machine. We ended up choosing the svm + convolutional NNmethod since it had a significant improvement compared to other people's methods. The final write up was also a group effort, we assigned the different sections amongst ourselves and then compiled it at the end.
