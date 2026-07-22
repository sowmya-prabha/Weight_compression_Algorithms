# Deep Neural Network (DNN) for MNIST Handwritten Digit Classification with Optimizer Comparison and Manual Weight Pruning

## Project Overview

This project implements a Deep Neural Network (DNN) to classify handwritten digits from the MNIST dataset. The model is trained using multiple optimization algorithms, and manual weight pruning is applied to study the effect of weight compression on classification accuracy.

The project compares the performance of different optimizers before and after pruning and analyzes how pruning affects the network.

---
## Objectives

- Load and analyze the MNIST dataset.
- Preprocess image data.
- Design a Deep Neural Network (DNN).
- Train the DNN using different optimizers.
- Evaluate model performance.
- Apply manual weight pruning.
- Compare accuracy before and after pruning.
- Analyze the impact of weight compression.

---

## Dataset

Dataset:
- MNIST Handwritten Digit Dataset

Dataset Information:

- Training Images : 60,000
- Testing Images : 10,000
- Image Size : 28 × 28 pixels
- Number of Classes : 10
- Image Type : Grayscale

Classes:

- Digit 0
- Digit 1
- Digit 2
- Digit 3
- Digit 4
- Digit 5
- Digit 6
- Digit 7
- Digit 8
- Digit 9

---

## Data Preprocessing

The following preprocessing steps are performed:

### 1. Load Dataset

Load MNIST dataset using TensorFlow.

### 2. Flatten Images

Convert each 28 × 28 image into a one-dimensional vector.

Before:

```
28 × 28
```

After:

```
784 Features
```

### 3. Normalize Pixel Values

Convert pixel values from

```
0 – 255
```

to

```
0 – 1
```

using

```
Pixel / 255
```

This improves model convergence.

---

## DNN Architecture

```
Input Layer (784 Features)

↓

Dense Layer
256 Neurons
ReLU

↓

Dense Layer
128 Neurons
ReLU

↓

Dense Layer
64 Neurons
ReLU

↓

Output Layer
10 Neurons
Softmax
```

---

## Activation Functions

### ReLU (Rectified Linear Unit)

Used in hidden layers.

Purpose:

- Introduces non-linearity.
- Removes negative values.
- Speeds up training.

Formula:

```
f(x)=max(0,x)
```

---

### Softmax

Used in the output layer.

Purpose:

- Converts outputs into probabilities.
- Predicts one of the ten digit classes.

Example:

```
Digit 0 : 0.01
Digit 1 : 0.02
Digit 2 : 0.90
Digit 3 : 0.01
...
```

Highest probability becomes the predicted digit.

---

## Optimizers Used

The project compares six optimization algorithms.

- Adam
- SGD
- RMSprop
- Adagrad
- Adamax
- Nadam

Each optimizer trains the same DNN independently.

---

## Training Parameters

- Epochs : 5
- Batch Size : 128
- Loss Function :
  Sparse Categorical Crossentropy
- Metric :
  Accuracy

---

## Manual Weight Pruning

Manual pruning is performed without using TensorFlow Model Optimization.

### Pruning Procedure

1. Extract weights from every Dense layer.
2. Calculate the pruning threshold using percentile.
3. Identify weights with small absolute values.
4. Replace those weights with zero.
5. Update the network.
6. Evaluate the model again.

Example

Before:

```
0.84
-0.002
0.67
0.0004
-0.92
```

After 30% pruning:

```
0.84
0
0.67
0
-0.92
```

The smallest weights are removed because they contribute less to the model prediction.

---

## Evaluation Metrics

The following metrics are recorded.

### Before Pruning

- Test Accuracy
- Test Loss

### After Pruning

- Test Accuracy
- Test Loss
- Number of Zero Weights
- Percentage of Pruned Weights

---

## Project Workflow

```
Load MNIST Dataset
        │
        ▼
Analyze Dataset
        │
        ▼
Flatten Images
        │
        ▼
Normalize Data
        │
        ▼
Build DNN
        │
        ▼
Compile Model
        │
        ▼
Train DNN
        │
        ▼
Evaluate Model
(Before Pruning)
        │
        ▼
Apply Manual Weight Pruning
        │
        ▼
Evaluate Model
(After Pruning)
        │
        ▼
Compare Optimizers
        │
        ▼
Display Final Results
```

---

## Technologies Used

- Python
- TensorFlow
- Keras
- NumPy
- Pandas
- Matplotlib
- Google Colab

---

## Expected Output

The project generates

- Dataset information
- Model summary
- Accuracy before pruning
- Accuracy after pruning
- Loss before pruning
- Loss after pruning
- Layer-wise pruning statistics
- Optimizer comparison table

## Accuracy

| Optimizer | Accuracy Before | Accuracy After |
|-----------|----------------:|---------------:|
| Adam | 97.62% | 97.53% |
| SGD | 92.74% | 92.27% |
| RMSprop | 97.51% | 97.51% |
| Adagrad | 88.82% | 87.58% |
| Adamax | 97.3% | 97.24% |
| Nadam | 97.43% | 97.22% |

---

## Advantages

- Simple and easy to understand.
- Demonstrates Deep Neural Network implementation.
- Compares multiple optimization algorithms.
- Demonstrates weight compression using manual pruning.
- Suitable for beginners in Deep Learning.

---

## Limitations

- Manual pruning only removes small weights.
- Does not physically reduce the model size.
- No quantization or structured pruning is implemented.
- Accuracy may decrease if a high pruning percentage is used.

---

## Future Enhancements

- Structured Weight Pruning
- Quantization
- Weight Sharing
- Low-Rank Factorization
- Knowledge Distillation
  
---

## Conclusion

This project demonstrates the implementation of a Deep Neural Network (DNN) for handwritten digit classification using the MNIST dataset. Multiple optimization algorithms are compared to analyze their effect on training performance. Manual weight pruning is then applied to compress the network by removing less significant weights. The results show how pruning influences model accuracy and provides insight into the trade-off between model compression and predictive performance.
