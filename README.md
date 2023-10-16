# Culinary-Cognition

![walter_bacon](https://github.com/ombharat6361/Culinary-Cognition/assets/96538649/32022c90-df4f-4516-ad84-d69acd1c7681)


## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Model](#model)
- [Usage](#usage)
- [Results](#results)
- [License](#license)

## Introduction

Have you ever wondered "Hmm what is that food on that plate?". Well if you have, this repository has the answer to exactly that question!
Welcome to Culinary Cognition, a model that tells you what kind of food is present in an image!

This model is an implementation of the DeepFood research paper and BEATS the model it proposed.

## Dataset

The model is trained on [Food101](https://www.kaggle.com/datasets/dansbecker/food-101), a comprehensive dataset of food images collected from various sources, including food blogs, social media, and recipe websites. This dataset consists of 101 food categories, with 101,000 images. For each class, 250 manually reviewed test images are provided as well as 750 training images. All images were rescaled to have a maximum side length of 512 pixels. I used [Tensorflow datasets](https://www.tensorflow.org/datasets/catalog/food101) version of this data, which already had all images as tensors, making it easier to work with.

## Model

The core of this project is Transfer Learning with the EfficientNet architecture, a family of neural network models that provide an excellent trade-off between model size and performance. The pre-trained EfficientNetV2B0 model is fine-tuned on the food detection dataset to adapt to this task. The model was trained for 10 epochs, which provided the best results.

## Usage

To use the trained food detection model, follow these steps:

1. Clone this repository:
   ```bash
   git clone https://github.com/ombharat6361/Culinary-Cognition.git
   cd Culinary-Cognition
   ```

2. To directly use the model in python:
   ```python
   import tensorflow as tf
   model = tf.keras.models.load_model("ENTER PATH TO ENTIRE MODELS DIR")
   model.summary()
   result = model_saved.predict("YOUR IMAGE TENSOR")
   result
   ```
   For more information on using saved models, visit the [Tensorflow documentation on saving and loading models](https://www.tensorflow.org/tutorials/keras/save_and_load).

## Results
This shows the final result I got on the test set after calling `.evaluate()` on the trained model.
![result](https://github.com/ombharat6361/Culinary-Cognition/assets/96538649/d79bbab1-e6e8-46bb-9571-cf32a40a9193)

## License
Complies with the [MIT License](LICENSE)
