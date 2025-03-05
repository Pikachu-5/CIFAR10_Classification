
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


- Total Parameters: 7,057,984 
- Trainable Parameters: 2,330,378 
- Non-Trainable Parameters: 66,848
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
