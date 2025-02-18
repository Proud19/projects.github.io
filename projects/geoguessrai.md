# Learning to Play GeoGuessr: Convolutional Neural Networks for Google Street View Geolocation 

## Project Overview

This project aims to develop an AI model capable of predicting the geographical location of a given image from Google Street View, akin to the popular game **GeoGuessr**. The project employs various machine learning models, including logistic regression, Convolutional Neural Networks (CNNs), and K-Nearest Neighbors (KNN), to predict the country of origin for a street-view image. Our goal is to build a model that can accurately predict geographical locations, identify country-specific features, and provide valuable insights into the nuances of machine learning applications for image-based geolocation tasks.

## References 
- [Project Report](https://github.com/user-attachments/files/18854451/CS229__Project_Final_Report_Template__Copy_.pdf)
- [Project Poster.pdf](https://github.com/user-attachments/files/18854465/229.Poster.pdf)



## Dataset

We utilized a dataset composed of Google Street View images from a variety of countries. These images contain various landmarks, architecture, and landscape features that can aid in identifying the country of origin. The dataset is imbalanced, with some countries having significantly more images than others, presenting a challenge for training a robust model. To tackle this, we used techniques like stratified sampling and weighted loss functions to improve the model's generalization across the different classes.

### Key Classes in the Dataset
- **Germany**
- **South Africa**
- **Singapore**
- **Japan**
- **Peru**

These countries were identified as some of the easiest for the model to predict due to distinct architectural and environmental features, which are also recognizable by human players.

## Model Architecture

### 1. **Multiclass Logistic Regression Model**
We started with a basic logistic regression model to provide a baseline for performance. This model was trained on pixel-level features from the images.

#### Results:
- **Accuracy:** 14.6%
- **Precision:** 3.43%
- **Recall:** 3.59%
- **F1 Score:** 2.84%

While this model performed better than random guessing (which yields a baseline accuracy of 1.8% for 55 classes), it was highly sensitive to overfitting due to the high parameter space and complexity of image data. This prompted the need for more advanced models with better generalization.

### 2. **Convolutional Neural Network (CNN)**
A CNN was employed to capture more complex patterns within the images, particularly useful for image classification tasks like ours. We started with a more complex architecture but encountered overfitting issues. After introducing dropout layers and reducing model complexity, we arrived at an architecture with a 64-unit dense layer and one dropout layer.

#### Results:
- **Accuracy:** 22.53%
- **Precision:** 30.73%
- **Recall:** 22.53%
- **F1 Score:** 23.23%

The CNN model significantly outperformed the logistic regression model. However, the F1 score was still somewhat low, indicating that the model had varying performance across different countries. The CNN also had better performance than a novice GeoGuessr player (Tobey), who tested the model informally. A heatmap of the confusion matrix revealed that some countries were much easier to identify than others, while others were rarely predicted correctly.

#### Key Observations:
- **Top Countries Predicted Correctly:** Germany, South Africa, Singapore
- **Common Misclassifications:** The model often confused countries with similar road signs, architectural styles, and climates.

### 3. **K-Nearest Neighbors (KNN) with CNN Features**
Next, we tried combining the CNN with KNN to leverage CNN-generated feature maps for improved geolocation predictions. Unfortunately, the performance of this model was disappointing.

#### Results:
- **Accuracy:** 4.46%
- **Precision:** 4.04%
- **Recall:** 4.46%
- **F1 Score:** 3.72%

The KNN model performed only marginally better than random guessing. A key reason for the poor performance was that the CNN feature map was not sufficiently "sharp" for distinguishing between nearby images, leading KNN to assign most points to the most common classes. Further refinement of the feature extraction process could improve this.


## Future Work

While the CNN model showed promising results, several areas for improvement remain:

1. **Feature Refinement:** The CNN feature maps were capable of capturing "obvious" patterns but struggled with more subtle country-specific features. Investigating alternative feature extraction methods or custom feature engineering (inspired by works like **PIGEON** or **DeepGeo**) could improve accuracy.

2. **KNN Improvement:** The KNN model underperformed, likely due to the lack of clear, distinct features in the CNN feature maps. Exploring more sophisticated feature extraction techniques or hybrid models combining CNN and manual features could lead to better results.

3. **OCR Integration:** We had considered integrating an OCR (Optical Character Recognition) component to detect text on road signs. While we didn’t have the resources to implement this, adding it could provide an additional layer of geolocation accuracy, especially in countries with identifiable text features.

4. **Object Recognition:** Future work could explore incorporating object recognition models (e.g., **PIGEON** or **PlaNet**) to detect objects that are unique to specific countries. This could significantly enhance the model's ability to differentiate between locations.

## Conclusion

This project explored multiple approaches to solving the image geolocation problem using Google Street View imagery. Our final model, a CNN-based classifier, significantly outperformed baseline models, and we were able to identify important patterns in the data that helped with location prediction. Despite its successes, the model still faces challenges with imbalanced data and feature extraction.

We are satisfied with the progress made and excited to explore further improvements, particularly in feature engineering and model refinement. The project demonstrated the potential of deep learning in real-world applications such as geolocation and provides a foundation for future exploration in the field.

## Contributions

- **Ethan:** Constructed the data pipeline, conducted literature review, and provided qualitative insights on country features based on personal GeoGuessr experience.
- **Proud:** Focused on the multiclass logistic regression model and evaluation metrics development.
- **Tobey:** Built, tuned, and ran the CNN and CNN-KNN models, including creating the data visualizations and plots.

## References

- Banerjee, Arsh. *Image Geolocation with Computer Vision.* 2023.
- Haas, Lukas, Michael Skreta, Silas Alberti, and Chelsea Finn. *Pigeon: Predicting image geolocations.* 2023.
- Kingma, Diederik P. and Jimmy Ba. *Adam: A Method for Stochastic Optimization.* 2015.
- Krylov, Vladimir A., Eamonn Kenny, and Rozenn Dahyot. *Automatic Discovery and Geotagging of Objects from Street View Imagery.* 2018.
- Simonyan, Karen and Andrew Zisserman. *Very Deep Convolutional Networks for Large-Scale Image Recognition.* 2015.
- Suresh, Sudharshan, Nathaniel Chodosh, and Montiel Abello. *DeepGeo: Photo localization with deep neural networks.* 2018.
- Weyand, Tobias, Ilya Kostrikov, and James Philbin. *PlaNet - Photo Geolocation with Convolutional Neural Networks.* 2016.
