
## 💡 Core Concept



In this repository there is a Jupyter Notebook that shows a built, trained, and fine-tuneed Convolutional neural network for image classification on the CIFAR-10 dataset using TensorFlow and Keras. The model architecture is designed using 3 convolutional blocks followed by a classification head and it has been fine-tuned to achieve around 88% accuracy.


## 🧮 Model Architecture

```

1. Block 1 (Input Feature Extraction):** 
- Input: 32×32×3 images. 
- Layers: 
	- Conv2D 
	- BatchNormalization - Conv2D
	- BatchNormalization 
	- MaxPooling2D

2. Block 2 (Intermediate Feature Extraction):** 
- Layers:
- Conv2D 
	- BatchNormalization 
	- Conv2D
	- BatchNormalization 
	- MaxPooling2D
	  
3. Block 3 (High-Level Feature Extraction):** 
- Layers: 
- Conv2D
	- BatchNormalization 
	- Conv2D
	- BatchNormalization 
	- MaxPooling2D

- Flatten: Converts the 4×4×128 feature maps into a 2048-dimensional vector 
- Dropout: Applied for regularization. 
- Dense Layer: 1024 neurons to learn class-specific features. 
- Dropout: Additional regularization. 
- Output Layer (Dense):10 neurons with softmax activation, one for each    CIFAR-10 class.


Model: "functional"
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┓
┃ Layer (type)                         ┃ Output Shape                ┃         Param # ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━┩
│ input_layer (InputLayer)             │ (None, 32, 32, 3)           │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ conv2d (Conv2D)                      │ (None, 32, 32, 32)          │             896 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ batch_normalization                  │ (None, 32, 32, 32)          │             128 │
│ (BatchNormalization)                 │                             │                 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ conv2d_1 (Conv2D)                    │ (None, 32, 32, 32)          │           9,248 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ batch_normalization_1                │ (None, 32, 32, 32)          │             128 │
│ (BatchNormalization)                 │                             │                 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ max_pooling2d (MaxPooling2D)         │ (None, 16, 16, 32)          │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ conv2d_2 (Conv2D)                    │ (None, 16, 16, 64)          │          18,496 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ batch_normalization_2                │ (None, 16, 16, 64)          │             256 │
│ (BatchNormalization)                 │                             │                 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ conv2d_3 (Conv2D)                    │ (None, 16, 16, 64)          │          36,928 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ batch_normalization_3                │ (None, 16, 16, 64)          │             256 │
│ (BatchNormalization)                 │                             │                 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ max_pooling2d_1 (MaxPooling2D)       │ (None, 8, 8, 64)            │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ conv2d_4 (Conv2D)                    │ (None, 8, 8, 128)           │          73,856 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ batch_normalization_4                │ (None, 8, 8, 128)           │             512 │
│ (BatchNormalization)                 │                             │                 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ conv2d_5 (Conv2D)                    │ (None, 8, 8, 128)           │         147,584 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ batch_normalization_5                │ (None, 8, 8, 128)           │             512 │
│ (BatchNormalization)                 │                             │                 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ max_pooling2d_2 (MaxPooling2D)       │ (None, 4, 4, 128)           │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ flatten (Flatten)                    │ (None, 2048)                │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ dropout (Dropout)                    │ (None, 2048)                │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ dense (Dense)                        │ (None, 1024)                │       2,098,176 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ dropout_1 (Dropout)                  │ (None, 1024)                │               0 │
├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤
│ dense_1 (Dense)                      │ (None, 10)                  │          10,250 │
└──────────────────────────────────────┴─────────────────────────────┴─────────────────┘
 Total params: 7,057,984 (26.92 MB)
 Trainable params: 2,330,378 (8.89 MB)
 Non-trainable params: 66,848 (261.12 KB)
 Optimizer params: 4,660,758 (17.78 MB)
```

## 🔍 Results 


With the current setup and fine-tuning, this model gets approximately 88% accuracy on the test set. Fine-tuning steps were applied to further optimize performance for challenging classes. THe classes for Cats and Dogs were were not as robust as for some of the other classes. For cats, Fine tuning the later layers led to an improvement in the cat predictions. While the cat performance improved, the dog predictions did not show a similar level of improvement—in fact, they sometimes dipped slightly. 


## ⚠️ Development and Debugging

Issues faced:
Confusion Between Cats and Dogs
 
The confusion matrix revealed that the model was misclassifying cats and dogs. While the cat predictions improved after some adjustments, dog predictions did not see similar gains.

Cats and dogs share many low-level features (such as texture and shape) which the early layers of the CNN capture. Without enough emphasis on the subtle differences, the model struggled to tell them apart.

Degbugging steps:

Generated and reviewed the confusion matrix to identify which classes were being misclassified. Froze the early convolutional layers and unfreezed the later convolutional block along with the dense classification layers. 

Fine-tuning led to a significant improvement in the cat predictions. Butt dog predictions remained slightly off.
