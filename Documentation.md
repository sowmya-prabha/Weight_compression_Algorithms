###### &#x20;                                          **Weight Compression Algorithms in Deep Learning**

**Introduction**



Deep learning models contain many weights. A weight is a number that tells the model how much importance to give to an input or connection. Large models need more memory and are slower. Weight compression reduces the model size while keeping almost the same accuracy.

How Weights are Learned

At the beginning, weights are random. During training, the model compares its prediction with the correct answer and updates the weights. After many updates, important connections usually get stronger and less useful ones become smaller in weights.



**1. Pruning**

Pruning means removing unnecessary weights. It is like cutting dry branches from a tree. Very small weights that do not help much are removed. This makes the model smaller and faster.

Instead of deleting lowest weights physically, many implementations simply set them to 0, meaning the connection has no effect.

threshold = 0.01 

for weight in weights: 

&#x20;    if abs(weight) < threshold: 

&#x20;    weight = 0



**2. Quantization**

Quantization means storing weights using fewer bits. For example, instead of 32-bit values, we can use 8-bit values. The model needs less memory and runs faster.

for each weight:

&#x20;   compressed\_weight = round(weight)

&#x20;   store(compressed\_weight)



**3. Weight Sharing**

Weight sharing means similar weights use the same value. Instead of storing many similar numbers, the model stores one value and reuses it. This saves memory.

0.51, 0.52 ,0.50, 0.53

All these almost have same value. So the model stores 0.52 for all. This saves memory.



**4. Low-Rank Factorization**

A large weight matrix is replaced with two smaller matrices that give almost the same result. This reduces storage and computation. In deep learning, one large weight matrix is divided into two smaller matrices. When these two smaller matrices are multiplied together, they produce almost the same result as the original matrix, but they require less memory.



**5. Knowledge Distillation**

A large teacher model teaches a smaller student model. The student learns the important knowledge and gives similar results with fewer parameters.



**6. Huffman Coding**

Huffman coding compresses the stored weights like a ZIP file. Frequently used values get shorter codes, so the model file becomes smaller without changing the information.



**Overview**



Weight compression helps reduce model size, memory usage and prediction time. The main techniques are pruning, quantization, weight sharing, low-rank factorization, knowledge distillation and Huffman coding. These methods are widely used to run deep learning models on mobile phones, IoT devices and edge computers.



**Limitations**



Pruning - Sometimes many small weights work together. Individually some weights seem small and useless but removing all of them reduces performances. 

Solution 1: Importance-based pruning. 

Solution 2: Sensitivity Analysis. 

Solution 3: Retraining



Quantization - Too few bits can reduce accuracy. Like in some cases if weight is 0.98 but it may take as 0 , hence information is lost.

Solution 1: Mixed Precision. 

Solution 2: Quantization-Aware Training.



Weight sharing - Different weights may be forced to become the same even when they should be different.

If  0.80 refers to ‘cat’ and 0.82 refers to ‘dog’ then weight sharing makes 0.81 where it loses differences.

Solution 1: Adaptive Clustering. 

Solution 2: Protect Important Weights. 



Low-Rank factorization - Not every matrix can be approximated well. Some matrices are highly complex and they cannot be represented well in small matrices. 

Solution 1: Compress Only Suitable Layers.

Solution 2: Adaptive Rank.



Knowledge Distillation - Requires training two models, which takes extra time and resources.

Solution 1: Self Distillation.

Solution 2: Reuse Existing Models.



Huffman Coding - Reduces storage only, not computation.

Solution 1: Combine with Pruning. 

Solution 2: Combine with Quantization.

Solution 3: Specialized Hardware.



